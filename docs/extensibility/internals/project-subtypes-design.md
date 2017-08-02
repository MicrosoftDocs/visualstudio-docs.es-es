---
title: "Dise&#241;o de subtipos de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "subtipos de proyecto, diseño"
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# Dise&#241;o de subtipos de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los subtipos de proyecto permiten a VSPackages extender proyectos basados en Microsoft Build Engine \(MSBuild\).  El uso de agregación permite reutilizar la mayor parte del sistema de proyectos básico administrado implementado en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] todavía personalizar el comportamiento para un escenario determinado.  
  
 Los temas siguientes detallan el diseño básico y la implementación de los subtipos de proyecto:  
  
-   Diseño de subtipo del proyecto.  
  
-   Agregación de varios niveles.  
  
-   admitir interfaces.  
  
## Diseño de subtipo del proyecto  
 La inicialización de un subtipo del proyecto se logra agregando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> y los objetos principales de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> .  Esta agregación permite a un subtipo del proyecto para reemplazar o mejorar la mayoría de funciones del proyecto base.  Los subtipos de proyecto obtienen la primera oportunidad de controlar propiedades mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, los comandos mediante <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>, y la administración de elementos de proyecto mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>.  Los subtipos de proyectos también pueden extender:  
  
-   Objetos de configuración de proyecto.  
  
-   objetos dependientes.  
  
-   objetos de exploración de la independientes.  
  
-   Objetos de automatización de proyectos.  
  
