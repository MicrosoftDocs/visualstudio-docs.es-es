---
title: Registrando un tipo de proyecto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 63e0140b752adda02aba6126580ec08ee1f7536a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843362"
---
# <a name="registering-a-project-type"></a>Registro de un tipo de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Al crear un nuevo tipo de proyecto, debe crear entradas del registro que habiliten [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para reconocer y trabajar con el tipo de proyecto. Normalmente, estas entradas del registro se crean mediante un archivo de script de registro (. RGS).  
  
 En el ejemplo siguiente, las instrucciones del registro proporcionan las rutas de acceso predeterminadas y los datos, si procede, seguidos de una tabla que contiene entradas del script del registro para cada instrucción. Las tablas proporcionan las entradas de script e información adicional sobre las instrucciones.  
  
> [!NOTE]
> La siguiente información del registro pretende ser un ejemplo del tipo y los propósitos de las entradas de los scripts del registro que se van a escribir para registrar el tipo de proyecto. Las entradas reales y sus usos pueden variar en función de los requisitos específicos de su tipo de proyecto. Debe revisar los ejemplos disponibles para encontrar uno que se parezca al tipo de proyecto que está desarrollando y, a continuación, revisar el script del registro para ese ejemplo.  
  
 Los ejemplos siguientes son de HKEY_CLASSES_ROOT.  
  
## <a name="example"></a>Ejemplo  
  
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
  
|Nombre|Tipo|data|Descripción|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrjFile`|Nombre y descripción de los archivos de tipo de proyecto que tienen la extensión. figp.|  
|`Content Type`|REG_SZ|`Text/plain`|Tipo de contenido de los archivos de proyecto.|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|Icono predeterminado usado para el proyecto de este tipo. La instrucción% MODULE% se completa en el registro en la ubicación predeterminada del archivo DLL de tipo de proyecto.|  
|`@`|REG_SZ|`&Open in Visual Studio`|Aplicación predeterminada en la que se abrirá este tipo de proyecto.|  
|`@`|REG_SZ|`devenv.exe "%1"`|Comando predeterminado que se ejecutará cuando se abra un proyecto de este tipo.|  
  
 Los ejemplos siguientes son de HKEY_LOCAL_MACHINE y se encuentran en el registro con la clave [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].  
  
## <a name="example"></a>Ejemplo  
  
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
  
|Nombre|Tipo|data|Descripción|  
|----------|----------|----------|-----------------|  
|`@` (valor predeterminado)|REG_SZ|`FigPrj Project VSPackage`|Nombre traducible de este VSPackage registrado (tipo de proyecto).|  
|`InprocServer32`|REG_SZ|`%MODULE%`|Ruta de acceso del archivo DLL de tipo de proyecto. El IDE carga este archivo DLL y pasa el CLSID de VSPackage a `DllGetClassObject` para <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> crear el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> objeto.|  
|`CompanyName`|REG_SZ|`Microsoft`|Nombre de la compañía que desarrolló el tipo de proyecto.|  
|`ProductName`|REG_SZ|`Figure Project Sample`|Nombre del tipo de proyecto.|  
|`ProductVersion`|REG_SZ|`9.0`|Número de versión de la versión del tipo de proyecto.|  
|`MinEdition`|REG_SZ|`professional`|Edición del VSPackage que se va a registrar.|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|La clave de carga del paquete para el VSPackage del proyecto. La clave se valida cuando se carga un proyecto después de que se haya iniciado el entorno.|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Nombre del archivo DLL satélite que contiene recursos localizados para el tipo de proyecto.|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Ruta de acceso del archivo DLL satélite.|  
|`FigProjectsEvents`|REG_SZ|Vea la instrucción para obtener valor.|Determina la cadena de texto devuelta para este evento de automatización.|  
|`FigProjectItemsEvents`|REG_SZ|Vea la instrucción para obtener valor.|Determina la cadena de texto devuelta para este evento de automatización.|  
  
 Todos los ejemplos siguientes se encuentran en el registro con la clave [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Ejemplo  
  
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
  
|Nombre|Tipo|data|Descripción|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrj Project`|Nombre predeterminado de los proyectos de este tipo.|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|IDENTIFICADOR de recurso del nombre que se va a recuperar de la DLL satélite registrada en packages.|  
|`Package`|REG_SZ|`%CLSID_Package%`|IDENTIFICADOR de clase del VSPackage registrado en paquetes.|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Ruta de acceso predeterminada de los archivos de plantilla de proyecto. Estos son los archivos que muestra la nueva plantilla de proyecto.|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Ruta de acceso predeterminada de los archivos de plantilla de elemento de proyecto. Estos son los archivos que muestra la plantilla agregar nuevo elemento.|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Permite al IDE implementar el cuadro de diálogo **abrir** .|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|Lo utiliza el IDE para determinar si el proyecto que se está abriendo se controla mediante este tipo de proyecto (generador de proyectos). El formato de más de una entrada es una lista delimitada por punto y coma. Por ejemplo, "vdproj; VDP".|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|Lo usa el IDE como la extensión de nombre de archivo predeterminada para la operación Guardar como.|  
|`Filter Settings`|REG_DWORD|Varios, vea instrucciones y comentarios en la tabla siguiente.|Esta configuración se usa para establecer los distintos filtros para mostrar archivos en los cuadros de diálogo de la interfaz de usuario.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|IDENTIFICADOR de recurso para agregar plantillas de elementos.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Ruta de acceso de los elementos de proyecto mostrados en el cuadro de diálogo para la plantilla **Agregar nuevo elemento** .|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Determina el criterio de ordenación en el nodo de árbol de los archivos que se muestran en el cuadro de diálogo **Agregar nuevo elemento** .|  
  
 En la tabla siguiente se muestran las opciones de filtros disponibles en el segmento de código anterior.  
  
