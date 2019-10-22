---
title: Usar MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab089a7a37acb377a043ec2c3a4db2c6538e6312
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344710"
---
# <a name="using-msbuild"></a>Uso de MSBuild
MSBuild proporciona un formato XML bien definido, extensible para crear archivos de proyecto que se describen por completo los elementos de proyecto para compilarse, las tareas de compilación y las configuraciones de compilación.

## <a name="general-msbuild-considerations"></a>Consideraciones generales MSBuild
 Los archivos de proyecto de MSBuild, por ejemplo, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] archivos .vbproj, contienen datos que se usan en tiempo de compilación, pero también pueden contener datos que se usan en tiempo de diseño. Datos de tiempo de compilación se almacenan utilizando primitivas de MSBuild, incluidos [elemento Item (MSBuild)](../../msbuild/item-element-msbuild.md) y [elemento Property (MSBuild)](../../msbuild/property-element-msbuild.md). Datos de tiempo de diseño, que son datos específicos del tipo de proyecto y los subtipos de proyecto relacionados, se almacenan en el XML de forma libre, reservada.

 MSBuild no tiene compatibilidad nativa para los objetos de configuración, pero proporcionar atributos condicionales para especificar los datos específicos de la configuración. Por ejemplo:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Para obtener más información sobre atributos condicionales, consulte [construcciones condicionales](../../msbuild/msbuild-conditional-constructs.md).

### <a name="extending-msbuild-for-your-project-type"></a>Ampliación de MSBuild para el tipo de proyecto
 Interfaces de MSBuild y las API están sujetos a cambios en versiones futuras de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Por lo tanto, es recomendable usar las clases de framework (MPF) de paquetes administrados, ya que proporcionan protección frente a cambios.

 Managed Package Framework para proyectos (MPFProj) proporciona clases auxiliares para crear y administrar el nuevo sistema de proyectos. Puede encontrar el origen de las instrucciones de código y compilación en [MPF de proyectos: Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Las clases MPF específicos del proyecto son los siguientes:

|Clase|Implementación|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement` clase es un contenedor para elementos de MSBuild.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Vs generadores de un solo archivo. Tareas de MSBuild
 Solo archivo generadores son accesibles en tiempo de diseño solo, pero se pueden usar las tareas de MSBuild en tiempo de diseño y tiempo de compilación. Para obtener la máxima flexibilidad, por lo tanto, use las tareas de MSBuild para transformar y generar código. Para obtener más información, consulte [Custom Tools](../../extensibility/internals/custom-tools.md).

## <a name="see-also"></a>Vea también
- [Referencia de MSBuild](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Herramientas personalizadas](../../extensibility/internals/custom-tools.md)