-   Colecciones de propiedades de automatización de proyectos.  
  
 Para obtener más información sobre extensibilidad por subtipos de proyectos, vea [Propiedades y métodos extendidos subtipos de proyecto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### archivos de directivas  
 El entorno de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]proporciona un ejemplo de extender el sistema de proyectos base con un subtipo del proyecto en su implementación de archivos de directivas.  Un archivo de directivas permite calcular las referencias del entorno de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]controlando las características que incluyen el explorador de soluciones, el cuadro de diálogo **agregue el proyecto** , el cuadro de diálogo **Agregar nuevo elemento** y el cuadro de diálogo de **Propiedades** .  Subtipo de directiva reemplaza y mejora estas características con <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` e implementaciones de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> .  
  
##### Mecanismo de agregación  
 El mecanismo de agregación de subtipo del proyecto de entorno admite niveles de agregación múltiples, por lo que un subtipo avanzados es implementado por la condimentación adicional un proyecto condimentado.  Además, los objetos que admiten de un subtipo de proyecto, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, están diseñados para permitir varios niveles de las capas.  De acuerdo con las restricciones de las reglas COM y COM de agregación, los subtipos del proyecto y los proyectos bases necesitan programar de forma cooperativa para habilitar el subtipo interno o el proyecto base de combinar correctamente en delegar llamadas a métodos y administrar los recuentos de referencias.  Es decir, el proyecto se agregado alrededor tiene que estar programado para admitir la agregación.  
  
 La ilustración siguiente muestra una representación esquemática de una agregación de varios niveles de subtipo del proyecto.  
  
 ![Gráfico Visual Studio multilevel projectflavor](~/docs/extensibility/internals/media/vs_multilevelprojectflavor.gif "VS\_MultilevelProjectFlavor")  
Subtipo de varios niveles de proyecto  
  
 Una agregación de varios niveles de subtipo de proyecto consta de tres niveles, un proyecto base, incluido entre un subtipo del proyecto, después agregado aún más por un subtipo avanzadas del proyecto.  En la ilustración se centra en algunas de las interfaces que admiten que se proporcionan como parte de la arquitectura de subtipo del proyecto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  
  
##### mecanismos de distribución  
 Entre muchas de las funciones bases del sistema de proyectos mejoradas por un subtipo del proyecto son mecanismos de distribución.  Un subtipo de proyecto afectan los mecanismos de distribución implementando las interfaces de configuración \(como <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>\) que se recuperan llamando a QueryInterface en <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>.  En un escenario donde el subtipo del proyecto y subtipo avanzadas de proyecto agregan implementaciones diferentes de la configuración, el proyecto base llama `QueryInterface` en `IUnknown`avanzadas de subtipo del proyecto.  Si el subtipo interno y contiene la implementación de configuración la que el proyecto base está solicitando, subtipo avanzadas de proyecto delega a la implementación proporcionada por el subtipo interno del proyecto.  Como un mecanismo para conservar el estado de un nivel de agregación a otro, todos los niveles de subtipos de proyecto implementa <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> para conservar los datos XML relacionados no\-generación en los archivos de proyecto.  Para obtener más información, vea [Conservar los datos en el archivo de proyecto de MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).  <xref:EnvDTE80.IInternalExtenderProvider> se implementa como un mecanismo para recuperar los extensores de automatización de los subtipos del proyecto.  
  
 La ilustración siguiente se centra en la implementación de extensores de automatización, el objeto de exploración de la configuración de proyecto en particular, utilizado por subtipos de proyecto para extender el sistema de proyectos base.  
  
 ![Gráfico VS Project Project Auto Extender](~/docs/extensibility/internals/media/vs_projectflavorautoextender.gif "VS\_ProjectFlavorAutoExtender")  
Extensor de automatización del subtipo del proyecto.  
  
 Los subtipos de proyecto pueden extender aún más el sistema de proyectos base ampliar el modelo de objetos de automatización.  Éstos se definen como parte del objeto de automatización DTE y se utilizan para extender el objeto de proyecto, el objeto de `ProjectItem` y el objeto de `Configuration` .  Para obtener más información, vea [Extender el modelo de objetos del proyecto de Base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## Agregación de varios niveles  
 Una implementación de subtipo del proyecto que contiene un subtipo de nivel inferior de proyecto necesita programar de forma cooperativa para permitir que el subtipo interno de proyecto funcione correctamente.  Una lista de las responsabilidades de programación incluye:  
  
-   La implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> de subtipo del proyecto que está ajustando el subtipo interno debe delegar a <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> la implementación de subtipo interno de proyecto para <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> y los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> .  
  
-   La implementación de <xref:EnvDTE80.IInternalExtenderProvider> de subtipo del proyecto de contenedor debe delegar a del subtipo interno del proyecto.  En particular, la implementación de <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> necesita obtener la cadena de nombres del subtipo interno del proyecto y después concatenar cadenas que desea agregar como extensores.  
  
-   La implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> de un subtipo del proyecto de contenedor debe crear instancias del objeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> del subtipo y bloqueo internos del proyecto él como delegado privado, ya que solo el objeto base de la configuración del proyecto sabe directamente que existe el objeto de configuración del subtipo del proyecto del contenedor.  Subtipo externo de proyecto puede elegir inicialmente interfaces de configuración que desea administrar directamente, y después delega el resto a la implementación de subtipo interno del proyecto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## admitir interfaces  
 El proyecto base delega las llamadas a las interfaces entre un subtipo del proyecto, ampliar varios aspectos de su implementación.  Esto incluye objetos de configuración del proyecto que extienden y diferentes objetos del explorador de propiedades.  Estas interfaces que se recuperan llamando a `QueryInterface` en `punkOuter` \(un puntero a `IUnknown`\) del agregador fuera del subtipo del proyecto.  
  
|Interfaz|Subtipo del proyecto|  
|--------------|--------------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Permite el subtipo del proyecto:<br /><br /> -   Proporcione una implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />-   Controlar la versión del depurador lo que subtipo de proyecto para proporcionar su propia implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />-   Deshabilite la evaluación de expresiones en tiempo de diseño correctamente controlando el caso de `DBGLAUNCH_DesignTimeExprEval` en su implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|Permite el subtipo del proyecto:<br /><br /> -   Extiende <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> de project para agregar o quitar las propiedades independientes de la configuración del proyecto.<br />-   Extiende el objeto de automatización de proyectos \(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>\) del proyecto.<br /><br /> Los valores de propiedad anteriores se toman de la enumeración de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Permite que el subtipo de proyectos asignado a <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> el objeto dado el objeto de exploración de la configuración del proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Permite que el subtipo de proyectos asignado a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> o el objeto de `VSITEMID` , dado el objeto de exploración de la configuración del proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Permite que el subtipo del proyecto se conserva los datos estructurados arbitrarios XML al archivo de proyecto \(.vbproj o .csproj\).  Estos datos no está visible a MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Permite el subtipo del proyecto:<br /><br /> -   Agregue nuevas propiedades de MSBuild que se persistirán.<br />-   quite las propiedades innecesarias de MSBuild.<br />-   consulta por un valor actual de una propiedad de MSBuild.<br />-   cambie el valor actual de una propiedad de MSBuild.|  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>