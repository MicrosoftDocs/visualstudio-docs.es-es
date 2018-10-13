---
title: 'Nueva generación de proyectos: Aspectos técnicos, primera parte | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 122ef6b8f1e597006fd53e6360d10d304cc760b8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302619"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Nueva generación de proyectos: aspectos técnicos, primera parte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

¿Cómo crear su propio tipo de proyecto ha pensado alguna vez? ¿Se ha preguntado qué pasará cuando cree un nuevo proyecto? Vamos a echar un vistazo en segundo plano y ver lo que realmente está ocurriendo.  
  
 Hay varias tareas que coordina la Visual Studio para usted:  
  
-   Muestra un árbol de todos los tipos de proyecto disponibles.  
  
-   Muestra una lista de plantillas de aplicación para cada tipo de proyecto y le permite elegir uno.  
  
-   Recopila información del proyecto para la aplicación, como el nombre del proyecto y la ruta de acceso.  
  
-   Esta información se pasa en el generador de proyectos.  
  
-   Genera los elementos de proyecto y carpetas en la solución actual.  
  
## <a name="the-new-project-dialog-box"></a>El cuadro de diálogo nuevo proyecto  
 Todo comienza cuando se selecciona un tipo de proyecto para un nuevo proyecto. Empecemos haciendo **nuevo proyecto** en el **archivo** menú. El **nuevo proyecto** aparece el cuadro de diálogo, aspecto algo parecido a esto:  
  
 ![Cuadro de diálogo nuevo proyecto](../../extensibility/internals/media/newproject.gif "NewProject")  
  
 Echemos un vistazo. El **tipos de proyecto** árbol enumera los distintos tipos de proyecto, puede crear. Al seleccionar un tipo de proyecto como **Visual C# Windows**, verá una lista de plantillas de aplicación para que pueda comenzar. **Plantillas instaladas de Visual Studio** se instalan con Visual Studio y están disponibles para cualquier usuario del equipo. Se pueden agregar nuevas plantillas que se crean o recopilar a **Mis plantillas** y están disponibles solo para usted.  
  
 Al seleccionar una plantilla como **aplicación Windows**, aparece una descripción del tipo de aplicación en el cuadro de diálogo; en este caso, **un proyecto para crear una aplicación con una interfaz de usuario de Windows**.  
  
 En la parte inferior de la **nuevo proyecto** cuadro de diálogo, verá varios controles que recopilación más información. Los controles que ve dependen del tipo de proyecto, pero generalmente incluyen un proyecto **nombre** cuadro de texto, un **ubicación** cuadro de texto relacionados y **examinar** botón y un **Nombre de la solución** cuadro de texto relacionados y **crear directorio para la solución** casilla de verificación.  
  
## <a name="populating-the-new-project-dialog-box"></a>Rellenar el cuadro de diálogo nuevo proyecto  
 ¿Donde does el **nuevo proyecto** cuadro de diálogo obtener su información de? Hay dos mecanismos en el trabajo en este caso, uno de ellos en desuso. El **nuevo proyecto** cuadro de diálogo combina y muestra la información obtenida de ambos mecanismos.  
  
 El método anterior (en desuso) usa las entradas de registro del sistema y archivos .vsdir. Este mecanismo se ejecuta cuando se abre Visual Studio. El método más reciente utiliza los archivos .vstemplate. Este mecanismo se ejecuta cuando se inicializa Visual Studio, por ejemplo, mediante la ejecución  
  
```  
devenv /setup  
```  
  
 o  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>Tipos de proyecto  
 La posición y nombres de los **tipos de proyecto** raíz como nodos, **Visual C#** y **otros lenguajes**, viene determinada por las entradas de registro del sistema. La organización de los nodos secundarios, como **base de datos** y **Smart Device**, refleja la jerarquía de las carpetas que contienen los archivos .vstemplate correspondientes. Echemos un vistazo a los nodos raíz en primer lugar.  
  
#### <a name="project-type-root-nodes"></a>Nodos raíz de tipo de proyecto  
 Cuando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] está inicializado, recorre las subclaves de la clave del registro del sistema HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs crear y dar nombre a los nodos raíz de la **detiposdeproyecto** árbol. Esta información se almacena en caché para su uso posterior. Examine el TemplateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 clave. Cada entrada es un GUID de VSPackage. El nombre de la subclave (/ 1) se omite, pero su presencia indica que se trata de un **tipos de proyecto** nodo raíz. Un nodo raíz a su vez puede tener varias subclaves que controlan su apariencia en el **tipos de proyecto** árbol. Echemos un vistazo a algunos de ellos.  
  
