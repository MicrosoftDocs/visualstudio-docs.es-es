---
title: Usar MSBuild | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a148a7c5fa6d0e72345ab7f96696a11d5ba5185f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="using-msbuild"></a>Uso de MSBuild
MSBuild proporciona un formato XML bien definido, extensible para crear archivos de proyecto que se describen los elementos de proyecto para generarse, tareas de compilación y configuraciones de compilación totalmente.  
  
## <a name="general-msbuild-considerations"></a>Consideraciones de general MSBuild  
 Los archivos de proyecto de MSBuild, por ejemplo, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] archivos .vbproj, contienen datos que se utilizan en tiempo de compilación, pero también pueden contener datos que se utilizan en tiempo de diseño. Datos de tiempo de compilación se almacenan utilizando primitivas de MSBuild, incluidos los [elemento Item (MSBuild)](../../msbuild/item-element-msbuild.md) y [elemento Property (MSBuild)](../../msbuild/property-element-msbuild.md). Datos de tiempo de diseño, que son específicos para el tipo de proyecto y los subtipos de proyecto relacionado, se almacenan en XML de forma libre reservado para él.  
  
 MSBuild no tiene compatibilidad nativa para los objetos de configuración, pero proporcionar atributos condicionales para especificar datos específicos de la configuración. Por ejemplo:  
  
```xml  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Para obtener más información sobre atributos condicionales, consulte [construcciones condicional](../../msbuild/msbuild-conditional-constructs.md).  
  
### <a name="extending-msbuild-for-your-project-type"></a>Ampliación de MSBuild para el tipo de proyecto  
 Interfaces de MSBuild y las API están sujetos a cambios en versiones futuras de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Por lo tanto, es recomendable utilizar las clases de managed package framework (MPF) ya que proporcionan protección frente a los cambios.  
  
 Managed Package Framework para proyectos (MPFProj) proporciona clases auxiliares para crear y administrar el nuevo sistema de proyectos. Puede encontrar el origen de las instrucciones de código y la compilación en [MPF para proyectos - Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
 Las clases MPF específica del proyecto son los siguientes:  
  
|Clase|Implementación|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement`clase es un contenedor de elementos de MSBuild.  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>Frente a generadores de un solo archivo. Tareas de MSBuild  
 Archivo único generadores son accesibles en tiempo de diseño solo, pero se pueden usar tareas de MSBuild en tiempo de diseño y tiempo de compilación. Para obtener la máxima flexibilidad, por lo tanto, utilizar tareas de MSBuild para transformar y generar el código. Para obtener más información, consulte [Custom Tools](../../extensibility/internals/custom-tools.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de MSBuild](../../msbuild/msbuild-reference.md)   
 [MSBuild](../../msbuild/msbuild.md)   
 [Herramientas personalizadas](../../extensibility/internals/custom-tools.md)