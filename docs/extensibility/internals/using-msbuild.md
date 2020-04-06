---
title: Usar MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f961249ff584f7767dc2505bb20b1fb0961b7dd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704287"
---
# <a name="using-msbuild"></a>Uso de MSBuild
MSBuild proporciona un formato XML bien definido y extensible para crear archivos de proyecto que describen completamente los elementos de proyecto que se van a compilar, compilar tareas y generar configuraciones.

## <a name="general-msbuild-considerations"></a>Consideraciones generales de MSBuild
 Los archivos de proyecto de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] MSBuild, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] por ejemplo, los archivos .csproj y .vbproj, contienen datos que se usan en tiempo de compilación, pero también pueden contener datos que se usan en tiempo de diseño. Los datos en tiempo de compilación se almacenan mediante primitivas de MSBuild, incluidos [Item Element (MSBuild)](../../msbuild/item-element-msbuild.md) y [Property Element (MSBuild).](../../msbuild/property-element-msbuild.md) Los datos en tiempo de diseño, que son datos específicos del tipo de proyecto y de los subtipos de proyecto relacionados, se almacenan en XML de forma libre reservado para él.

 MSBuild no tiene compatibilidad nativa con objetos de configuración, pero proporciona atributos condicionales para especificar datos específicos de la configuración. Por ejemplo:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Para obtener más información sobre los atributos condicionales, vea [Construcciones condicionales](../../msbuild/msbuild-conditional-constructs.md).

### <a name="extending-msbuild-for-your-project-type"></a>Ampliación de MSBuild para el tipo de proyecto
 Las interfaces y API de MSBuild están [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]sujetas a cambios en versiones futuras de . Por lo tanto, es prudente usar las clases de marco de paquete administrado (MPF) porque proporcionan blindaje de los cambios.

 Managed Package Framework for Projects (MPFProj) proporciona clases auxiliares para crear y administrar un nuevo sistema de proyectos. Puede encontrar el código fuente y las instrucciones de compilación en [MPF for Projects - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Las clases MPF específicas del proyecto son las siguientes:

|Clase|Implementación|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement`clase es un contenedor para los elementos de MSBuild.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Generadores de archivos únicos frente a tareas de MSBuild
 Los generadores de archivos individuales solo son accesibles en tiempo de diseño, pero las tareas de MSBuild se pueden usar en tiempo de diseño y en tiempo de compilación. Por lo tanto, para obtener la máxima flexibilidad, use tareas de MSBuild para transformar y generar código. Para obtener más información, consulte [Herramientas personalizadas](../../extensibility/internals/custom-tools.md).

## <a name="see-also"></a>Vea también
- [Referencia de MSBuild](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Herramientas personalizadas](../../extensibility/internals/custom-tools.md)
