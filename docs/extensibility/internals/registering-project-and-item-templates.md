---
title: "Registro de proyecto y plantillas de elementos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proyectos [Visual Studio SDK], agregar elementos"
  - "registro, cuadro de diálogo Agregar nuevo elemento"
  - "Cuadro de diálogo Agregar nuevo elemento"
  - "Agregar cuadro de diálogo nuevo proyecto"
  - "registro, cuadro de diálogo Agregar nuevo proyecto"
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# Registro de proyecto y plantillas de elementos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Tipos de proyecto deben registrar los directorios donde se encuentran las plantillas de proyecto y elemento de proyecto.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utiliza la información de registro asociada con los tipos de proyecto para determinar qué se debe mostrar en el **Agregar nuevo proyecto** y **Agregar nuevo elemento** cuadros de diálogo.  
  
 Para obtener más información acerca de las plantillas, consulte [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## Entradas del registro para proyectos  
 Los siguientes ejemplos muestran entradas del registro en HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\ \<*versión*\>. Las tablas que lo acompaña explican los elementos usados en los ejemplos.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|Nombre|Tipo|Descripción|  
|------------|----------|-----------------|  
|@|REG\_SZ|Nombre predeterminado de los proyectos de este tipo.|  
|DisplayName|REG\_SZ|Identificador de recurso del nombre que recuperarse desde el archivo DLL satélite registrados en paquetes.|  
|Paquete|REG\_SZ|Id. de clase del paquete se registra en paquetes.|  
|ProjectTemplatesDir|REG\_SZ|Ruta de acceso predeterminada de los archivos de plantilla de proyecto. Se muestran los archivos de plantilla de proyecto por el **nuevo proyecto** plantilla.|  
  
### Registrar plantillas de elementos  
 Debe registrar el directorio donde se almacenan las plantillas de elemento.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|Nombre|Tipo|Descripción|  
|------------|----------|-----------------|  
|@|REG\_SZ|Id. de recurso para las plantillas Agregar elemento.|  
|TemplatesDir|REG\_SZ|Ruta de acceso de los elementos de proyecto que se muestra en el cuadro de diálogo para el **Agregar nuevo elemento** asistente.|  
|TemplatesLocalizedSubDir|REG\_SZ|Identificador de recurso de cadena que denomina el subdirectorio de TemplatesDir que contiene plantillas de otros idiomas. Porque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga el recurso de cadena de archivos DLL satélite si los tiene, cada archivo DLL satélite puede contener un nombre de subdirectorio localizadas diferentes.|  
|SortPriority|REG\_DWORD|Establecer SortPriority para controlar el orden en que las plantillas se muestran en el **Agregar nuevo elemento** cuadro de diálogo. Los valores mayores de SortPriority aparecen anteriormente en la lista de plantillas.|  
  
### Filtros de archivos de registro  
 Si lo desea, puede registrar filtros que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utiliza cuando se le pida para nombres de archivo. Por ejemplo, el [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filtrar el el **Abrir archivo** cuadro de diálogo:  
  
 **Archivos Visual C\# \(\*.cs, \*.resx, \*.settings, \*.xsd, \*.wsdl\); \*.cs, \*.resx, \*.settings, \*.xsd, \*.wsdl\)**  
  
 Para permitir el registro de varios filtros, cada filtro se registra en su propia subclave bajo HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\ \<*versión*\> \\Projects\\ {\<*ProjectGUID*\>} \\Filters\\ \<*subclave*\>. El nombre de la subclave es arbitrario; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] omite el nombre de la subclave y utiliza sólo sus valores.  
  
 Puede controlar los contextos en los que se usa un filtro estableciendo marcas, que se muestra en la tabla siguiente. Si un filtro no tiene ningún indicador, se mostrará después de los filtros comunes en el **Agregar elemento existente** cuadro de diálogo y el **Abrir archivo** cuadro de diálogo, pero no se usará en el **Buscar en archivos** cuadro de diálogo.  
  
```  
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]  
@="#3"  
"CommonOpenFilesFilter"=dword:00000000  
"CommonFindFilesFilter"=dword:00000000  
"FindInFilesFilter"=dword:00000000  
"NotOpenFileFilter"=dword:00000000  
"NotAddExistingItemFilter"=dword:00000000  
"SortPriority"=dword:00000064  
```  
  
|Nombre|Tipo|Descripción|  
|------------|----------|-----------------|  
|CommonFindFilesFilter|REG\_DWORD|Hace que el filtro de uno de los filtros comunes en el **Buscar en archivos** cuadro de diálogo. Filtros comunes se enumeran en la lista de filtros antes que los filtros no marcado como común.|  
|CommonOpenFilesFilter|REG\_DWORD|Hace que el filtro de uno de los filtros comunes en el **Abrir archivo** cuadro de diálogo. Filtros comunes se enumeran en la lista de filtros antes que los filtros no marcado como común.|  
|FindInFilesFilter|REG\_DWORD|Muestra el filtro después de los filtros comunes en el **Buscar en archivos** cuadro de diálogo.|  
|NotOpenFileFilter|REG\_DWORD|Indica que el filtro no se utiliza en el **Abrir archivo** cuadro de diálogo.|  
|NotAddExistingItemFilter|REG\_DWORD|Indica que el filtro no se utiliza en el **Agregar elemento existente** cuadro de diálogo.|  
|SortPriority|REG\_DWORD|Establecer SortPriority para controlar el orden en que se muestran los filtros. Los valores mayores de SortPriority aparecen anteriormente en la lista de filtros.|  
  
## Estructura de directorios  
 VSPackages puede poner las carpetas y archivos de plantilla en cualquier lugar en un disco local o remoto, siempre y cuando se registra la ubicación a través de un entorno de desarrollo integrado \(IDE\). Sin embargo, para facilitar la organización, se recomienda la siguiente estructura de directorios bajo la ruta de instalación de su producto.  
  
 \\Templates  
  
 \\Projects \(contiene las plantillas de proyecto\)  
  
 \\Applications  
  
 \\Components  
  
 \\ ...  
  
 \\ProjectItems \(contiene los elementos de proyecto\)  
  
 \\Class  
  
 \\Form  
  
 \\Web página  
  
 \\HelperFiles \(contiene los archivos utilizados en los elementos de proyecto de varios archivos\)  
  
 \\WizardFiles  
  
## Vea también  
 [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Asistentes](../../extensibility/internals/wizards.md)   
 [Localizar aplicaciones](../../ide/localizing-applications.md)   
 [CATID para los objetos que se utilizan normalmente para extender proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)