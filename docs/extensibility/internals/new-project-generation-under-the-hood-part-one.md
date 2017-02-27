---
title: "Nueva generaci&#243;n de proyecto: En realidad, parte 1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proyectos [Visual Studio], cuadro de diálogo nuevo proyecto"
  - "proyectos [Visual Studio], nueva generación del proyecto"
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# Nueva generaci&#243;n de proyecto: En realidad, parte 1
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

¿Cómo crear su propio tipo de proyecto ha pensado alguna vez? ¿Se pregunta lo que ocurre cuando se crea un nuevo proyecto? Vamos a echar un vistazo debajo del capó y ver lo que está ocurriendo realmente.  
  
 Hay varias tareas que coordina Visual Studio para usted:  
  
-   Muestra un árbol de todos los tipos de proyecto disponibles.  
  
-   Muestra una lista de plantillas de aplicación para cada tipo de proyecto y le permite elegir uno.  
  
-   Recopila información del proyecto para la aplicación, como el nombre del proyecto y la ruta de acceso.  
  
-   Esta información se pasa en el generador del proyecto.  
  
-   Genera los elementos de proyecto y carpetas en la solución actual.  
  
## El cuadro de diálogo nuevo proyecto  
 Todo comienza cuando se selecciona un tipo de proyecto para un proyecto nuevo. Empecemos haciendo clic en **nuevo proyecto** en el **archivo** menú. El **nuevo proyecto** aparece el cuadro de diálogo, aspecto algo parecido a esto:  
  
 ![Cuadro de diálogo Nuevo proyecto](../../extensibility/internals/media/newproject.png "NewProject")  
  
 Echemos un vistazo. El **tipos de proyecto** los distintos tipos de proyecto, puede crear listas de árbol. Al seleccionar un tipo de proyecto como **Windows de Visual C\#**, verá una lista de plantillas de aplicación para que pueda comenzar.**Plantillas instaladas de visual Studio** se instalan con Visual Studio y están disponibles para cualquier usuario del equipo. Se pueden agregar plantillas nuevas que cree o recopilar a **Mis plantillas** y están disponibles sólo para usted.  
  
 Al seleccionar una plantilla como **aplicación Windows**, aparece una descripción del tipo de aplicación en el cuadro de diálogo; en este caso, **un proyecto para crear una aplicación con una interfaz de usuario de Windows**.  
  
 En la parte inferior de la **nuevo proyecto** cuadro de diálogo, verá varios controles que recopilan más información. Los controles que se ven dependen del tipo de proyecto, pero generalmente incluyen un proyecto **nombre** cuadro de texto, un **ubicación** cuadro de texto relacionados y **Examinar** botón y un **nombre de la solución** cuadro de texto relacionados y **Crear directorio para la solución** casilla de verificación.  
  
## Rellenar el cuadro de diálogo nuevo proyecto  
 ¿Donde does el **nuevo proyecto** cuadro de diálogo obtener su información de? Existen dos mecanismos en el trabajo aquí, uno de ellos en desuso. El **nuevo proyecto** cuadro de diálogo combina y muestra la información obtenida de dos mecanismos.  
  
 El método anterior \(en desuso\) usa las entradas del registro de sistema y los archivos .vsdir. Este mecanismo se ejecuta cuando se abre Visual Studio. El método más reciente utiliza los archivos .vstemplate. Este mecanismo se ejecuta cuando se inicializa Visual Studio, por ejemplo, mediante la ejecución  
  
```  
devenv /setup  
```  
  
 o  
  
```  
devenv /installvstemplates  
```  
  
### Tipos de proyecto  
 La posición y los nombres de los **tipos de proyecto** root de nodos, como **Visual C\#** y **otros lenguajes**, viene determinado por las entradas del registro del sistema. La organización de los nodos secundarios, como **base de datos** y **Smart Device**, refleja la jerarquía de las carpetas que contienen los archivos .vstemplate correspondientes. Echemos un vistazo a los nodos raíz en primer lugar.  
  
#### Nodos raíz de tipo de proyecto  
 Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está inicializado, recorre las subclaves de la clave del registro del sistema HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\14.0\\NewProjectTemplates\\TemplateDirs para generar y el nombre de los nodos raíz de la **tipos de proyecto** árbol. Esta información se almacena en caché para su uso posterior. Un vistazo a la clave de \\\/1 TemplateDirs\\ {FAE04EC1\-301F\-11D3\-BF4B\-00C04F79EFBC}. Cada entrada es un GUID de VSPackage. El nombre de la subclave \(\/ 1\) se omite, pero su presencia indica que se trata de un **tipos de proyecto** nodo raíz. Un nodo raíz puede tener varias subclaves que controlan su apariencia en el **tipos de proyecto** árbol. Echemos un vistazo a algunos de ellos.  
  
