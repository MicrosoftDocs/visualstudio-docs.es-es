---
title: 'Nueva generación de proyecto: Under the Hood, parte 1 | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ac31f2866c6b69587f70775d5ed1245b1a2bb0a9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Nueva generación de proyecto: Under the Hood, parte 1
¿Imaginar que acerca de cómo crear su propio tipo de proyecto? Se ha preguntado realmente, ¿qué ocurre cuando se crea un nuevo proyecto? Vamos a echar un vistazo en segundo plano y ver lo que realmente está ocurriendo.  
  
 Hay varias tareas que Visual Studio se coordina para usted:  
  
-   Muestra un árbol de todos los tipos de proyecto disponibles.  
  
-   Muestra una lista de plantillas de aplicación para cada tipo de proyecto y le permite elegir uno.  
  
-   Recopila información del proyecto para la aplicación, como el nombre de proyecto y la ruta de acceso.  
  
-   Esta información se pasa en el generador de proyectos.  
  
-   Genera los elementos de proyecto y carpetas en la solución actual.  
  
## <a name="the-new-project-dialog-box"></a>El cuadro de diálogo nuevo proyecto  
 Todo comienza cuando se selecciona un tipo de proyecto para un nuevo proyecto. Puede empezar haciendo clic en **nuevo proyecto** en el **archivo** menú. El **nuevo proyecto** aparece el cuadro de diálogo, aspecto parecido a lo siguiente:  
  
 ![Cuadro de diálogo nuevo proyecto](../../extensibility/internals/media/newproject.gif "nuevo proyecto")  
  
 ¡Eche un vistazo. El **tipos de proyecto** árbol enumera los distintos tipos de proyecto que se puede crear. Al seleccionar un tipo de proyecto como **Windows en Visual C#**, verá una lista de plantillas de aplicación para que pueda comenzar. **Plantillas instaladas de Visual Studio** se instalan con Visual Studio y están disponibles para cualquier usuario del equipo. Se pueden agregar nuevas plantillas que se crean o recopilar a **Mis plantillas** y están disponibles solo a usted.  
  
 Cuando selecciona una plantilla como **aplicación de Windows**, una descripción del tipo de aplicación aparece en el cuadro de diálogo; en este caso, **un proyecto para crear una aplicación con una interfaz de usuario de Windows**.  
  
 En la parte inferior de la **nuevo proyecto** cuadro de diálogo, verá varios controles que recopilan más información. Los controles que se ven dependen del tipo de proyecto, pero generalmente incluyen un proyecto **nombre** cuadro de texto, un **ubicación** cuadro de texto relacionados y **examinar** botón y un **Nombre de la solución** cuadro de texto relacionados y **crear directorio para la solución** casilla de verificación.  
  
## <a name="populating-the-new-project-dialog-box"></a>Rellenar el cuadro de diálogo nuevo proyecto  
 ¿Donde does el **nuevo proyecto** cuadro de diálogo obtener su información de? Hay dos mecanismos en el trabajo en este caso, uno de ellos en desuso. El **nuevo proyecto** cuadro de diálogo combina y muestra la información obtenida de ambos mecanismos.  
  
 El método anterior (en desuso) usa entradas del registro del sistema y los archivos .vsdir. Este mecanismo se ejecuta cuando se abre Visual Studio. El método más reciente utiliza los archivos .vstemplate. Este mecanismo se ejecuta cuando se inicializa Visual Studio, por ejemplo, mediante la ejecución  
  
```  
devenv /setup  
```  
  
 o  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>Tipos de proyecto  
 La posición y los nombres de los **tipos de proyecto** raíz como nodos, **Visual C#** y **otros lenguajes**, viene determinado por las entradas del registro del sistema. La organización de los nodos secundarios, como **base de datos** y **Smart Device**, refleja la jerarquía de las carpetas que contienen los archivos .vstemplate correspondientes. Echemos un vistazo a los nodos raíz en primer lugar.  
  
#### <a name="project-type-root-nodes"></a>Nodos raíz de tipo de proyecto  
 Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está inicializado, recorren las subclaves de la clave del registro de sistema HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs crear y dar nombre a los nodos raíz de la **detiposdeproyecto** árbol. Esta información se almacena en caché para su uso posterior. Mire el TemplateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 clave. Cada entrada es un GUID de VSPackage. El nombre de la subclave (/ 1) se omite, pero su presencia indica que se trata de un **tipos de proyecto** nodo raíz. Un nodo raíz a su vez puede tener varias subclaves que controlan su apariencia en el **tipos de proyecto** árbol. Echemos un vistazo a algunas de ellas.  
  
