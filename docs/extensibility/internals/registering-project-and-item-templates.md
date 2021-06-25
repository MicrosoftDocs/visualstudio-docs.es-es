---
title: Registro de plantillas de proyecto y elemento | Microsoft Docs
description: Obtenga información sobre Visual Studio información de registro de los tipos de proyecto para determinar qué mostrar en los cuadros de diálogo Agregar nuevo proyecto y Agregar nuevo elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b60022c6adf65d0b0d60d32b4ad7ae72067726d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905637"
---
# <a name="registering-project-and-item-templates"></a>Registro de plantillas para proyectos y elementos
Los tipos de proyecto deben registrar los directorios donde se encuentran sus plantillas de proyecto y elemento de proyecto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa la información de registro asociada a los tipos de proyecto para determinar qué mostrar en los cuadros de **diálogo** Agregar nuevo proyecto y **Agregar nuevo** elemento .

 Para obtener más información sobre las plantillas, vea [Adding Project and Project Item Templates](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="registry-entries-for-projects"></a>Entradas del Registro para proyectos
 En los ejemplos siguientes se muestran las entradas del Registro en HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ < *versión>.* Las tablas que lo acompañan explican los elementos utilizados en los ejemplos.

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
|DisplayName|REG_SZ|Identificador de recurso del nombre que se va a recuperar del archivo DLL satélite registrado en Paquetes.|
|Paquete|REG_SZ|Identificador de clase del paquete registrado en Paquetes.|
|ProjectTemplatesDir|REG_SZ|Ruta de acceso predeterminada de los archivos de plantilla de proyecto. La plantilla Nuevo proyecto muestra los archivos de plantilla **de** proyecto.|

### <a name="registering-item-templates"></a>Registro de plantillas de elemento
 Debe registrar el directorio donde almacena las plantillas de elemento.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Nombre | Tipo | Descripción |
|--------------------------|-----------| - |
| @ | REG_SZ | Id. de recurso para agregar plantillas de elemento. |
| TemplatesDir | REG_SZ | Ruta de acceso de los elementos de proyecto que se muestran en el cuadro de diálogo del **Asistente para agregar nuevo** elemento. |
| TemplatesLocalizedSubDir | REG_SZ | Identificador de recurso de una cadena que denomina el subdirectorio de TemplatesDir que contiene plantillas localizadas. Dado que carga el recurso de cadena desde archivos DLL satélite si los tiene, cada archivo DLL satélite puede [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] contener un nombre de subdirectorio localizado diferente. |
| SortPriority | REG_DWORD | Establezca SortPriority para regular el orden en el que se muestran las plantillas en el **cuadro de diálogo** Agregar nuevo elemento. Los valores de SortPriority más grandes aparecen anteriormente en la lista de plantillas. |

### <a name="registering-file-filters"></a>Registro de filtros de archivo
 Opcionalmente, puede registrar filtros que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usan cuando solicita nombres de archivo. Por ejemplo, el [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filtro del cuadro de diálogo **Abrir** archivo es:

 **Archivos de Visual C# ( \* .cs, \* .resx, \* .settings, \* .xsd, \* .wsdl); \* . cs, \* .resx, \* .settings, \* .xsd, \* .wsdl)**

 Para admitir el registro de varios filtros, cada filtro se registra en su propia subclave en HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ < *Version*>\Projects \\ { \<*ProjectGUID*> }\Filters \\ < *Subkey*>. El nombre de la subclave es arbitrario; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] omite el nombre de la subclave y usa solo sus valores.

 Puede controlar los contextos en los que se usa un filtro estableciendo marcas, que se muestran en la tabla siguiente. Si un filtro no tiene ninguna marca establecida, aparecerá después de los filtros comunes  en el cuadro de diálogo Agregar  elemento existente y en el cuadro de diálogo Abrir archivo, pero no se usará en el cuadro de diálogo Buscar en archivos . 

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
|CommonFindFilesFilter|REG_DWORD|Convierte el filtro en uno de los filtros comunes del **cuadro de diálogo** Buscar en archivos . Los filtros comunes se enumeran en la lista de filtros antes de que los filtros no estén marcados como comunes.|
|CommonOpenFilesFilter|REG_DWORD|Convierte el filtro en uno de los filtros comunes del **cuadro de diálogo** Abrir archivo. Los filtros comunes se enumeran en la lista de filtros antes de que los filtros no estén marcados como comunes.|
|FindInFilesFilter|REG_DWORD|Muestra el filtro después de los filtros comunes en el **cuadro de diálogo Buscar en** archivos .|
|NotOpenFileFilter|REG_DWORD|Indica que el filtro no se usa en el **cuadro de diálogo** Abrir archivo .|
|NotAddExistingItemFilter|REG_DWORD|Indica que el filtro no se usa en el **cuadro de diálogo Agregar elemento** existente .|
|SortPriority|REG_DWORD|Establezca SortPriority para regular el orden en el que se muestran los filtros. Los valores de SortPriority más grandes aparecen anteriormente en la lista de filtros.|

## <a name="directory-structure"></a>Estructura de directorios
 Los VSPackages pueden colocar archivos de plantilla y carpetas en cualquier lugar de un disco local o remoto, siempre que la ubicación se registre a través del entorno de desarrollo integrado (IDE). Sin embargo, para facilitar la organización, se recomienda la siguiente estructura de directorios en la ruta de instalación del producto.

 \Templates

 \Projects (contiene las plantillas de proyecto)

 \Applications

 \Components

 \ ...

 \ProjectItems (contiene los elementos del proyecto)

 \Class

 \Form

 \Web Page

 \HelperFiles (contiene los archivos usados en elementos de proyecto de varios archivos)

 \WizardFiles

## <a name="see-also"></a>Consulta también

- [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Asistentes](../../extensibility/internals/wizards.md)
- [Localizar aplicaciones](../../ide/globalizing-and-localizing-applications.md)
- [CATID para los objetos que se usan normalmente para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
