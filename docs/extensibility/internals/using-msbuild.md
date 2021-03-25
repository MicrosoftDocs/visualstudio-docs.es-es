---
title: Usar MSBuild | Microsoft Docs
description: MSBuild proporciona un formato XML extensible para crear archivos de proyecto que describen por completo los elementos de proyecto que se van a compilar, las tareas de compilación y las configuraciones de compilación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8891d9674a952f0272855c8b9203109ad2e22468
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090699"
---
# <a name="using-msbuild"></a>Uso de MSBuild
MSBuild proporciona un formato XML bien definido y extensible para crear archivos de proyecto que describen por completo los elementos de proyecto que se van a compilar, las tareas de compilación y las configuraciones de compilación.

## <a name="general-msbuild-considerations"></a>Consideraciones generales de MSBuild
 Los archivos de proyecto de MSBuild, por ejemplo, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] archivos. csproj y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . vbproj, contienen datos que se utilizan en tiempo de compilación, pero también pueden contener datos que se usan en tiempo de diseño. Los datos en tiempo de compilación se almacenan mediante primitivos de MSBuild, incluidos [Item Element (MSBuild)](../../msbuild/item-element-msbuild.md) y [Property Element (MSBuild)](../../msbuild/property-element-msbuild.md). Los datos en tiempo de diseño, que son datos específicos del tipo de proyecto y los subtipos de proyecto relacionados, se almacenan en XML de formato libre reservado para él.

 MSBuild no tiene compatibilidad nativa con objetos de configuración, pero proporciona atributos condicionales para especificar datos específicos de la configuración. Por ejemplo:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Para obtener más información sobre los atributos condicionales, vea [construcciones condicionales](../../msbuild/msbuild-conditional-constructs.md).

### <a name="extending-msbuild-for-your-project-type"></a>Extender MSBuild para el tipo de proyecto
 Las interfaces y las API de MSBuild están sujetas a cambios en versiones futuras de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Por lo tanto, es prudente usar las clases de Managed Package Framework (MPF) porque proporcionan protección frente a los cambios.

 Managed Package Framework for Projects (MPFProj) proporciona clases auxiliares para crear y administrar el nuevo sistema del proyecto. Puede encontrar el código fuente y las instrucciones de compilación en [MPF para proyectos-Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Las clases MPF específicas del proyecto son las siguientes:

|Clase|Implementación|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement` la clase es un contenedor para los elementos de MSBuild.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Generadores de un solo archivo frente a tareas de MSBuild
 Solo se puede tener acceso a los generadores de un solo archivo en tiempo de diseño, pero las tareas de MSBuild se pueden usar en tiempo de diseño y en tiempo de compilación. Para obtener la máxima flexibilidad, por lo tanto, use tareas de MSBuild para transformar y generar código. Para obtener más información, vea [herramientas personalizadas](../../extensibility/internals/custom-tools.md).

## <a name="see-also"></a>Consulte también
- [Referencia de MSBuild](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Herramientas personalizadas](../../extensibility/internals/custom-tools.md)