##### <a name="default"></a>(Predeterminado)  
 Este es el identificador de recurso de la cadena localizada que designa el nodo raíz. El recurso de cadena se encuentra en el archivo DLL seleccionado por el GUID de VSPackage satélite.  
  
 En el ejemplo, el GUID de VSPackage es  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 y el identificador de recurso (valor predeterminado) del nodo raíz (/ 1) es #2345  
  
 Si Buscar el GUID de la clave de paquetes cercano y examine la subclave SatelliteDll, puede encontrar la ruta de acceso del ensamblado que contiene el recurso de cadena:  
  
 \<Ruta de acceso de instalación de Visual Studio > \VC#\VCSPackages\1033\csprojui.dll  
  
 Para comprobarlo, abra el Explorador de archivos y arrastre csprojui.dll en el directorio de Visual Studio... La tabla de cadenas muestra que el recurso #2345 tiene el título **Visual C#**.  
  
##### <a name="sortpriority"></a>SortPriority  
 Esto determina la posición del nodo raíz en el **tipos de proyecto** árbol.  
  
 SortPriority REG_DWORD 0x00000014 (20)  
  
 Cuanto menor sea el número de la prioridad, cuanto mayor sea la posición en el árbol.  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 Si esta subclave está presente, la posición del nodo raíz se controla mediante el cuadro de diálogo Opciones del desarrollador. Por ejemplo,  
  
 DeveloperActivity REG_SZ VC #  
  
 indica que Visual C# será un nodo raíz si Visual Studio está establecido para [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] desarrollo. De lo contrario, será un nodo secundario de **otros lenguajes**.  
  
