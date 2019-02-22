---
title: Registro de plantillas de proyecto y elemento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec6f2a8b25438d7909f47087b8f6a80e595e7cba
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630527"
---
# <a name="registering-project-and-item-templates"></a>Registro de plantillas para proyectos y elementos
Tipos de proyecto deben registrar los directorios donde se encuentran sus plantillas de proyecto y elemento de proyecto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa la información de registro asociada con los tipos de proyecto para determinar qué se debe mostrar en el **Agregar nuevo proyecto** y **Agregar nuevo elemento** cuadros de diálogo.

 Para obtener más información acerca de las plantillas, consulte [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md).

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
|DisplayName|REG_SZ|Id. de recurso del nombre que deben recuperarse de la DLL satélite registrados en los paquetes.|
|Paquete|REG_SZ|Id. de clase del paquete se registra en los paquetes.|
|ProjectTemplatesDir|REG_SZ|Ruta de acceso predeterminada de los archivos de plantilla de proyecto. Los archivos de plantilla de proyecto se muestran mediante el **nuevo proyecto** plantilla.|

### <a name="registering-item-templates"></a>Registrar las plantillas de elemento
 Debe registrar el directorio donde se almacenan las plantillas de elemento.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```


| nombre | Tipo | Descripción |
|--------------------------|-----------| - |
| @ | REG_SZ | Identificador de recurso para las plantillas Agregar elemento. |
| TemplatesDir | REG_SZ | Ruta de acceso de los elementos de proyecto que se muestra en el cuadro de diálogo para la **Agregar nuevo elemento** asistente. |
| TemplatesLocalizedSubDir | REG_SZ | Identificador de recurso de cadena que designa el subdirectorio de TemplatesDir que contiene las plantillas localizadas. Dado que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga el recurso de cadena de archivos DLL satélite si los tiene, cada archivo DLL satélite puede contener un nombre de subdirectorio localizados diferentes. |
| SortPriority | REG_DWORD | Establecer SortPriority para controlar el orden en que se muestran las plantillas en el **Agregar nuevo elemento** cuadro de diálogo. Los valores mayores de SortPriority aparecen anteriormente en la lista de plantillas. |

### <a name="registering-file-filters"></a>Filtros de archivos de registro
 Si lo desea, puede registrar los filtros que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa cuando se le pida para los nombres de archivo. Por ejemplo, el [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filtrar el **abrir archivo** cuadro de diálogo:

 **Archivos de Visual C# (\*. cs,\*.resx,\*.settings,\*.xsd,\*.wsdl);\*. CS,\*.resx,\*.settings,\*.xsd,\*.wsdl)**

 Para admitir el registro de varios filtros, cada filtro se registra en su propia subclave bajo HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*versión*> \Projects\\{} \< *ProjectGUID*>} \Filters\\<*subclave*>. El nombre de la subclave es arbitrario; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] omite el nombre de la subclave y usa sólo en sus valores.

 Puede controlar los contextos en los que se usa un filtro estableciendo marcas, que se muestra en la tabla siguiente. Si un filtro no tiene ningún indicador, se mostrará después de los filtros comunes en el **Agregar elemento existente** cuadro de diálogo y el **abrir archivo** cuadro de diálogo, pero no se usará en el **buscar en archivos**  cuadro de diálogo.

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
|CommonFindFilesFilter|REG_DWORD|Hace que el filtro de uno de los filtros comunes en el **buscar en archivos** cuadro de diálogo. Los filtros comunes se muestran en la lista de filtros antes de los filtros de marcado no tan comunes.|
|CommonOpenFilesFilter|REG_DWORD|Hace que el filtro de uno de los filtros comunes en el **abrir archivo** cuadro de diálogo. Los filtros comunes se muestran en la lista de filtros antes de los filtros de marcado no tan comunes.|
|FindInFilesFilter|REG_DWORD|Muestra el filtro después de los filtros comunes en el **buscar en archivos** cuadro de diálogo.|
|NotOpenFileFilter|REG_DWORD|Indica que el filtro no se utiliza en el **abrir archivo** cuadro de diálogo.|
|NotAddExistingItemFilter|REG_DWORD|Indica que el filtro no se utiliza en el **Agregar elemento existente** cuadro de diálogo.|
|SortPriority|REG_DWORD|Establecer SortPriority para controlar el orden en que se muestran los filtros. Los valores mayores de SortPriority aparecen anteriormente en la lista de filtros.|

## <a name="directory-structure"></a>Estructura de directorios
 Los VSPackages puede colocar las carpetas y archivos de plantilla en cualquier lugar en un disco local o remoto, siempre y cuando la ubicación se ha registrado mediante el entorno de desarrollo integrado (IDE). Sin embargo, para facilitar la organización, se recomienda la siguiente estructura de directorios bajo la ruta de instalación de su producto.

 \Templates

 \Projects (contiene las plantillas de proyecto)

 \Applications

 \Components

 \ ...

 \ProjectItems (contiene los elementos de proyecto)

 \Class

 \Form

 \Web página

 \HelperFiles (contiene los archivos usados en los elementos de proyecto de varios archivos)

 \WizardFiles

## <a name="see-also"></a>Vea también
- [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Asistentes](../../extensibility/internals/wizards.md)
- [Localizar aplicaciones](../../ide/localizing-applications.md)
- [CATID para los objetos que se utilizan normalmente para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)