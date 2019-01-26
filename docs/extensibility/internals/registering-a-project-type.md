---
title: Registrar un tipo de proyecto | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b1413acafd4358d4b29435a0cd62edd5a8ce22e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940835"
---
# <a name="registering-a-project-type"></a>Registro de un tipo de proyecto
Cuando se crea un nuevo tipo de proyecto, debe crear las entradas del registro que permiten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para reconocer y trabajar con el tipo de proyecto. Normalmente crea estas entradas del registro mediante un archivo de registro (.rgs) de la secuencia de comandos.  
  
 En el ejemplo siguiente, las instrucciones del registro proporcionan rutas de acceso predeterminadas y datos en su caso, seguido de una tabla que contiene las entradas de la secuencia de comandos del registro para cada instrucción. Las tablas proporcionan las entradas de secuencia de comandos y obtener información adicional acerca de las instrucciones.  
  
> [!NOTE]
>  La siguiente información del registro debe ser un ejemplo del tipo y con fines de las entradas de las secuencias de comandos del registro que va a escribir para registrar el tipo de proyecto. Las entradas reales y sus usos pueden variar en función de los requisitos específicos del tipo de proyecto. Debe revisar los ejemplos disponibles para encontrar uno que refleje el tipo de proyecto que está desarrollando y, a continuación, revise el script del registro para ese ejemplo.  
  
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
  
|nombre|Tipo|Datos|Descripción|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrjFile`|Nombre y descripción de los archivos de tipo de proyecto que tienen la extensión .figp.|  
|`Content Type`|REG_SZ|`Text/plain`|Tipo de contenido para los archivos del proyecto.|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|Icono de predeterminado usado para el proyecto de este tipo. Se ha completado el % MODULE (instrucción) % en el registro en la ubicación predeterminada del tipo de proyecto DLL.|  
|`@`|REG_SZ|`&Open in Visual Studio`|En el que este tipo de proyecto se abrirá la aplicación de predeterminada.|  
|`@`|REG_SZ|`devenv.exe "%1"`|Comando predeterminado que se va a ejecutar cuando se abre un proyecto de este tipo.|  
  
 Los ejemplos siguientes provienen de HKEY_LOCAL_MACHINE y se encuentran en el registro bajo la clave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].  
  
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
  
|nombre|Tipo|Datos|Descripción|  
|----------|----------|----------|-----------------|  
|`@` (Valor predeterminado)|REG_SZ|`FigPrj Project VSPackage`|Nombre localizable del esto había registrado VSPackage (tipo de proyecto).|  
|`InprocServer32`|REG_SZ|`%MODULE%`|Ruta de acceso del tipo de proyecto DLL. El IDE carga este archivo DLL y pasa el CLSID VSPackage para `DllGetClassObject` obtener <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> para construir el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> objeto.|  
|`CompanyName`|REG_SZ|`Microsoft`|Nombre de la compañía que desarrolló el tipo de proyecto.|  
|`ProductName`|REG_SZ|`Figure Project Sample`|Nombre del tipo de proyecto.|  
|`ProductVersion`|REG_SZ|`9.0`|Liberar el número de versión del tipo de proyecto.|  
|`MinEdition`|REG_SZ|`professional`|Edición del VSPackage que se está registrando.|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|El paquete se carga la clave para el proyecto de VSPackage. La clave se valida cuando se carga un proyecto después de que se ha iniciado el entorno.|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Nombre de archivo del archivo DLL que contiene recursos localizados para el tipo de proyecto de satélite.|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Ruta de acceso del archivo DLL satélite.|  
|`FigProjectsEvents`|REG_SZ|Vea la declaración de valor.|Determina la cadena de texto devuelta para este evento de automatización.|  
|`FigProjectItemsEvents`|REG_SZ|Vea la declaración de valor.|Determina la cadena de texto devuelta para este evento de automatización.|  
  
 Los siguientes ejemplos se encuentran en el registro bajo la clave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
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
  
|nombre|Tipo|Datos|Descripción|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrj Project`|Nombre predeterminado de los proyectos de este tipo.|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Id. de recurso del nombre que deben recuperarse de la DLL satélite registrados en los paquetes.|  
|`Package`|REG_SZ|`%CLSID_Package%`|Id. de clase de VSPackage registrados en los paquetes.|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Ruta de acceso predeterminada de los archivos de plantilla de proyecto. Estos son los archivos mostrados por la plantilla de proyecto nuevo.|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Ruta de acceso predeterminada de los archivos de plantilla de elemento de proyecto. Estos son los archivos mostrados por la plantilla de agregar nuevo elemento.|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Permite que el IDE implementar la **abierto** cuadro de diálogo.|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|El IDE lo utiliza para determinar si el proyecto que se está abriendo está controlado por este tipo de proyecto (generador de proyectos). El formato de más de una entrada es una lista delimitada por puntos y. Por ejemplo "vdproj; vdp".|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|Usar el IDE como la extensión de nombre de archivo predeterminado para la operación Guardar como.|  
|`Filter Settings`|REG_DWORD|Varios, vea las instrucciones y comentarios en la tabla siguiente.|Estos valores se utilizan para establecer los distintos filtros para mostrar los archivos en los cuadros de diálogo de interfaz de usuario.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Identificador de recurso para las plantillas Agregar elemento.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Ruta de acceso de los elementos de proyecto que se muestra en el cuadro de diálogo para la **Agregar nuevo elemento** plantilla.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Determina el criterio de ordenación en el nodo de árbol de archivos que se muestran en el **Agregar nuevo elemento** cuadro de diálogo.|  
  
 En la siguiente tabla muestra las opciones de los filtros disponibles en el segmento de código anterior.  
  