##### <a name="default"></a>(Predeterminado)  
 Es el identificador de recurso de la cadena localizada que designa el nodo raíz. El recurso de cadena se encuentra en el archivo seleccionado por el GUID de VSPackage DLL satélite.  
  
 En el ejemplo, el GUID de VSPackage es  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 y el identificador de recurso (valor predeterminado) del nodo raíz (/ 1) es #2345  
  
 Si Buscar el GUID de la clave de los paquetes cercano y examina la subclave SatelliteDll, puede encontrar la ruta de acceso del ensamblado que contiene el recurso de cadena:  
  
 \<Ruta de instalación de Visual Studio > \VC#\VCSPackages\1033\csprojui.dll  
  
 Para comprobarlo, abra el Explorador de archivos y arrastre csprojui.dll en el directorio de Visual Studio... La tabla de cadenas muestra que el recurso #2345 tiene el título **Visual C#**.  
  
##### <a name="sortpriority"></a>SortPriority  
 Esto determina la posición del nodo raíz en el **tipos de proyecto** árbol.  
  
 REG_DWORD SortPriority 0x00000014 (20)  
  
 Cuanto menor sea el número de la prioridad, mayor será la posición en el árbol.  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 Si esta subclave está presente, a continuación, la posición del nodo raíz se controla mediante el cuadro de diálogo Opciones del desarrollador. Por ejemplo,  
  
 REG_SZ DeveloperActivity VC #  
  
 indica que Visual C# será un nodo raíz si Visual Studio se establece para [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] desarrollo. De lo contrario, será un nodo secundario de **otros lenguajes**.  
  