|Opción de filtro|Descripción|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|Indica que el filtro es uno de los filtros comunes del cuadro de diálogo **Buscar en archivos** . Los filtros comunes se enumeran en la lista de filtros antes de que los filtros no estén marcados como comunes.|  
|`CommonOpenFilesFilter`|Indica que el filtro es uno de los filtros comunes del cuadro de diálogo **Abrir archivo** . Los filtros comunes se enumeran en la lista de filtros antes de que los filtros no estén marcados como comunes.|  
|`FindInFilesFilter`|Indica que el filtro será uno de los filtros del cuadro de diálogo **Buscar en archivos** y se mostrará después de los filtros comunes.|  
|`NotOpenFileFilter`|Indica que el filtro no se utilizará en el cuadro de diálogo **Abrir archivo** .|  
|`NotAddExistingItemFilter`|Indica que el filtro no se utilizará en el cuadro de diálogo Agregar **elemento existente** .|  
  
 De forma predeterminada, si un filtro no tiene uno o varios de estos marcadores establecidos, el filtro se usa en el cuadro de diálogo **Agregar elemento existente** y en el cuadro de diálogo **Abrir archivo** después de que aparezcan los filtros comunes. El filtro no se utiliza en el cuadro de diálogo **Buscar en archivos** .  
  
 Todos los ejemplos siguientes se encuentran en el registro con la clave [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Ejemplo  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Nombre|Tipo|data|Descripción|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|IDENTIFICADOR de recurso para las nuevas plantillas de proyecto.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Ruta de acceso predeterminada para los proyectos del tipo de proyecto registrado.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Establece el criterio de ordenación de los proyectos mostrados en el cuadro de diálogo Asistente para nuevos proyectos.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indica que los proyectos de este tipo solo se muestran en el cuadro de diálogo nuevo proyecto.|  
  
 Todos los ejemplos siguientes se encuentran en el registro con la clave [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Ejemplo  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Nombre|Tipo|data|Descripción|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|Ninguno|Valor predeterminado que indica que las siguientes entradas son para las entradas de proyectos de archivos varios.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Valor de identificador de recurso para los archivos de plantilla agregar nuevos elementos.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Ruta de acceso predeterminada de los elementos que se mostrarán en el cuadro de diálogo **Agregar nuevo elemento** .|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Establece el criterio de ordenación que se va a mostrar en el nodo de árbol del cuadro de diálogo **Agregar nuevo elemento** .|  
  
 El siguiente ejemplo se encuentra en el registro con la clave [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].  
  
## <a name="example"></a>Ejemplo  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 La entrada de menú apunta al IDE al recurso que se usa para recuperar la información de menú. Cuando estos datos se hayan combinado en la base de datos de menú, se agregará la misma clave en la sección MenusMerged del registro. El VSPackage no debe modificar nada en la sección MenusMerged directamente. En el campo de datos de la tabla siguiente, hay tres campos separados por comas. El primer campo identifica una ruta de acceso completa de un archivo de recursos de menú:  
  
- Si se omite el primer campo, el recurso de menú se carga desde el archivo DLL satélite identificado por el GUID del VSPackage.  
  
  El segundo campo identifica un identificador de recurso de menú del tipo CTMENU:  
  
- Si se especifica el identificador de recurso y la ruta de acceso del archivo se proporciona mediante el primer parámetro, se carga un recurso de menú desde la ruta de acceso completa del archivo.  
  
- Si se proporciona el identificador de recurso, pero la ruta de acceso del archivo no es, el recurso de menú se carga desde el archivo DLL satélite.  
  
- Si se proporciona la ruta de acceso completa al archivo y se omite el identificador de recurso, se espera que el archivo que se va a cargar sea un archivo CTO.  
  
  El último campo identifica el número de versión del recurso CTMENU. Puede volver a combinar el menú cambiando el número de versión.  
  
|Nombre|Tipo|data|Descripción|  
|----------|----------|----------|-----------------|  
|% CLSID_Package%|REG_SZ|`,1000,1`|Recurso para recuperar la información de menú.|  
  
 Todos los ejemplos siguientes se encuentran en el registro con la clave [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Nombre|Tipo|data|Descripción|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Valor de ID. de recurso del proyecto de ilustraciones nuevas plantillas de proyecto.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Ruta de acceso predeterminada del nuevo directorio de proyectos. Los elementos de este directorio se mostrarán en el cuadro de diálogo **Asistente para nuevo proyecto** .|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Establece el orden en el que los proyectos se mostrarán en el nodo de árbol del cuadro de diálogo **nuevo proyecto** .|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indica que los proyectos de este tipo solo se muestran en el cuadro de diálogo **nuevo proyecto** .|  
  
 El siguiente ejemplo se encuentra en el registro con la clave [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|Nombre|Tipo|data|Descripción|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|IDENTIFICADOR de clase del VSPackage registrado.|  
|`UseInterface`|REG_DWORD|`1`|1 indica que la interfaz de usuario se utilizará para interactuar con este proyecto. 0 indica que no hay ninguna interfaz de interfaz de usuario.|  
  
 Los archivos. vsz que controlan los nuevos tipos de proyecto suelen contener una entrada RELATIVE_PATH. Esta ruta de acceso es relativa a la ruta de acceso especificada en la entrada \ProductDir del tipo de proyecto en la siguiente clave de configuración:  
  
 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 Por ejemplo, las plantillas de proyecto de Enterprise Frameworks agregan las siguientes entradas del registro:  
  
 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Archivos de Programa\microsoft visual Studio\EnterpriseFrameworks\  
  
 Esto significa que si incluye una entrada PROJECT_TYPE = EF en el archivo. vsz, el entorno busca los archivos. vsz en el directorio ProductDir especificado anteriormente.  
  
## <a name="see-also"></a>Consulte también  
 [Lista de comprobación: crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)   
 [Creación de instancias de proyecto mediante generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