##### <a name="folder"></a>Carpeta  
 Si esta subclave está presente, el nodo raíz se convierte en un nodo secundario de la carpeta especificada. Aparece una lista de posibles carpetas bajo la clave  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 Por ejemplo, la entrada de proyectos de base de datos tiene una clave de la carpeta que coincida con la entrada de otros tipos de proyectos en PseudoFolders. Por lo tanto, en la **tipos de proyecto** árbol, **proyectos de base de datos** será un nodo secundario de **otros tipos de proyectos**.  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>Nodos secundarios de tipo de proyecto y archivos de .vstdir  
 La posición de los nodos secundarios en el **tipos de proyecto** árbol sigue la jerarquía de las carpetas en las carpetas ProjectTemplates. Las plantillas de máquina (**plantillas instaladas de Visual Studio**), la ubicación típica es \Program 14.0\Common7\IDE\ProjectTemplates\ Visual Studio y plantillas de usuario (**Mis plantillas**), la ubicación típica es Documents\Visual Studio 14.0\Templates\ProjectTemplates\\. Las jerarquías de carpetas de estas dos ubicaciones se combinan para crear la **tipos de proyecto** árbol.  
  
 Para Visual Studio con opciones del desarrollador de C#, la **tipos de proyecto** árbol es algo parecido a esto:  
  
 ![Tipos de proyecto](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 La carpeta correspondiente de ProjectTemplates tiene el siguiente aspecto:  
  
 ![Plantillas de proyecto](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 Cuando el **nuevo proyecto** se abre el cuadro de diálogo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] recorre la carpeta ProjectTemplates y vuelve a crear su estructura está en el **tipos de proyecto** árbol con algunos cambios:  
  
-   El nodo raíz en el **tipos de proyecto** árbol viene determinado por la plantilla de aplicación.  
  
-   El nombre de nodo se puede localizar y puede contener caracteres especiales.  
  
-   Se puede cambiar el criterio de ordenación.  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>Buscar el nodo raíz para un tipo de proyecto  
 Cuando Visual Studio recorre las carpetas ProjectTemplates, abre todos los archivos .zip y extrae los archivos .vstemplate. Un archivo .vstemplate utiliza XML para describir una plantilla de aplicación. Para obtener más información, consulte [nueva generación de proyecto: Under the Hood, parte dos](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 El \<ProjectType > etiqueta determina el tipo de proyecto para la aplicación. Por ejemplo, el archivo \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip contiene un archivo de EmptyProject.vstemplate que tiene esta etiqueta:  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 El \<ProjectType > etiqueta y no la subcarpeta en la carpeta ProjectTemplates, determina el nodo de raíz de la aplicación en el **tipos de proyecto** árbol. En el ejemplo, las aplicaciones de Windows CE aparecerán bajo la **Visual C#** nodo raíz, e incluso si fuera a mover la carpeta WindowsCE a la carpeta de Visual Basic, aplicaciones para Windows CE todavía aparecerán bajo la  **Visual C#** nodo raíz.  
  
##### <a name="localizing-the-node-name"></a>Localizar el nombre de nodo  
 Cuando Visual Studio recorre las carpetas ProjectTemplates, examina los archivos de .vstdir encuentra. Un archivo .vstdir es un archivo XML que controla la apariencia del tipo de proyecto en el **nuevo proyecto** cuadro de diálogo. En el archivo .vstdir, use la \<LocalizedName > etiqueta al nombre de la **tipos de proyecto** nodo.  
  
 Por ejemplo, el archivo \CSharp\Database\TemplateIndex.vstdir contiene esta etiqueta:  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 Esto determina el identificador de recursos y archivos DLL satélite de la cadena localizada que designa el nodo raíz, en este caso, **base de datos**. El nombre localizado puede contener caracteres especiales que no están disponibles para los nombres de carpeta, como **.NET**.  
  
 Si no hay ningún \<LocalizedName > etiqueta está presente, el tipo de proyecto denominado por la propia carpeta, **SmartPhone2003**.  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>Buscar el criterio de ordenación para un tipo de proyecto  
 Para determinar el criterio de ordenación del tipo de proyecto, usan archivos .vstdir la \<SortOrder > etiqueta.  
  
 Por ejemplo, el archivo \CSharp\Windows\Windows.vstdir contiene esta etiqueta:  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 El archivo \CSharp\Database\TemplateIndex.vstdir tiene una etiqueta con un valor mayor:  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 Cuanto menor sea el número en el \<SortOrder > etiqueta, cuanto mayor sea la posición en el árbol, por lo que el **Windows** nodo aparece más arriba que el **base de datos** nodo en el **tipos de proyecto**  árbol.  
  
 Si no hay ningún \<SortOrder > etiqueta se especifica para un tipo de proyecto, aparece en orden alfabético después de cualquier tipo de proyecto que contienen \<SortOrder > especificaciones.  
  
 Tenga en cuenta que no hay ningún archivo .vstdir en Mis documentos (**Mis plantillas**) carpetas. Nombres de tipo de proyecto de aplicación de usuario no están localizados y aparecen en orden alfabético.  
  
#### <a name="a-quick-review"></a>Una revisión rápida  
 Vamos a modificar el **nuevo proyecto** diálogo cuadro y crear una nueva plantilla de proyecto de usuario.  
  
1.  Agregar una subcarpeta MyProjectNode a la carpeta de 14.0\Common7\IDE\ProjectTemplates\CSharp \Program Visual Studio.  
  
2.  Cree un archivo MyProject.vstdir en la carpeta de MyProjectNode mediante cualquier editor de texto.  
  
3.  Agregue estas líneas al archivo .vstdir:  
  
    ```  
    <TemplateDir Version="1.0.0">  
        <SortOrder>6</SortOrder>  
    </TemplateDir>  
    ```  
  
4.  Guarde y cierre el archivo .vstdir.  
  
5.  Cree un archivo MyProject.vstemplate en la carpeta de MyProjectNode mediante cualquier editor de texto.  
  
6.  Agregue estas líneas al archivo .vstemplate:  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <TemplateData>  
            <ProjectType>CSharp</ProjectType>  
        </TemplateData>  
    </VSTemplate>  
    ```  
  
7.  Guarde el archivo de the.vstemplate y cierre el editor.  
  
8.  Envíe el archivo .vstemplate en una nueva carpeta comprimida de MyProjectNode\MyProject.zip.  
  
9. En la ventana de comandos de Visual Studio, escriba:  
  
    ```  
    devenv /installvstemplates  
    ```  
  
 Abra Visual Studio.  
  
1.  Abra la **nuevo proyecto** diálogo cuadro y expanda el **Visual C#** nodo del proyecto.  
  
 ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
 **MyProjectNode** aparece como un nodo secundario de Visual C# situada bajo el nodo de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Nueva generación de proyectos: aspectos técnicos, segunda parte](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)