##### \(Predeterminado\)  
 Es el identificador de recurso de la cadena traducida que los nombres del nodo raíz. El recurso de cadena se encuentra en el archivo seleccionado por el GUID de VSPackage DLL satélite.  
  
 En el ejemplo, el GUID de VSPackage es  
  
 {FAE04EC1\-301F\-11D3\-BF4B\-00C04F79EFBC}  
  
 y el identificador de recurso \(valor predeterminado\) del nodo raíz \(\/ 1\) es \#2345  
  
 Si Buscar el GUID en la clave de paquetes cercano y examine la subclave SatelliteDll, puede encontrar la ruta de acceso del ensamblado que contiene el recurso de cadena:  
  
 \< ruta de instalación de visual Studio \> \\VC\#\\VCSPackages\\1033\\csprojui.dll  
  
 Para comprobarlo, abra el Explorador de archivos y arrastre csprojui.dll en el directorio de Visual Studio... La tabla de cadenas muestra que el recurso \#2345 tiene el título **Visual C\#**.  
  
##### SortPriority  
 Determina la posición del nodo raíz en el **tipos de proyecto** árbol.  
  
 SortPriority REG\_DWORD 0x00000014 \(20\)  
  
 Cuanto menor sea el número de prioridad, mayor será la posición en el árbol.  
  
##### DeveloperActivity  
 Si esta subclave está presente, la posición del nodo raíz se controla mediante el cuadro de diálogo Opciones del desarrollador. Por ejemplo,  
  
 DeveloperActivity REG\_SZ VC \#  
  
 indica que Visual C\# será un nodo raíz si Visual Studio está establecido para [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] desarrollo. De lo contrario, será un nodo secundario de **otros lenguajes**.  
  
##### Carpeta  
 Si esta subclave está presente, el nodo raíz se convierte en un nodo secundario de la carpeta especificada. Aparece una lista de posibles carpetas bajo la clave  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\11.0\\NewProjectTemplates\\PseudoFolders  
  
 Por ejemplo, la entrada de los proyectos de base de datos tiene una clave de la carpeta que coincide con la entrada de otros tipos de proyectos de PseudoFolders. Por lo tanto, en el **tipos de proyecto** árbol, **proyectos de base de datos** será un nodo secundario de **otros tipos de proyectos**.  
  
