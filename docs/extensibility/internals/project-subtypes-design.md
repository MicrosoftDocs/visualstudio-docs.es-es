---
title: "Diseño de subtipos de proyecto | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 126bee146d1f53233db3c14672f80da4c0d60e9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="project-subtypes-design"></a>Diseño de subtipos de proyecto
Subtipos de proyecto permiten VSPackages ampliar proyectos basados en Microsoft Build Engine (MSBuild). El uso de agregación permite reutilizar la mayor parte de implementada en el sistema del proyecto principal administrada [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aún sigue personalizar el comportamiento de un escenario determinado.  
  
 Los siguientes temas detalla el diseño básico y la implementación de subtipos de proyecto:  
  
-   Diseño de subtipo de proyecto.  
  
-   Agregación de varios nivel.  
  
-   Compatibilidad con Interfaces.  
  
## <a name="project-subtype-design"></a>Diseño de subtipo de proyecto  
 La inicialización de un subtipo de proyecto se logra al agregar el método main <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> objetos. Esta agregación permite un subtipo de proyecto invalidar o para mejorar la mayoría de las capacidades del objeto base. Subtipos de proyecto obtener la primera oportunidad de controlar propiedades mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, mediante los comandos <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>y administración de elementos de proyecto mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>. También pueden ampliar los subtipos de proyecto:  
  
-   Objetos de configuración del proyecto.  
  
-   Objetos dependientes de la configuración.  
  
-   Objetos de examinar independientes de la configuración.  
  
-   Objetos de automatización de proyecto.  
  
-   Colecciones de propiedades de automatización de proyecto.  
  
 Para obtener más información sobre extensibilidad para los subtipos de proyecto, vea [propiedades y métodos extendidos subtipos de proyecto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### <a name="policy-files"></a>Archivos de directivas  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno proporciona un ejemplo de cómo extender el sistema de proyectos base con un subtipo de proyecto en su implementación de archivos de directivas. Un archivo de directiva permite el modelado de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno mediante la administración de características que incluyen el Explorador de soluciones, **Agregar proyecto** cuadro de diálogo, **Agregar nuevo elemento** cuadro de diálogo y el  **Propiedades** cuadro de diálogo. El subtipo de directiva invalida y mejora estas características a través de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> las implementaciones.  
  
##### <a name="aggregation-mechanism"></a>Mecanismo de agregación  
 Mecanismo de agregación de subtipo de proyecto del entorno admite varios niveles de agregación, lo que permite un subtipo avanzado que se implementa en más flavoring un proyecto con tipo. Además, los objetos auxiliares de un proyecto de subtipo, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, están diseñados para permitir que varios niveles de distribución en capas. En consonancia con las restricciones de COM y COM reglas de agregación, subtipos de proyecto y proyectos de base que se pueden programar de forma cooperativa para habilitar el subtipo interno o en el proyecto de base correctamente participar en llamadas a métodos de delegación y la administración de recuentos de referencias . Es decir, el proyecto que se agregan debe programarse para admitir la agregación.  
  
 En la siguiente ilustración muestra una representación esquemática de una agregación de subtipo de proyecto de varios niveles.  
  
 ![Gráfico de projectflavor multinivel de Visual Studio](../../extensibility/internals/media/vs_multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
Subtipo de proyecto de varios niveles  
  
 Una agregación de subtipo de proyecto multinivel consta de tres niveles, un proyecto de base, que se agrega un subtipo de proyecto, a continuación, más agregadas por un subtipo avanzadas del proyecto. En la ilustración se centra en algunas de las interfaces de soporte que se proporcionan como parte de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] arquitectura de subtipo del proyecto.  
  
##### <a name="deployment-mechanisms"></a>Mecanismos de implementación  
 Uno de los muchos del sistema del proyecto de base funcionalidades mejoradas por un subtipo de proyecto son mecanismos de implementación. Un subtipo de proyecto influye en los mecanismos de implementación mediante la implementación de interfaces de configuración (como <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>) que se recuperan mediante una llamada a QueryInterface en <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>. En un escenario donde el subtipo de proyecto y el subtipo de proyecto avanzada agreguen las implementaciones de configuración diferente, el proyecto de base llama `QueryInterface` en el subtipo de proyecto avanzada `IUnknown`. Si el subtipo de proyecto interna contiene la implementación de configuración que está solicitando el proyecto de base, el subtipo avanzadas del proyecto se delega a la implementación proporcionada por el subtipo de proyecto interna. Como un mecanismo para conservar el estado de nivel de agregación de uno a otro, implementan todos los niveles de subtipos de proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> conservar la compilación no relacionadas con datos XML en los archivos de proyecto. Para obtener más información, consulte [guardar datos en el archivo de proyecto de MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider>se implementa como un mecanismo para recuperar los extensores de automatización de los subtipos de proyecto.  
  
 En la siguiente ilustración se centra en la implementación de extensor de automatización, el objeto de búsqueda de la configuración de proyecto en particular, utilizan subtipos de proyecto para extender el sistema de proyectos de base.  
  
 ![Gráfico de VS Project Project Auto Extender](../../extensibility/internals/media/vs_projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
Extensor de automatización del subtipo de proyecto.  
  
 Subtipos de proyecto pueden ampliar aún más el sistema de proyectos base extendiendo el modelo de objetos de automatización. Estos se definen como parte del objeto de automatización DTE y se utilizan para ampliar el objeto del proyecto, el `ProjectItem` objeto y el `Configuration` objeto. Para obtener más información, vea [extender el modelo de objetos del proyecto de Base de](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## <a name="multi-level-aggregation"></a>Agregación de varios nivel  
 Una implementación de subtipo de proyecto que contiene un subtipo de proyecto de nivel inferior debe programarse de forma cooperativa para permitir el subtipo de proyecto interna funcionar correctamente. Incluye una lista de las responsabilidades de programación:  
  
-   El <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementación del subtipo de proyecto que se ajuste el subtipo interno debe delegar a la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementación del subtipo de proyecto interna para ambos <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> métodos.  
  
-   El <xref:EnvDTE80.IInternalExtenderProvider> implementación del subtipo de proyecto contenedor debe delegar a la de su subtipo de proyecto interna. En particular, la implementación de <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> debe obtener la cadena de nombres desde el subtipo de proyecto interna y, a continuación, concatenar las cadenas que va a agregar como dispositivos Extender.  
  
-   El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> debe crear una instancia de la implementación de un subtipo de proyecto contenedor el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> objeto de su interior subtipo de proyecto y mantenerlo como un delegado privado, ya que sólo el objeto de configuración de proyecto del proyecto base directamente sabe que el contenedor existe el objeto de configuración del subtipo de proyecto. El subtipo de proyecto externo puede elegir inicialmente interfaces de configuración desea controlar directamente y, a continuación, delegar el resto del subtipo de proyecto interna de implementación para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## <a name="supporting-interfaces"></a>Compatibilidad con Interfaces  
 El proyecto de base delega las llamadas para admitir interfaces agregadas por un subtipo de proyecto para ampliar los diversos aspectos de su implementación. Esto incluye extender los objetos de configuración de proyecto y varios objetos del explorador de propiedades. Estas interfaces se recuperan mediante una llamada a `QueryInterface` en `punkOuter` (un puntero a la `IUnknown`) del agregador de subtipo de proyecto más externo.  
  
|Interfaz|Subtipo de proyecto|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Permite al subtipo de proyecto para:<br /><br /> -Proporcione una implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />-Controlar el lanzamiento del depurador al permitir que el subtipo de proyecto proporcionar su propia implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />-Deshabilitar la evaluación de expresiones en tiempo de diseño mediante el control de forma adecuada el `DBGLAUNCH_DesignTimeExprEval` mayúsculas en su implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|Permite al subtipo de proyecto para:<br /><br /> -Ampliar la <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> del proyecto para agregar o quitar propiedades de configuración independientes del proyecto.<br />-Ampliar el objeto de automatización de proyecto (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) del proyecto.<br /><br /> Valores de propiedad anteriores se toman de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> enumeración.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Permite el subtipo de proyecto asignar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objeto según el objeto de búsqueda de la configuración de proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Permite el subtipo de proyecto asignar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> o `VSITEMID` objeto, según el objeto de búsqueda de la configuración de proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Permite el subtipo de proyecto conservar los datos XML estructurado arbitrarios en el archivo de proyecto (.vbproj o .csproj). Estos datos no son visibles para MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Permite al subtipo de proyecto para:<br /><br /> -Agregue nuevas propiedades de MSBuild que se deben conservar.<br />-Quitar propiedades innecesarias de MSBuild.<br />-Consulta para un valor actual de una propiedad de MSBuild.<br />-Cambie el valor actual de una propiedad de MSBuild.|  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>