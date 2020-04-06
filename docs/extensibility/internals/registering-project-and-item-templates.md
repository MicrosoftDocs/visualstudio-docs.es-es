---
title: Registro de plantillas de proyectos y elementos ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b64504c39b1fc3c4a82530b265cfd0e96832b4f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705822"
---
# <a name="registering-project-and-item-templates"></a>Registro de plantillas para proyectos y elementos
Los tipos de proyecto deben registrar los directorios donde se encuentran sus plantillas de proyecto y elemento de proyecto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]usa la información de registro asociada a los tipos de proyecto para determinar qué mostrar en los cuadros de diálogo **Agregar nuevo proyecto** y Agregar nuevo **elemento.**

 Para obtener más información acerca de las plantillas, vea Agregar plantillas de [proyecto y elemento](../../extensibility/internals/adding-project-and-project-item-templates.md)de proyecto .

## <a name="registry-entries-for-projects"></a>Entradas del Registro para Proyectos
 En los ejemplos siguientes se muestran las entradas\\<del Registro en HKEY_LOCAL_MACHINE, Software, Microsoft, VisualStudio*Versión*>. Las tablas adjuntas explican los elementos utilizados en los ejemplos.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|Nombre|Tipo|Descripción|
|----------|----------|-----------------|
|@|REG_SZ|Nombre predeterminado de proyectos de este tipo.|
|DisplayName|REG_SZ|Identificador de recurso del nombre que se va a recuperar del archivo DLL satélite registrado en Paquetes.|
|Paquete|REG_SZ|ID de clase del paquete registrado en Paquetes.|
|ProjectTemplatesDir|REG_SZ|Ruta de acceso predeterminada de los archivos de plantilla de proyecto. Los archivos de plantilla de proyecto se muestran mediante la plantilla **Nuevo proyecto.**|

### <a name="registering-item-templates"></a>Registro de plantillas de elementos
 Debe registrar el directorio donde almacena las plantillas de elementos.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Nombre | Tipo | Descripción |
|--------------------------|-----------| - |
| @ | REG_SZ | Identificador de recurso para agregar plantillas de elemento. |
| TemplatesDir | REG_SZ | Ruta de acceso de los elementos del proyecto que se muestran en el cuadro de diálogo para el Asistente para **agregar nuevo elemento.** |
| TemplatesLocalizedSubDir | REG_SZ | Identificador de recurso de una cadena que nombra el subdirectorio de TemplatesDir que contiene plantillas localizadas. Dado [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que carga el recurso de cadena desde archivos DLL satélite si los tiene, cada DLL satélite puede contener un nombre de subdirectorio localizado diferente. |
| SortPriority | REG_DWORD | Establezca SortPriority para controlar el orden en que se muestran las plantillas en el cuadro de diálogo **Agregar nuevo elemento.** Los valores SortPriority más grandes aparecen anteriormente en la lista de plantillas. |

### <a name="registering-file-filters"></a>Registro de filtros de archivos
 Opcionalmente, puede registrar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] filtros que se usan cuando solicita nombres de archivo. Por ejemplo, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] el filtro para el cuadro de diálogo **Abrir archivo** es:

 **Archivos de Visual\*CTM\*(.cs,\*.resx, .settings,\*.xsd,\*.wsdl); \*.cs,\*.resx,\*.settings,\*\*.xsd, .wsdl)**

 Para admitir el registro de varios filtros, cada filtro se registra en\\<su propia\\\<subclave en HKEY_LOCAL_MACHINE, Software, Microsoft, VisualStudio*Versión*>, Proyectos,*ProjectGUID*>, Filtros,\\<*subclave*>. El nombre de la subclave es arbitrario; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignora el nombre de la subclave y utiliza solo sus valores.

 Puede controlar los contextos en los que se utiliza un filtro estableciendo indicadores, que se muestran en la tabla siguiente. Si un filtro no tiene ninguna marca establecida, aparecerá después de los filtros comunes en el cuadro de diálogo **Agregar elemento existente** y el cuadro de diálogo Abrir **archivo,** pero no se usará en el cuadro de diálogo **Buscar en archivos.**

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
|CommonFindFilesFilter|REG_DWORD|Convierte el filtro en uno de los filtros comunes del cuadro de diálogo **Buscar en archivos.** Los filtros comunes se enumeran en la lista de filtros antes de que los filtros no estén marcados como comunes.|
|CommonOpenFilesFilter|REG_DWORD|Convierte el filtro en uno de los filtros comunes del cuadro de diálogo **Abrir archivo.** Los filtros comunes se enumeran en la lista de filtros antes de que los filtros no estén marcados como comunes.|
|FindInFilesFilter|REG_DWORD|Enumera el filtro después de los filtros comunes en el cuadro de diálogo **Buscar en archivos.**|
|NotOpenFileFilter|REG_DWORD|Indica que el filtro no se utiliza en el cuadro de diálogo **Abrir archivo.**|
|NotAddExistingItemFilter|REG_DWORD|Indica que el filtro no se utiliza en el cuadro de diálogo **Agregar elemento existente.**|
|SortPriority|REG_DWORD|Establezca SortPriority para controlar el orden en que se muestran los filtros. Los valores SortPriority más grandes aparecen anteriormente en la lista de filtros.|

## <a name="directory-structure"></a>Estructura de directorios
 VSPackages puede colocar archivos de plantilla y carpetas en cualquier lugar de un disco local o remoto, siempre y cuando la ubicación se registre a través del entorno de desarrollo integrado (IDE). Sin embargo, para facilitar la organización, se recomienda la siguiente estructura de directorios en la ruta de instalación del producto.

 Plantillas

 •Proyectos (contiene las plantillas de proyecto)

 Aplicaciones

 •Componentes

 \ ...

 •ProjectItems (contiene los elementos del proyecto)

 •Clase

 •Formulario

 Página web

 •HelperFiles (contiene los archivos utilizados en elementos de proyecto de varios archivos)

 •WizardFiles

## <a name="see-also"></a>Vea también

- [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Asistentes](../../extensibility/internals/wizards.md)
- [Localizar aplicaciones](../../ide/globalizing-and-localizing-applications.md)
- [CATID para los objetos que se usan normalmente para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
