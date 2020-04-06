---
title: 'Nueva generación de proyectos: Bajo la capucha, primera parte Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aca35e85e57a07a2b411a23d81b99cff9983b9c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707053"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Nueva generación de proyectos: aspectos técnicos, primera parte
¿Alguna vez has pensado en cómo crear tu propio tipo de proyecto? ¿Te preguntas qué sucede realmente cuando creas un nuevo proyecto? Echemos un vistazo debajo del capó y veamos qué está pasando realmente.

 Hay varias tareas que Visual Studio coordina automáticamente:

- Muestra un árbol de todos los tipos de proyecto disponibles.

- Muestra una lista de plantillas de aplicación para cada tipo de proyecto y le permite elegir una.

- Recopila información del proyecto para la aplicación, como el nombre del proyecto y la ruta de acceso.

- Pasa esta información a la fábrica del proyecto.

- Genera elementos y carpetas de proyecto en la solución actual.

## <a name="the-new-project-dialog-box"></a>El cuadro de diálogo Nuevo proyecto
 Todo comienza cuando se selecciona un tipo de proyecto para un nuevo proyecto. Comencemos haciendo clic en **Nuevo proyecto** en el menú **Archivo.** Aparece el cuadro de diálogo **Nuevo proyecto,** con un aspecto similar al siguiente:

 ![Cuadro de diálogo Nuevo proyecto](../../extensibility/internals/media/newproject.gif "NuevoProyecto")

 Veámoslo con más detalle. El árbol **Tipos** de proyecto enumera los distintos tipos de proyecto que puede crear. Cuando seleccione un tipo de proyecto como **Visual C- Windows**, verá una lista de plantillas de aplicación para empezar. **Visual Studio** instala las plantillas instaladas en Visual Studio y están disponibles para cualquier usuario del equipo. Las nuevas plantillas que cree o recopile se pueden agregar a **Mis plantillas** y solo están disponibles para usted.

 Al seleccionar una plantilla como Aplicación de **Windows**, aparece una descripción del tipo de aplicación en el cuadro de diálogo; en este caso, **un proyecto para crear una aplicación con una interfaz**de usuario de Windows.

 En la parte inferior del cuadro de diálogo **Nuevo proyecto,** verá varios controles que recopilan más información. Los controles que ve dependen del tipo de proyecto, pero generalmente incluyen un cuadro de texto **Nombre** del proyecto, un cuadro de texto **Ubicación** y el botón **Examinar** relacionado y un cuadro de texto Nombre de **solución** y una casilla de verificación **Crear directorio para solución** relacionada.

## <a name="populating-the-new-project-dialog-box"></a>Rellenar el cuadro de diálogo Nuevo proyecto
 ¿De dónde obtiene el cuadro de diálogo **Nuevo proyecto** su información? Hay dos mecanismos en el trabajo aquí, uno de ellos en desuso. El cuadro de diálogo **Nuevo proyecto** combina y muestra la información obtenida de ambos mecanismos.

 El método anterior (obsoleto) utiliza entradas del registro del sistema y archivos .vsdir. Este mecanismo se ejecuta cuando se abrió Visual Studio. El método más reciente utiliza archivos .vstemplate. Este mecanismo se ejecuta cuando Visual Studio se inicializa, por ejemplo, ejecutando

```
devenv /setup
```

 or

```
devenv /installvstemplates
```

### <a name="project-types"></a>Tipos de proyecto
 La posición y los nombres de los nodos raíz de los tipos de **proyecto,** como **Visual C-** y **otros lenguajes**, se determina mediante entradas del registro del sistema. La organización de los nodos secundarios, como Base de **datos** y **Dispositivo inteligente,** refleja la jerarquía de las carpetas que contienen los archivos .vstemplate correspondientes. Echemos un vistazo a los nodos raíz primero.

#### <a name="project-type-root-nodes"></a>Nodos raíz de tipo de proyecto
 Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se inicializa, recorre las subclaves de la clave del Registro del sistema HKEY_LOCAL_MACHINE, SOFTWARE, Microsoft, VisualStudio, 14,0, NewProjectTemplates, TemplateDirs para compilar y asignar un nombre a los nodos raíz del árbol de tipos de **proyecto.** Esta información se almacena en caché para su uso posterior. Observe la clave\\TemplateDirs .FAE04EC1-301F-11D3-BF4B-00C04F79EFBC.\\ Cada entrada es un GUID de VSPackage. El nombre de la subclave (/1) se omite, pero su presencia indica que se trata de un nodo raíz de tipos de **proyecto.** Un nodo raíz puede, a su vez, tener varias subclaves que controlan su apariencia en el árbol Tipos de **proyecto.** Echemos un vistazo a algunos de ellos.