#### Nodos secundarios de tipo de proyecto y archivos .vstdir  
 La posición de los nodos secundarios en el **tipos de proyecto** árbol sigue la jerarquía de las carpetas en las carpetas ProjectTemplates. Las plantillas de máquina \(**Plantillas instaladas de Visual Studio**\), la ubicación típica es \\Program 14.0\\Common7\\IDE\\ProjectTemplates\\ Visual Studio y plantillas de usuario \(**Mis plantillas**\), la ubicación típica es Documents\\Visual Studio 14.0\\Templates\\ProjectTemplates\\. Las jerarquías de carpetas de estas dos ubicaciones se combinan para crear la **tipos de proyecto** árbol.  
  
 Para Visual Studio con opciones del desarrollador de C\#, el **tipos de proyecto** árbol parecido al siguiente:  
  
 ![Tipos de proyecto](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 La carpeta ProjectTemplates correspondiente tiene este aspecto:  
  
 ![Plantillas de proyecto](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 Cuando el **nuevo proyecto** se abre el cuadro de diálogo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] recorre la carpeta ProjectTemplates y vuelve a crear su estructura en el **tipos de proyecto** árbol con algunos cambios:  
  
-   El nodo raíz en el **tipos de proyecto** árbol viene determinado por la plantilla de aplicación.  
  
-   El nombre de nodo se puede localizar y puede contener caracteres especiales.  
  
-   Se puede cambiar el criterio de ordenación.  
  
##### Buscar el nodo raíz para un tipo de proyecto  
 Cuando Visual Studio recorre las carpetas ProjectTemplates, abre todos los archivos .zip y extrae los archivos .vstemplate. Un archivo .vstemplate usa XML para describir una plantilla de aplicación. Para obtener más información, consulta [Nueva generación de proyecto: Bajo el capó, segunda parte](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 La etiqueta \< ProjectType \> determina el tipo de proyecto para la aplicación. Por ejemplo, el archivo \\CSharp\\SmartDevice\\WindowsCE\\1033\\WindowsCE\-EmptyProject.zip contiene un archivo EmptyProject.vstemplate que tiene esta etiqueta:  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 La etiqueta \< ProjectType \> y no la subcarpeta en la carpeta ProjectTemplates, determina el nodo de raíz de la aplicación en el **tipos de proyecto** árbol. En el ejemplo, las aplicaciones de Windows CE aparecerán bajo la **Visual C\#** nodo raíz, e incluso si fuera a mover la carpeta WindowsCE a la carpeta de Visual Basic, aplicaciones para Windows CE aún aparecerán bajo la **Visual C\#** nodo raíz.  
  
##### Localizar el nombre de nodo  
 Cuando Visual Studio recorre las carpetas ProjectTemplates, examina los archivos .vstdir. Un archivo .vstdir es un archivo XML que controla la apariencia del tipo de proyecto en el **nuevo proyecto** cuadro de diálogo. En el archivo .vstdir, use la etiqueta \< LocalizedName \> al nombre de la **tipos de proyecto** nodo.  
  
 Por ejemplo, el archivo \\CSharp\\Database\\TemplateIndex.vstdir contiene esta etiqueta:  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 Esto determina el identificador de recursos y archivos DLL satélite de la cadena traducida que designa el nodo raíz, en este caso, **base de datos**. El nombre localizado puede contener caracteres especiales que no están disponibles para los nombres de carpeta, como **.NET**.  
  
 Si no hay ninguna etiqueta \< LocalizedName \> está presente, el tipo de proyecto denominado por la propia carpeta, **SmartPhone2003**.  
  
##### Buscar el criterio de ordenación para un tipo de proyecto  
 Para determinar el criterio de ordenación del tipo de proyecto, archivos de .vstdir utilizan la etiqueta \< SortOrder \>.  
  
 Por ejemplo, el archivo \\CSharp\\Windows\\Windows.vstdir contiene esta etiqueta:  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 El archivo \\CSharp\\Database\\TemplateIndex.vstdir tiene una etiqueta con un valor mayor:  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 Cuanto menor sea el número en el \< SortOrder \> etiqueta, cuanto mayor sea la posición en el árbol para que el **Windows** aparecerá el nodo superior del **base de datos** nodo en el **tipos de proyecto** árbol.  
  
 Si no se especifica ninguna etiqueta \< SortOrder \> para un tipo de proyecto, aparece después de los tipos de proyecto que contienen especificaciones \< SortOrder \> por orden alfabético.  
  
 Tenga en cuenta que no hay ningún archivo .vstdir en los documentos \(**Mis plantillas**\) carpetas. Nombres de tipo de proyecto de aplicación de usuario no están localizados y aparecen en orden alfabético.  
  
#### Una revisión rápida  
 Vamos a modificar el **nuevo proyecto** cuadro de diálogo y cree una nueva plantilla de proyecto de usuario.  
  
1.  Agregue una subcarpeta MyProjectNode a la carpeta de 14.0\\Common7\\IDE\\ProjectTemplates\\CSharp \\Program Visual Studio.  
  
2.  Cree un archivo MyProject.vstdir en la carpeta MyProjectNode con cualquier editor de texto.  
  
3.  Agregue estas líneas al archivo .vstdir:  
  
    ```  
    <TemplateDir Version="1.0.0">  
        <SortOrder>6</SortOrder>  
    </TemplateDir>  
    ```  
  
4.  Guarde y cierre el archivo .vstdir.  
  
5.  Cree un archivo MyProject.vstemplate en la carpeta MyProjectNode con cualquier editor de texto.  
  
6.  Agregue estas líneas al archivo .vstemplate:  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <TemplateData>  
            <ProjectType>CSharp</ProjectType>  
        </TemplateData>  
    </VSTemplate>  
    ```  
  
7.  Guarde el archivo the.vstemplate y cierre el editor.  
  
8.  Envíe el archivo .vstemplate en una nueva carpeta comprimida de MyProjectNode\\MyProject.zip.  
  
9. En la ventana de comandos de Visual Studio, escriba:  
  
    ```  
    devenv /installvstemplates  
    ```  
  
 Abra Visual Studio.  
  
1.  Abra la **nuevo proyecto** diálogo cuadro y expanda el **Visual C\#** nodo del proyecto.  
  
 ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
 **MyProjectNode** aparece como un nodo secundario de Visual C\# sólo bajo el nodo de Windows.  
  
## Vea también  
 [Nueva generación de proyecto: Bajo el capó, segunda parte](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)