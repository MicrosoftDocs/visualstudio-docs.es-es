---
title: Registrando plantillas de proyecto y elemento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a06e7a292d960e675ad4b0de97499557542fef1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185836"
---
# <a name="registering-project-and-item-templates"></a>Registro de plantillas para proyectos y elementos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Los tipos de proyecto deben registrar los directorios donde se encuentran las plantillas de proyecto y de elemento de proyecto. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usa la información de registro asociada a los tipos de proyecto para determinar lo que se va a mostrar en los cuadros de diálogo **Agregar nuevo proyecto** y **Agregar nuevo elemento** .  
  
 Para obtener más información acerca de las plantillas, vea [agregar plantillas de proyecto y de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="registry-entries-for-projects"></a>Entradas del registro para proyectos  
 En los ejemplos siguientes se muestran las entradas del registro en HKEY_LOCAL_MACHINE versión de \software\microsoft\visualstudio \\ < *Version*>. En las tablas adjuntas se explican los elementos que se usan en los ejemplos.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|Nombre|Tipo|Descripción|  
|----------|----------|-----------------|  
|@|REG_SZ|Nombre predeterminado de los proyectos de este tipo.|  
|DisplayName|REG_SZ|IDENTIFICADOR de recurso del nombre que se va a recuperar de la DLL satélite registrada en packages.|  
|Paquete|REG_SZ|IDENTIFICADOR de clase del paquete registrado en paquetes.|  
|ProjectTemplatesDir|REG_SZ|Ruta de acceso predeterminada de los archivos de plantilla de proyecto. La nueva plantilla de **proyecto** muestra los archivos de plantilla de proyecto.|  
  
### <a name="registering-item-templates"></a>Registrar plantillas de elementos  
 Debe registrar el directorio donde se almacenan las plantillas de elementos.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|Nombre|Tipo|Descripción|  
|----------|----------|-----------------|  
|@|REG_SZ|IDENTIFICADOR de recurso para agregar plantillas de elementos.|  
|TemplatesDir|REG_SZ|Ruta de acceso de los elementos de proyecto mostrados en el cuadro de diálogo para el Asistente para **Agregar nuevo elemento** .|  
|TemplatesLocalizedSubDir|REG_SZ|IDENTIFICADOR de recurso de una cadena que nombra el subdirectorio de TemplatesDir que contiene las plantillas localizadas. Dado [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que carga el recurso de cadena desde archivos dll satélite, si los tiene, cada archivo dll satélite puede contener un nombre de subdirectorio localizado diferente.|  
|SortPriority|REG_DWORD|Establezca SortPriority para controlar el orden en el que se muestran las plantillas en el cuadro de diálogo **Agregar nuevo elemento** . Los valores de SortPriority más grandes aparecen anteriormente en la lista de plantillas.|  
  
### <a name="registering-file-filters"></a>Registrando filtros de archivo  
 Opcionalmente, puede registrar filtros que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] use cuando pida nombres de archivo. Por ejemplo, el [!INCLUDE[csprcs](../../includes/csprcs-md.md)] filtro para el cuadro de diálogo **Abrir archivo** es:  
  
 **Archivos de Visual C# ( \* . CS, \* . resx, \* . Settings, \* . xsd, \* . WSDL); \* . CS, \* . resx, \* . Settings, \* . xsd, \* . WSDL)**  
  
 Para admitir el registro de varios filtros, cada filtro se registra en su propia subclave en HKEY_LOCAL_MACHINE versión de \software\microsoft\visualstudio \\ < *Version*> \projects \\ { \<*ProjectGUID*> } \Filters \\ < *subclave*>. El nombre de la subclave es arbitrario; [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] omite el nombre de la subclave y usa solo sus valores.  
  
 Puede controlar los contextos en los que se usa un filtro mediante el establecimiento de marcas, que se muestra en la tabla siguiente. Si un filtro no tiene ninguna marca establecida, se mostrará después de los filtros comunes en el cuadro de diálogo **Agregar elemento existente** y el cuadro de diálogo **Abrir archivo** , pero no se utilizará en el cuadro de diálogo **Buscar en archivos** .  
  
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
|----------|----------|-----------------|  
|CommonFindFilesFilter|REG_DWORD|Hace que el filtro sea uno de los filtros comunes del cuadro de diálogo **Buscar en archivos** . Los filtros comunes se muestran en la lista de filtros antes de que los filtros no estén marcados como comunes.|  
|CommonOpenFilesFilter|REG_DWORD|Hace que el filtro sea uno de los filtros comunes del cuadro de diálogo **Abrir archivo** . Los filtros comunes se muestran en la lista de filtros antes de que los filtros no estén marcados como comunes.|  
|FindInFilesFilter|REG_DWORD|Muestra el filtro después de los filtros comunes en el cuadro de diálogo **Buscar en archivos** .|  
|NotOpenFileFilter|REG_DWORD|Indica que el filtro no se utiliza en el cuadro de diálogo **Abrir archivo** .|  
|NotAddExistingItemFilter|REG_DWORD|Indica que el filtro no se utiliza en el cuadro de diálogo **Agregar elemento existente** .|  
|SortPriority|REG_DWORD|Establezca SortPriority para controlar el orden en que se muestran los filtros. Los valores de SortPriority más grandes aparecen anteriormente en la lista de filtros.|  
  
## <a name="directory-structure"></a>Estructura de directorios  
 Los VSPackages pueden colocar archivos de plantilla y carpetas en cualquier parte de un disco local o remoto, siempre y cuando la ubicación se registre a través del entorno de desarrollo integrado (IDE). Sin embargo, para facilitar la organización, se recomienda la siguiente estructura de directorios en la ruta de instalación del producto.  
  
 \Plantillas  
  
 \Projects (contiene las plantillas de proyecto)  
  
 \Applications  
  
 \Components  
  
 \ ...  
  
 \ProjectItems (contiene los elementos de proyecto)  
  
 \Class  
  
 \Form  
  
 Página \servicio  
  
 \HelperFiles (contiene los archivos usados en los elementos de proyecto de varios archivos)  
  
 \WizardFiles  
  
## <a name="see-also"></a>Consulte también  
 [Agregar plantillas de proyecto y de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Asistentes](../../extensibility/internals/wizards.md)   
 [Localizar aplicaciones](../../ide/localizing-applications.md)   
 [CATID para los objetos que se usan normalmente para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