##### <a name="default"></a>(Es el valor predeterminado).
 Este es el identificador de recurso de la cadena localizada que nombra el nodo raíz. El recurso de cadena se encuentra en el archivo DLL satélite seleccionado por el GUID de VSPackage.

 En el ejemplo, el GUID de VSPackage es

 •FAE04EC1-301F-11D3-BF4B-00C04F79EFBC

 y el ID de recurso (valor predeterminado) del nodo raíz (/1) es #2345

 Si busca el GUID en la clave Packages cercana y examina la subclave SatelliteDll, puede encontrar la ruta de acceso del ensamblado que contiene el recurso de cadena:

 \<Ruta de instalación de>, VC, VCSPackages, 1033, csprojui.dll

 Para comprobarlo, abra el Explorador de archivos y arrastre csprojui.dll al directorio de Visual Studio. La tabla de cadenas muestra que el #2345 de recursos tiene el título **visual.**

##### <a name="sortpriority"></a>SortPriority
 Esto determina la posición del nodo raíz en el árbol Tipos de **proyecto.**

 SortPriority REG_DWORD 0x00000014 (20)

 Cuanto menor sea el número de la prioridad, mayor será la posición en el árbol.

##### <a name="developeractivity"></a>DeveloperActivity
 Si esta subclave está presente, la posición del nodo raíz se controla mediante el cuadro de diálogo Configuración del desarrollador. Por ejemplo,

 DeveloperActivity REG_SZ VC #

 indica que Visual C. será un nodo raíz si [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Visual Studio está configurado para el desarrollo. De lo contrario, será un nodo secundario de **Otros idiomas**.

##### <a name="folder"></a>Carpeta
 Si esta subclave está presente, el nodo raíz se convierte en un nodo secundario de la carpeta especificada. Aparece una lista de posibles carpetas bajo la clave

 HKEY_LOCAL_MACHINE,SOFTWARE, Microsoft, VisualStudio, 11,0, NewProjectTemplates, PseudoFolders

 Por ejemplo, la entrada Proyectos de base de datos tiene una clave Carpeta que coincide con la entrada Otros tipos de proyecto en PseudoFolders. Por lo tanto, en el árbol **Tipos** de proyecto, Proyectos de **base** de datos será un nodo secundario de Otros tipos de **proyecto**.

#### <a name="project-type-child-nodes-and-vstdir-files"></a>Nodos secundarios de tipo de proyecto y archivos .vstdir
 La posición de los nodos secundarios en el árbol Tipos de **proyecto** sigue la jerarquía de las carpetas de las carpetas ProjectTemplates. Para las plantillas de máquina **(plantillas instaladas**de Visual Studio), la ubicación típica es "Archivos de programa" (Archivos de programa), Microsoft Visual Studio 14.0 (Common7)\\y "Plantillas de usuario"**(Mis plantillas),** la ubicación típica es "Mis documentos", "Visual Studio 14.0", "Templates" y "ProjectTemplates". Las jerarquías de carpetas de estas dos ubicaciones se combinan para crear el árbol Tipos de **proyecto.**

 Para la configuración de desarrollador de Visual Studio con C, el árbol **de tipos** de proyecto tiene un aspecto similar al siguiente:

 ![Tipos de proyecto](../../extensibility/internals/media/projecttypes.png "ProjectTypes")

 La carpeta ProjectTemplates correspondiente tiene este aspecto:

 ![Plantillas de proyecto](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")

 Cuando se abre el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cuadro de diálogo **Nuevo proyecto,** recorre la carpeta ProjectTemplates y vuelve a crear su estructura en el árbol Tipos de **proyecto** con algunos cambios:

- El nodo raíz del árbol Tipos de **proyecto** viene determinado por la plantilla de aplicación.

- El nombre del nodo se puede localizar y puede contener caracteres especiales.

- El criterio de ordenación se puede cambiar.

##### <a name="finding-the-root-node-for-a-project-type"></a>Encontrar el nodo raíz para un tipo de proyecto
 Cuando Visual Studio recorre las carpetas ProjectTemplates, abre todos los archivos .zip y extrae los archivos .vstemplate. Un archivo .vstemplate utiliza XML para describir una plantilla de aplicación. Para obtener más información, consulte Nueva generación de [proyectos: Bajo la capucha, segunda parte.](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 La \<etiqueta de> ProjectType determina el tipo de proyecto de la aplicación. Por ejemplo, el archivo .CSharp-SmartDevice-WindowsCE-1033-WindowsCE-EmptyProject.zip contiene un archivo EmptyProject.vstemplate que tiene esta etiqueta:

```
<ProjectType>CSharp</ProjectType>
```

 El \<ProjectType> etiqueta y no la subcarpeta de la carpeta ProjectTemplates, determina el nodo raíz de una aplicación en el árbol Tipos de **proyecto.** En el ejemplo, las aplicaciones de Windows CE aparecen bajo el nodo raíz de **Visual C,** e incluso si se va a mover la carpeta WindowsCE a la carpeta VisualBasic, las aplicaciones de Windows CE seguirían apareciendo en el nodo raíz de **Visual C.**

##### <a name="localizing-the-node-name"></a>Localización del nombre del nodo
 Cuando Visual Studio recorre las carpetas ProjectTemplates, examina los archivos .vstdir que encuentra. Un archivo .vstdir es un archivo XML que controla el aspecto del tipo de proyecto en el cuadro de diálogo **Nuevo proyecto.** En el archivo .vstdir, use la \<etiqueta de> LocalizedName para asignar un nombre al nodo Tipos de **proyecto.**

 Por ejemplo, el archivo .CSharp-Database-TemplateIndex.vstdir contiene esta etiqueta:

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 Esto determina el archivo DLL satélite y el identificador de recurso de la cadena localizada que nombra el nodo raíz, en este caso, Base de **datos**. El nombre localizado puede contener caracteres especiales que no están disponibles para los nombres de carpeta, como **.NET**.

 Si \<no hay ninguna etiqueta de> LocalizedName, el tipo de proyecto se denomina mediante la propia carpeta, **SmartPhone2003**.

##### <a name="finding-the-sort-order-for-a-project-type"></a>Búsqueda del criterio de ordenación para un tipo de proyecto
 Para determinar el criterio de ordenación del tipo \<de proyecto, los archivos .vstdir usan la etiqueta de> SortOrder.

 Por ejemplo, el archivo .CSharp-Windows-Windows.vstdir contiene esta etiqueta:

```
<SortOrder>5</SortOrder>
```

 El archivo .CSharp-Database-TemplateIndex.vstdir tiene una etiqueta con un valor mayor:

```
<SortOrder>5000</SortOrder>
```

 Cuanto menor sea \<el número de la etiqueta SortOrder>, mayor será la posición en el árbol, por lo que el nodo **Windows** aparece más alto que el nodo Base de **datos** en el árbol Tipos de **proyecto.**

 Si \<no se especifica ninguna etiqueta de> SortOrder para un tipo \<de proyecto, aparece en orden alfabético siguiendo los tipos de proyecto que contienen Especificaciones de> SortOrder.

 Tenga en cuenta que no hay archivos .vstdir en las carpetas Mis documentos (**Mis plantillas**). Los nombres de tipo de proyecto de aplicación de usuario no están localizados y aparecen en orden alfabético.

#### <a name="a-quick-review"></a>Una revisión rápida
 Vamos a modificar el cuadro de diálogo **Nuevo proyecto** y crear una nueva plantilla de proyecto de usuario.

1. Agregue una subcarpeta MyProjectNode a la carpeta de archivos de programa de Microsoft Visual Studio 14.0, Common7, IDE, ProjectTemplates y CSharp.

2. Cree un archivo MyProject.vstdir en la carpeta MyProjectNode con cualquier editor de texto.

3. Agregue estas líneas al archivo .vstdir:

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. Guarde y cierre el archivo .vstdir.

5. Cree un archivo MyProject.vstemplate en la carpeta MyProjectNode con cualquier editor de texto.

6. Agregue estas líneas al archivo .vstemplate:

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. Guarde el archivo .vstemplate y cierre el editor.

8. Envíe el archivo .vstemplate a una nueva carpeta comprimida MyProjectNode-MyProject.zip.

9. En la ventana de comandos de Visual Studio, escriba:

    ```
    devenv /installvstemplates
    ```

   Abra Visual Studio.

10. Abra el cuadro de diálogo **Nuevo proyecto** y expanda el nodo del proyecto de **Visual C.**

    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")

    **MyProjectNode** aparece como un nodo secundario de Visual C. justo debajo del nodo de Windows.

## <a name="see-also"></a>Vea también
- [Nueva generación de proyectos: aspectos técnicos, segunda parte](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