##### <a name="folder"></a>Carpeta  
 Si esta subclave está presente, el nodo raíz se convierte en un nodo secundario de la carpeta especificada. Aparece una lista de posibles carpetas bajo la clave  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 Por ejemplo, la entrada de los proyectos de base de datos tiene una clave de la carpeta que coincide con la entrada de otros tipos de proyectos de PseudoFolders. Por lo tanto, en el **tipos de proyecto** árbol, **proyectos de base de datos** será un nodo secundario de **otros tipos de proyectos**.  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>Los nodos secundarios de tipo de proyecto y los vstdir archivos  
 La posición de los nodos secundarios en el **tipos de proyecto** árbol sigue a la jerarquía de las carpetas en las carpetas ProjectTemplates. Las plantillas de máquina (**plantillas instaladas de Visual Studio**), la ubicación típica es \Program 14.0\Common7\IDE\ProjectTemplates\ Visual Studio y plantillas de usuario (**Mis plantillas**), la ubicación típica es Documents\Visual Studio 14.0\Templates\ProjectTemplates\\. Las jerarquías de carpetas de estas dos ubicaciones se combinan para crear el **tipos de proyecto** árbol.  
  
 Para Visual Studio con la configuración de desarrollador de C#, la **tipos de proyecto** árbol es algo parecido a esto:  
  
 ![Tipos de proyecto](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 La carpeta ProjectTemplates correspondiente tiene este aspecto:  
  
 ![Plantillas de proyecto](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 Cuando el **nuevo proyecto** abre el cuadro de diálogo, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] recorre la carpeta ProjectTemplates y vuelve a crear su estructura está en el **tipos de proyecto** árbol con algunos cambios:  
  
-   El nodo raíz en el **tipos de proyecto** árbol viene determinada por la plantilla de aplicación.  
  
-   El nombre de nodo se puede localizar y puede contener caracteres especiales.  
  
-   Se puede cambiar el criterio de ordenación.  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>Buscar el nodo raíz de un tipo de proyecto  
 Cuando Visual Studio recorre las carpetas ProjectTemplates, abre todos los archivos .zip y extrae los archivos .vstemplate. Un archivo .vstemplate usa XML para describir una plantilla de aplicación. Para obtener más información, consulte [nueva generación de proyectos: Under the Hood, segunda parte](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 El \<ProjectType > etiqueta determina el tipo de proyecto para la aplicación. Por ejemplo, el archivo \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip contiene un archivo EmptyProject.vstemplate que tiene esta etiqueta:  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 El \<ProjectType > etiqueta y no la subcarpeta en la carpeta ProjectTemplates, determina el nodo raíz de la aplicación en el **tipos de proyecto** árbol. En el ejemplo, las aplicaciones de Windows CE aparecerán bajo el **Visual C#** nodo raíz, y aunque hayan mover la carpeta WindowsCE a la carpeta de Visual Basic, las aplicaciones de Windows CE aún podrían aparecer bajo el  **Visual C#** nodo raíz.  
  
##### <a name="localizing-the-node-name"></a>Localizar el nombre del nodo  
 Cuando Visual Studio recorre las carpetas ProjectTemplates, examina todos los vstdir archivos que encuentre. Un archivo vstdir es un archivo XML que controla la apariencia del tipo de proyecto en el **nuevo proyecto** cuadro de diálogo. En el archivo vstdir, use el \<LocalizedName > etiqueta al nombre de la **tipos de proyecto** nodo.  
  
 Por ejemplo, el archivo \CSharp\Database\TemplateIndex.vstdir contiene esta etiqueta:  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 Esto determina el identificador de recursos y el archivo DLL satélite de la cadena localizada que designa el nodo raíz, en este caso, **base de datos**. El nombre localizado puede contener caracteres especiales que no están disponibles para los nombres de carpeta, como **.NET**.  
  
 Si no hay ningún \<LocalizedName > etiqueta está presente, la propia carpeta, el nombre del tipo de proyecto **SmartPhone2003**.  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>Buscar el criterio de ordenación para un tipo de proyecto  
 Para determinar el criterio de ordenación del tipo de proyecto, usan los archivos de los vstdir el \<SortOrder > etiqueta.  
  
 Por ejemplo, el archivo \CSharp\Windows\Windows.vstdir contiene esta etiqueta:  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 El archivo \CSharp\Database\TemplateIndex.vstdir tiene una etiqueta con un valor mayor:  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 Cuanto menor sea el número de la \<SortOrder > etiqueta, cuanto mayor sea la posición en el árbol, por lo que el **Windows** aparecerá el nodo superior del **base de datos** nodo en el **tipos de proyecto**  árbol.  
  
 Si no hay ningún \<SortOrder > etiqueta a la que se especifica para un tipo de proyecto, aparece en orden alfabético siguiendo los tipos de proyecto que contienen \<SortOrder > especificaciones.  
  
 Tenga en cuenta que no hay ningún archivo vstdir en los documentos de mi (**Mis plantillas**) carpetas. Nombres de tipo de proyecto de aplicación de usuario no están localizados y aparecen en orden alfabético.  
  
#### <a name="a-quick-review"></a>Una revisión rápida  
 Vamos a modificar el **nuevo proyecto** diálogo cuadro y crear una nueva plantilla de proyecto de usuario.  
  
1.  Agregar una subcarpeta MyProjectNode a la carpeta \Archivos 14.0\Common7\IDE\ProjectTemplates\CSharp de Visual Studio \Program Files\Microsoft.  
  
2.  Cree un archivo MyProject.vstdir en la carpeta MyProjectNode con cualquier editor de texto.  
  
3.  Agregue estas líneas al archivo vstdir:  
  
    ```  
    <TemplateDir Version="1.0.0">  
        <SortOrder>6</SortOrder>  
    </TemplateDir>  
    ```  
  
4.  Guarde y cierre el archivo vstdir.  
  
5.  Cree un archivo MyProject.vstemplate en la carpeta MyProjectNode con cualquier editor de texto.  
  
6.  En el archivo .vstemplate, agregue estas líneas:  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <TemplateData>  
            <ProjectType>CSharp</ProjectType>  
        </TemplateData>  
    </VSTemplate>  
    ```  
  
7.  Guarde el archivo de the.vstemplate y cierre el editor.  
  
8.  Envíe el archivo .vstemplate en una nueva carpeta MyProjectNode\MyProject.zip comprimida.  
  
9. En la ventana de comandos de Visual Studio, escriba:  
  
    ```  
    devenv /installvstemplates  
    ```  
  
 Abra Visual Studio.  
  
1.  Abra el **nuevo proyecto** diálogo cuadro y expanda el **Visual C#** nodo del proyecto.  
  
 ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
 **MyProjectNode** aparece como un nodo secundario de Visual C# solo en el nodo de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Nueva generación de proyectos: aspectos técnicos, segunda parte](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

