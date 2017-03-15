---
title: "Uso de MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, compilar con MSBuild"
  - "MSBuild, extensibilidad"
  - "paquetes, compilar con MSBuild"
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Uso de MSBuild
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

MSBuild proporciona un formato XML bien definido, extensible para crear archivos de proyecto que describen completamente los elementos de proyecto para generarse, tareas de compilación y configuraciones de compilación.  
  
 Para obtener un ejemplo de extremo a extremo de un sistema de proyecto de lenguaje basado en MSBuild, vea el ejemplo de IronPython Deep Dive en el[Muestras de VSSDK](../../misc/vssdk-samples.md).  
  
## Consideraciones generales MSBuild  
 Los archivos de proyecto de MSBuild, por ejemplo, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] archivos .vbproj, contienen datos que se utilizan en tiempo de compilación, pero también pueden contener datos que se utilizan en tiempo de diseño. Datos de tiempo de compilación se almacenan utilizando primitivas de MSBuild, incluidos [Elemento Item \(MSBuild\)](../../msbuild/item-element-msbuild.md) y [Elemento Property \(MSBuild\)](../../msbuild/property-element-msbuild.md). Datos de tiempo de diseño, que contiene los datos específicos del tipo de proyecto y los subtipos de proyecto relacionados, se almacenan en el XML de forma libre que se reserva para él.  
  
 MSBuild no tiene compatibilidad nativa para los objetos de configuración, pero proporcionar atributos condicionales para especificar datos de configuración específicos. Por ejemplo:  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Para obtener más información sobre atributos condicionales, consulte [Construcciones condicionales](../../msbuild/msbuild-conditional-constructs.md).  
  
### Extensión para el tipo de proyecto de MSBuild  
 Interfaces de MSBuild y las API están sujetos a cambios en versiones futuras de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Por lo tanto, es recomendable usar las clases de framework \(MPF\) de paquete administrado porque proporcionan protección de los cambios.  
  
 Managed Package Framework para proyectos \(MPFProj\) proporciona clases auxiliares para crear y administrar el nuevo sistema de proyectos. Puede encontrar el origen de instrucciones de código y compilación en [MPF de proyectos: Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
 Las clases MPF específico del proyecto son los siguientes:  
  
|Clase|Implementación|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` clase es un contenedor para los elementos de MSBuild.  
  
#### Vs generadores de un solo archivo. Tareas de MSBuild  
 Archivo único generadores son accesibles en tiempo de diseño sólo, pero se pueden usar tareas de MSBuild en tiempo de diseño y en tiempo de compilación. Para obtener la máxima flexibilidad, por lo tanto, usar tareas de MSBuild para transformar y generar código. Para obtener más información, consulta [Herramientas personalizadas](../../extensibility/internals/custom-tools.md).  
  
## Vea también  
 [Referencia de MSBuild](../../msbuild/msbuild-reference.md)   
 [MSBuild](http://msdn.microsoft.com/es-es/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [Herramientas personalizadas](../../extensibility/internals/custom-tools.md)