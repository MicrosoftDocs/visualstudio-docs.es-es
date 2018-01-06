---
title: Registrar plantillas de proyecto y elemento | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c064a6632741eba69a553be87fb8f829063b266b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="registering-project-and-item-templates"></a>Registro de proyecto y plantillas de elementos
Tipos de proyecto deben registrar los directorios donde se encuentran las plantillas de proyecto y elemento de proyecto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utiliza la información de registro asociada con los tipos de proyecto para determinar qué se debe mostrar en el **Agregar nuevo proyecto** y **Agregar nuevo elemento** cuadros de diálogo.  
  
 Para obtener más información acerca de las plantillas, consulte [Agregar proyecto y plantillas de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="registry-entries-for-projects"></a>Entradas del registro para los proyectos  
 Los ejemplos siguientes muestran las entradas del registro bajo HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*versión*>. En las tablas que lo acompaña explica los elementos usados en los ejemplos.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|nombre|Tipo|Descripción|  
|----------|----------|-----------------|  
|@|REG_SZ|Nombre predeterminado de los proyectos de este tipo.|  
|DisplayName|REG_SZ|Identificador de recurso del nombre que se recuperan desde el archivo DLL satélite registrados en paquetes.|  
|Package|REG_SZ|Id. de clase del paquete registrados en paquetes.|  
|ProjectTemplatesDir|REG_SZ|Ruta de acceso predeterminada de los archivos de plantilla de proyecto. Los archivos de plantilla de proyecto se muestran por la **nuevo proyecto** plantilla.|  
  
### <a name="registering-item-templates"></a>Plantillas de elementos del registro  
 Debe registrar el directorio donde se almacenan plantillas de elementos.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|nombre|Tipo|Descripción|  
|----------|----------|-----------------|  
|@|REG_SZ|Id. de recurso para plantillas de agregar elementos.|  
|TemplatesDir|REG_SZ|Ruta de acceso de los elementos de proyecto que se muestra en el cuadro de diálogo para la **Agregar nuevo elemento** asistente.|  
|TemplatesLocalizedSubDir|REG_SZ|Id. de recurso de una cadena que designa el subdirectorio de TemplatesDir que contiene plantillas de otros idiomas. Dado que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga el recurso de cadena de archivos DLL satélite si los tiene, cada archivo DLL satélite puede contener un nombre de subdirectorio localizados diferentes.|  
|SortPriority|REG_DWORD|Establecer SortPriority para controlar el orden en que las plantillas se muestran en la **Agregar nuevo elemento** cuadro de diálogo. Los valores mayores de SortPriority aparecen anteriormente en la lista de plantillas.|  
  
### <a name="registering-file-filters"></a>Registro de filtros de archivos  
 Si lo desea, puede registrar filtros que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utiliza cuando se le pida para nombres de archivo. Por ejemplo, el [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filtrar el el **archivos abiertos** cuadro de diálogo:  
  
 **Archivos de Visual C# (\*. cs,\*.resx,\*.settings,\*.xsd,\*.wsdl);\*. CS,\*.resx,\*.settings,\*.xsd,\*.wsdl)**  
  
 Para permitir el registro de varios filtros, cada filtro se registra en su propia subclave bajo HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*versión*> \Projects\\{} \< *ProjectGUID*>} \Filters\\<*subclave*>. El nombre de la subclave es arbitrario; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] omite el nombre de la subclave y usa solo sus valores.  
  
 Puede controlar los contextos en los que se usa un filtro estableciendo marcas, que se muestra en la tabla siguiente. Si un filtro no tiene todas las marcas, se enumerarán después los filtros comunes en el **Agregar elemento existente** cuadro de diálogo y el **archivos abiertos** cuadro de diálogo, pero no se usará en la **buscar en archivos**  cuadro de diálogo.  
  
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
  
|nombre|Tipo|Descripción|  
|----------|----------|-----------------|  
|CommonFindFilesFilter|REG_DWORD|Hace que el filtro de uno de los filtros comunes en el **buscar en archivos** cuadro de diálogo. Filtros comunes se muestran en la lista de filtros antes que los filtros no marcado como común.|  
|CommonOpenFilesFilter|REG_DWORD|Hace que el filtro de uno de los filtros comunes en el **archivos abiertos** cuadro de diálogo. Filtros comunes se muestran en la lista de filtros antes que los filtros no marcado como común.|  
|FindInFilesFilter|REG_DWORD|Muestra el filtro después de los filtros comunes en el **buscar en archivos** cuadro de diálogo.|  
|NotOpenFileFilter|REG_DWORD|Indica que el filtro no se utiliza en el **archivos abiertos** cuadro de diálogo.|  
|NotAddExistingItemFilter|REG_DWORD|Indica que el filtro no se utiliza en el **Agregar elemento existente** cuadro de diálogo.|  
|SortPriority|REG_DWORD|Establecer SortPriority para controlar el orden en que se muestran los filtros. Los valores mayores de SortPriority aparecen anteriormente en la lista de filtros.|  
  
## <a name="directory-structure"></a>Estructura de directorios  
 VSPackages puede colocar las carpetas y archivos de plantilla en cualquier sitio en un disco local o remoto, siempre y cuando se registra la ubicación a través de un entorno de desarrollo integrado (IDE). Sin embargo, para facilitar la organización, se recomienda la siguiente estructura de directorios bajo la ruta de instalación de su producto.  
  
 \Templates  
  
 \Projects (contiene las plantillas de proyecto)  
  
 \Applications  
  
 \Components  
  
 \ ...  
  
 \ProjectItems (que contiene los elementos de proyecto)  
  
 \Class  
  
 \Form  
  
 \Web página  
  
 \HelperFiles (que contiene los archivos utilizados en elementos de proyecto de varios archivos)  
  
 \WizardFiles  
  
## <a name="see-also"></a>Vea también  
 [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Asistentes](../../extensibility/internals/wizards.md)   
 [Localizar aplicaciones](../../ide/localizing-applications.md)   
 [CATID para los objetos que se utilizan normalmente para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)