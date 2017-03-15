---
title: "Registra un tipo de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proyectos [Visual Studio SDK], nuevas entradas del registro del proyecto"
  - "registro de nuevos tipos de proyecto"
  - "registro de nuevos tipos de proyecto"
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Registra un tipo de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cuando se crea un nuevo tipo de proyecto, debe crear las entradas de Registro que permiten a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] reconozca y para trabajar con el tipo de proyecto.  Normalmente crea estas entradas de Registro utilizando un archivo de script de registro \(.rgs\).  
  
 En el ejemplo siguiente, las instrucciones de registro proporcionan las rutas predeterminadas y los datos se precisa, seguido de una tabla que contiene entradas de script de registro para cada instrucción.  Las tablas proporcionan las entradas de script y la información adicional sobre las instrucciones.  
  
> [!NOTE]
>  La siguiente información del registro está diseñado para ser un ejemplo de tipo y de los propósitos de las entradas de los scripts del registro que escribirá para registrar el tipo de proyecto.  Las entradas reales y su utilizan pueden variar según los requisitos específicos del tipo de proyecto.  Debe revisar los ejemplos disponibles para buscar uno que se asemeje cerca del tipo de proyecto que se está desarrollando, y después para revisar el script de registro para ese ejemplo.  
  
 los ejemplos siguientes son de HKEY\_CLASSES\_ROOT.  
  
## Ejemplo  
  
```  
\.figp  
   @="FigPrjFile"  
   "Content Type"="text/plain"  
\.figp\ShellNew  
   "NullFile"=""  
\FigPrjFile  
   @="Figure Project File"  
\DefaultIcon  
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"  
\shell\open  
   @="&Open in Visual Studio"  
\shell\open\command  
   @="devenv.exe \"%1\""  
```  
  
|Name|Tipo|Datos|Descripción|  
|----------|----------|-----------|-----------------|  
|`@`|REG\_SZ|`FigPrjFile`|Nombre y descripción de los archivos del tipo de proyecto que tienen la extensión .figp.|  
|`Content Type`|REG\_SZ|`Text/plain`|Tipo de contenido de los archivos de proyecto.|  
|`NullFile`|REG\_SZ|`Null`||  
|`@`|REG\_SZ|`%MODULE%,-206`|icono predeterminado utilizado para el proyecto de este tipo.  La instrucción de %MODULE% se completa en el registro en la ubicación predeterminada del tipo de proyecto DLL.|  
|`@`|REG\_SZ|`&Open in Visual Studio`|Aplicación predeterminada en que se abrirán a este tipo de proyecto.|  
|`@`|REG\_SZ|`devenv.exe "%1"`|Comando predeterminado que se ejecutará cuando se abre un proyecto de este tipo.|  
  
 Los ejemplos siguientes son HKEY\_LOCAL\_MACHINE y se encuentran en el registro bajo la clave \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\99.0Exp\\Packages\].  
  
## Ejemplo  
  
```  
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)  
   @="FigPrj Project Package"  
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"  
   "CompanyName"="Microsoft"  
   "ProductName"="Figure Project Sample"  
   "ProductVersion"="9.0"  
   "MinEdition"="professional"  
   "ID"=dword:00000001  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL  
   "DllName"="FigPrjUI.dll"  
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation  
   "FigProjects"=""  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents  
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"  
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"  
```  
  
|Name|Tipo|Datos|Descripción|  
|----------|----------|-----------|-----------------|  
|`@`\(valor predeterminado\)|REG\_SZ|`FigPrj Project VSPackage`|Nombre localizable de este paquete VSPackage registrado \(tipo de proyecto\).|  
|`InprocServer32`|REG\_SZ|`%MODULE%`|Ruta de acceso del tipo de proyecto DLL.  El IDE carga esta DLL y pasa el paquete VSPackage CLSID en `DllGetClassObject` para obtener <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> para construir el objeto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> .|  
|`CompanyName`|REG\_SZ|`Microsoft`|nombre de la compañía que desarrolló el tipo de proyecto.|  
|`ProductName`|REG\_SZ|`Figure Project Sample`|Nombre del tipo de proyecto.|  
|`ProductVersion`|REG\_SZ|`9.0`|Número de versión de lanzamiento del tipo de proyecto.|  
|`MinEdition`|REG\_SZ|`professional`|Edición de VSPackage que está registrado.|  
|`ID`|REG\_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|La clave de carga del paquete para el proyecto VSPackage.  Se valida la clave cuando un proyecto se carga cuando se haya iniciado el entorno.|  
|`DllName`|REG\_SZ|`%RESOURCE_DLL%`|Nombre de archivo del archivo DLL satélite que contiene recursos adaptados para el tipo de proyecto.|  
|`Path`|REG\_SZ|`%RESOURCE_PATH%`|Ruta del archivo DLL satélite.|  
|`FigProjectsEvents`|REG\_SZ|Vea la instrucción por valor.|Determina la cadena de texto devuelta para este evento de automatización.|  
|`FigProjectItemsEvents`|REG\_SZ|Vea la instrucción por valor.|Determina la cadena de texto devuelta para este evento de automatización.|  
  
 Todos los ejemplos siguientes se encuentran en el registro bajo la clave \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Projects\].  
  