|Opción de filtro|Descripción|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|Indica que el filtro es uno de los filtros comunes en el **buscar en archivos** cuadro de diálogo. Los filtros comunes se muestran en la lista de filtros antes que los filtros no marcados como común.|  
|`CommonOpenFilesFilter`|Indica que el filtro es uno de los filtros comunes en el **abrir archivo** cuadro de diálogo. Los filtros comunes se muestran en la lista de filtros antes que los filtros no marcados como común.|  
|`FindInFilesFilter`|Indica que el filtro será uno de los filtros en la **buscar en archivos** diálogo cuadro y se mostrará después de los filtros comunes.|  
|`NotOpenFileFilter`|Indica que el filtro no se usará en el **abrir archivo** cuadro de diálogo.|  
|`NotAddExistingItemFilter`|Indica que el filtro no se usará en el complemento **elemento existente** cuadro de diálogo.|  
  
 De forma predeterminada, si un filtro no tiene uno o varios de estos marcadores de conjunto, el filtro se usa en el **Agregar elemento existente** cuadro de diálogo y el **abrir archivo** cuadro de diálogo después de que se muestran los filtros comunes. El filtro no se usa en el **buscar en archivos** cuadro de diálogo.  
  
 Los siguientes ejemplos se encuentran en el registro bajo la clave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Ejemplo  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|nombre|Tipo|Datos|Descripción|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Identificador de recurso para las plantillas de proyecto nuevo.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Ruta de acceso para los proyectos del tipo de proyecto registrados de forma predeterminada.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Conjuntos de criterio de ordenación de los proyectos que se muestra en el cuadro de diálogo del Asistente para nuevos proyectos.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indica que se muestran los proyectos de este tipo solo en el cuadro de diálogo nuevo proyecto.|  
  
 Los siguientes ejemplos se encuentran en el registro bajo la clave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
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
  
|nombre|Tipo|Datos|Descripción|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|Ninguna|Valor predeterminado que indica que las entradas siguientes son para las entradas de los proyectos de archivos varios.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Valor de identificador de recurso para los archivos de plantilla de agregar nuevos elementos.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Ruta de acceso predeterminada de los elementos que se mostrará en el **Agregar nuevo elemento** cuadro de diálogo.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Establece el criterio de ordenación para mostrar en el nodo de árbol de la **Agregar nuevo elemento** cuadro de diálogo.|  
  
 En el siguiente ejemplo se encuentra en el registro bajo la clave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].  
  
## <a name="example"></a>Ejemplo  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 La entrada de menú señala el IDE para el recurso utilizado para recuperar la información de menú. Cuando estos datos se ha combinado con la base de datos de menú, se agregará la misma clave en la sección MenusMerged del registro. El VSPackage no debe modificar nada en la sección MenusMerged directamente. En el campo de datos en la tabla siguiente, hay tres por comas de campos separados por. El primer campo identifica una ruta de acceso completa de un archivo de recursos de menú:  
  
- Si se omite el primer campo, el recurso de menú se carga desde el archivo DLL identificado por el GUID del VSPackage satélite.  
  
  El segundo campo identifica un identificador de recurso de menú del tipo CTMENU:  
  
- Si se especifica el identificador de recurso y la ruta de acceso de archivo proporcionado por el primer parámetro, un recurso de menú se carga desde la ruta de acceso completa al archivo.  
  
- Si se proporciona el identificador de recurso, pero no lo es la ruta de acceso de archivo, el recurso de menú se carga desde el archivo DLL satélite.  
  
- Si se proporciona la ruta de acceso completa y el identificador de recurso se omite, se espera que se cargue el archivo sea un archivo de director de tecnología.  
  
  El último campo identifica el número de versión para el recurso CTMENU. Puede combinar el menú nuevo, cambie el número de versión.  
  
|nombre|Tipo|Datos|Descripción|  
|----------|----------|----------|-----------------|  
|%CLSID_Package%|REG_SZ|`,1000,1`|El recurso para recuperar la información de menú.|  
  
 Los siguientes ejemplos se encuentran en el registro bajo la clave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|nombre|Tipo|Datos|Descripción|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Valor de identificador de recurso para las plantillas de proyecto nuevo proyecto de figuras.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Ruta de acceso predeterminada del directorio de los proyectos nuevos. Los elementos de este directorio se mostrará en el **Asistente para nuevo proyecto** cuadro de diálogo.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Establece el orden en que los proyectos se mostrará en el nodo de árbol de la **nuevo proyecto** cuadro de diálogo.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indica que los proyectos de este tipo se muestran solo en el **nuevo proyecto** cuadro de diálogo.|  
  
 En el siguiente ejemplo se encuentra en el registro bajo la clave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|nombre|Tipo|Datos|Descripción|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|Id. de clase de VSPackage registrado.|  
|`UseInterface`|REG_DWORD|`1`|1 indica que se utilizará la interfaz de usuario para interactuar con este proyecto. 0 indica que no hay ninguna interfaz de la interfaz de usuario.|  
  
 Archivos.vsz que controlan los nuevos tipos de proyecto con frecuencia contienen una entrada RELATIVE_PATH. Esta ruta de acceso es relativa a la ruta de acceso especificada en la entrada \ProductDir del tipo de proyecto en la siguiente clave del programa de instalación:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 Por ejemplo, las plantillas de proyecto de Enterprise Frameworks agregue las siguientes entradas del registro:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\  
  
 Esto significa que si incluir un PROJECT_TYPE = entrada EF en el archivo .vsz, la encuentra entorno su .vsz archivos en el directorio de ProductDir especificado anteriormente.  
  
## <a name="see-also"></a>Vea también  
 [Lista de comprobación: Creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)   
 [Creación de instancias de proyecto mediante generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)