## Ejemplo  
  
```  
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)  
   @="FigPrj Project"  
   "DisplayName"="#2"  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"  
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"  
   "DisplayProjectFileExtensions"="#3"  
   "PossibleProjectExtensions"="figp"  
   "DefaultProjectExtension"=".figp"  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)  
   @="#4"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000000  
   "FindInFilesFilter"=dword:00000000  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2  
      (Folder 2 contains settings for Find in Files filters.)  
   @="#5"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000001  
   "FindInFilesFilter"=dword:00000001  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Name|Tipo|Datos|Descripción|  
|----------|----------|-----------|-----------------|  
|`@`|REG\_SZ|`FigPrj Project`|Nombre predeterminado de proyectos de este tipo.|  
|`DisplayName`|REG\_SZ|`#%IDS_PROJECT_TYPE%`|Id. de recurso del que se recuperará de DLL satélite registrado en paquetes.|  
|`Package`|REG\_SZ|`%CLSID_Package%`|Identificador de la clase de VSPackage registrado en paquetes.|  
|`ProjectTemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|ruta de acceso predeterminada de los archivos de plantilla de proyecto.  Éstos son los archivos mostrados por la plantilla de proyecto.|  
|`ItemTemplatesDir`|REG\_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Ruta de acceso predeterminada de los archivos de plantilla de elemento de proyecto.  Éstos son los archivos mostrados por la plantilla de agregar nuevo elemento.|  
|`DisplayProjectFileExtensions`|REG\_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Permite al IDE para implementar el cuadro de diálogo de **Abrir** .|  
|`PossibleProjectExtensions`|REG\_SZ|`figp`|Utilizado por el IDE para determinar si el proyecto que está abierto controla este tipo de proyecto \(generador de proyectos\).  El formato para más de una entrada es una lista delimitada por punto y coma.  por ejemplo “vdproj; vdp”.|  
|`DefaultProjectExtension`|REG\_SZ|`.figp`|Utilizado por el IDE como extensión de nombre de archivo predeterminada para el Guardar como operación.|  
|`Filter Settings`|REG\_DWORD|Diferente, vea instrucciones y comentarios después de tabla.|Estos valores se utilizan para establecer varios filtros para mostrar los archivos en cuadros de diálogo de la interfaz de usuario.|  
|`@`|REG\_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Id. de recurso para las plantillas de elemento Add.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Ruta de los elementos de proyecto mostrados en el cuadro de diálogo para la plantilla de **Agregar nuevo elemento** .|  
|`SortPriority`|REG\_DWORD|`100 (vcprx64)`|Determina el criterio de ordenación en el nodo de árbol de los archivos mostrados en el cuadro de diálogo de **Agregar nuevo elemento** .|  
  
 La tabla siguiente se muestran las opciones de los filtros disponibles en el segmento de código anterior.  
  
|opción de filtro|Descripción|  
|----------------------|-----------------|  
|`CommonFindFilesFilter`|indica que el filtro es uno de los filtros comunes en el cuadro de diálogo de **Buscar en archivos** .  Filtros comunes se muestran en la lista de filtros antes de los filtros no marcados como común.|  
|`CommonOpenFilesFilter`|indica que el filtro es uno de los filtros comunes en el cuadro de diálogo de **Abrir archivo** .  Filtros comunes se muestran en la lista de filtros antes de los filtros no marcados como común.|  
|`FindInFilesFilter`|Indica que el filtro es uno de los filtros en el cuadro de diálogo de **Buscar en archivos** y aparecerá después de que los filtros de común.|  
|`NotOpenFileFilter`|Indica que el filtro no se usará en el cuadro de diálogo de **Abrir archivo** .|  
|`NotAddExistingItemFilter`|Indica que el filtro no se usará en el cuadro de diálogo de **Elemento existente** add.|  
  
 De forma predeterminada, si un filtro no tiene uno o más de estos marcadores establecidos, el filtro se utiliza en el cuadro de diálogo de **Agregar elemento existente** y el cuadro de diálogo de **Abrir archivo** después de que se enumeran los filtros comunes.  el filtro no se utiliza en el cuadro de diálogo de **Buscar en archivos** .  
  
 Todos los ejemplos siguientes se encuentran en el registro bajo la clave \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Projects\].  
  
## Ejemplo  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Name|Tipo|Datos|Descripción|  
|----------|----------|-----------|-----------------|  
|`@`|REG\_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Id. de recurso para las plantillas de proyecto.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Ruta de acceso predeterminada para los proyectos del tipo de proyecto registrado.|  
|`SortPriority`|REG\_DWORD|`41 (x29)`|Establece el criterio de ordenación de los proyectos mostrados en el cuadro de diálogo asistente para proyectos de Nuevo.|  
|`NewProjectDialogOnly`|REG\_DWORD|`0`|0 indica que los proyectos de este tipo solo deben mostrarse en el cuadro de diálogo Nuevo proyecto.|  
  
 Todos los ejemplos siguientes se encuentran en el registro bajo la clave \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Projects\].  
  
## Ejemplo  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Name|Tipo|Datos|Descripción|  
|----------|----------|-----------|-----------------|  
|`@`|REG\_SZ|None|El valor predeterminado que indica que las entradas siguientes son para los archivos varios proyectos entradas.|  
|`@`|REG\_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Valor de Id. de recurso de los archivos de plantilla de elementos de agregar nueva.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Ruta de acceso predeterminada de los elementos que se muestran en el cuadro de diálogo de **Agregar nuevo elemento** .|  
|`SortPriority`|REG\_DWORD|`100 (vcprx64)`|Establece el criterio de ordenación para la presentación en el nodo de árbol del cuadro de diálogo de **Agregar nuevo elemento** .|  
  
 El ejemplo siguiente se encuentra en el registro bajo la clave \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Menus\].  
  
## Ejemplo  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 Los puntos de entrada de menú el IDE al recurso utilizado para recuperar información del menú.  Cuando estos datos se ha combinado en la base de datos en el menú, la misma clave se agregará en la sección de MenusMerged del registro.  El Paquete no debe modificar nada en la sección de MenusMerged directamente.  en el campo de datos en la tabla siguiente, hay tres coma\-separar\-campos.  El primer campo identifica una ruta de acceso completa de un archivo de recursos de menús:  
  
-   Si se omite el primer campo, el recurso de menú se cargan desde un archivo DLL satélite identificado por el paquete VSPackage GUID.  
  
 El segundo campo identifica un Id. de recurso de menú de tipo CTMENU:  
  
-   Si se especifica el Id. de recurso, y la ruta de acceso del archivo es proporcionada por el primer parámetro, un recurso de menú se carga desde la ruta completa del archivo.  
  
-   Si se proporciona el Id. de recurso, pero no es la ruta del archivo, el recurso de menú se cargan desde un archivo DLL satélite.  
  
-   Si se proporciona la ruta completa del archivo y se omite el Id. de recurso, el archivo que se cargará es esperado es un archivo de CTO.  
  
 El último campo identifica el número de versión para el recurso de CTMENU.  Puede combinar el menú de nuevo cambiando el número de versión.  
  
|Name|Tipo|Datos|Descripción|  
|----------|----------|-----------|-----------------|  
|el %CLSID\_Package%|REG\_SZ|`,1000,1`|El recurso para recuperar información del menú.|  
  
 Todos los ejemplos siguientes se encuentran en el registro bajo la clave \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\NewProjectTemplates\].  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Name|Tipo|Datos|Descripción|  
|----------|----------|-----------|-----------------|  
|`@`|REG\_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Valor de Id. de recurso para las plantillas de proyecto nuevo del proyecto de las figuras.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|La ruta de acceso predeterminada de Nuevo proyecta el directorio.  Los elementos en este directorio se mostrarán en el cuadro de diálogo de **Asistente para nuevo proyecto** .|  
|`SortPriority`|REG\_DWORD|`41 (x29)`|Establece el orden en que los proyectos se mostrarán en el nodo de árbol del cuadro de diálogo de **Nuevo proyecto** .|  
|`NewProjectDialogOnly`|REG\_DWORD|`0`|0 indica que los proyectos de este tipo solo deben mostrarse en el cuadro de diálogo de **Nuevo proyecto** .|  
  
 El ejemplo siguiente se encuentra en el registro bajo la clave \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\InstalledProducts\].  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|Name|Tipo|Datos|Descripción|  
|----------|----------|-----------|-----------------|  
|`Package`|REG\_SZ|`%CLSID_Package%`|Identificador de la clase de VSPackage registrado.|  
|`UseInterface`|REG\_DWORD|`1`|1 indica que la interfaz de usuario se utilizará para interactuar con este proyecto.  0 indica que no hay ninguna interfaz de la interfaz de usuario.|  
  
 los archivos de The.vsz que controlan nuevos tipos de proyecto con frecuencia contienen una entrada de RELATIVE\_PATH.  Esta ruta de acceso es ruta relativa a especificada en la clave de \\ProductDir entry of the project type in the following Setup:  
  
 HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\7.0Exp\\Setup  
  
 Por ejemplo, las plantillas de proyecto de Marcos empresarial agregan las entradas de Registro siguientes:  
  
 HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\7.0Exp\\Setup\\EF\\ProductDir \= C:\\Program Files\\Microsoft Visual Studio\\EnterpriseFrameworks \\  
  
 Eso significa si incluye una entrada de PROJECT\_TYPE\=EF en el archivo .vsz, el entorno buscan archivos .vsz en el directorio de ProductDir especificado previamente.  
  
## Vea también  
 [Lista de comprobación: Crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)   
 [Creación de instancias de proyecto mediante generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)