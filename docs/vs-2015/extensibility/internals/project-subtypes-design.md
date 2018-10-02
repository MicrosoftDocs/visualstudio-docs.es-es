---
title: Diseño de subtipos de proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6b4d9f77f4ea1a302efb38bb75ebecd2ee54c1f9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574094"
---
# <a name="project-subtypes-design"></a>Diseño de subtipos de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [diseño subtipos de proyecto](https://docs.microsoft.com/visualstudio/extensibility/internals/project-subtypes-design).  
  
Subtipos de proyecto permiten a los VSPackages ampliar proyectos basados en Microsoft Build Engine (MSBuild). El uso de agregación permite reutilizar la mayor parte del sistema del proyecto principal administrada implementada en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aún sigue personalizar el comportamiento de un escenario determinado.  
  
 Los siguientes temas detallan el diseño básico y la implementación de subtipos de proyecto:  
  
-   Diseño de subtipo de proyecto.  
  
-   Agregación de varios nivel.  
  
-   Interfaces admitidas.  
  
## <a name="project-subtype-design"></a>Diseño de subtipo de proyecto  
 La inicialización de un subtipo de proyecto se logra agregando principal <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> objetos. Esta agregación permite un subtipo de proyecto reemplazar o mejorar la mayoría de las capacidades del proyecto base. Subtipos de proyecto obtención la primera oportunidad de controlar las propiedades mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, mediante los comandos <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>y administración de elemento de proyecto mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>. También pueden ampliar los subtipos de proyecto:  
  
-   Objetos de configuración del proyecto.  
  
-   Objetos dependientes de la configuración.  
  
-   Examinar independientes de la configuración de objetos.  
  
-   Objetos de automatización de proyecto.  
  
-   Colecciones de propiedades de automatización de proyecto.  
  
 Para obtener más información sobre la extensibilidad de subtipos de proyecto, vea [propiedades y métodos extendidos por subtipos de proyecto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### <a name="policy-files"></a>Archivos de directivas  
 El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entorno proporciona un ejemplo de extender el sistema de proyectos base con un subtipo de proyecto en su implementación de archivos de directivas. Un archivo de directiva permite el modelado de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entorno mediante la administración de características que incluyen el Explorador de soluciones, **Agregar proyecto** cuadro de diálogo, **Agregar nuevo elemento** cuadro de diálogo y el  **Propiedades** cuadro de diálogo. El subtipo de directiva invalida y mejora estas características a través de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementaciones.  
  
##### <a name="aggregation-mechanism"></a>Mecanismo de agregación  
 Mecanismo de agregación de subtipo de proyecto del entorno es compatible con varios niveles de agregación, lo que permite un subtipo de avanzada que se implementa en más flavoring un proyecto característico. Además, los objetos auxiliares de un proyecto de subtipo, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, están diseñados para permitir varios niveles de disposición en capas. De acuerdo con las restricciones de COM y COM reglas de agregación, subtipos de proyecto y los proyectos de base deben programarse de forma cooperativa para permitir el subtipo interno o el proyecto base participar correctamente las llamadas a métodos de delegación y la administración de recuentos de referencias . Es decir, el proyecto que se agregan debe programarse para admitir la agregación.  
  
 La siguiente ilustración muestra una representación esquemática de una agregación de subtipo de proyecto de varios niveles.  
  
 ![Gráfico de projectflavor multinivel de Visual Studio](../../extensibility/internals/media/vs-multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
Subtipo de proyecto de varios niveles  
  
 Una agregación de subtipo de proyecto de varios niveles se compone de tres niveles, un proyecto de base, que se agrega un subtipo de proyecto y, después, agregan aún más un subtipo de proyecto avanzadas. En la ilustración se centra en algunas de las interfaces auxiliares que se proporcionan como parte de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] arquitectura de subtipo de proyecto.  
  
##### <a name="deployment-mechanisms"></a>Mecanismos de implementación  
 Entre otros muchos del sistema del proyecto base funcionalidades mejoradas mediante un subtipo de proyecto son mecanismos de implementación. Un subtipo de proyecto influye en mecanismos de implementación mediante la implementación de interfaces de configuración (como <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>) que se recuperan llamando a QueryInterface en <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>. En un escenario donde el subtipo de proyecto y el subtipo de proyecto avanzada agregan implementaciones de configuración diferente, el proyecto base llama a `QueryInterface` en el subtipo de proyecto avanzada `IUnknown`. Si el subtipo interno del proyecto contiene la implementación de configuración que está solicitando el proyecto de base para los delegados de subtipo de proyecto avanzada para la implementación proporcionada por el subtipo de proyecto interno. Como un mecanismo para conservar el estado de nivel de agregación de uno a otro, se implementan todos los niveles de subtipos de proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> conservar la compilación no relacionadas con datos XML en los archivos del proyecto. Para obtener más información, consulte [conservar datos en el archivo de proyecto de MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> se implementa como un mecanismo para recuperar los extensores de automatización de los subtipos de proyecto.  
  
 La siguiente ilustración se centra en la implementación de extensores de automatización, el objeto de exploración de la configuración de proyecto en particular, utilizan subtipos de proyecto para ampliar el sistema del proyecto base.  
  
 ![Gráfico de VS Project Project Auto Extender](../../extensibility/internals/media/vs-projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
Extensor de automatización del subtipo de proyecto.  
  
 Subtipos de proyecto pueden ampliar aún más el sistema de proyectos base al extender el modelo de objetos de automatización. Estos se definen como parte del objeto de automatización DTE y se usan para extender el objeto de proyecto, el `ProjectItem` objeto y el `Configuration` objeto. Para obtener más información, vea [extender el modelo de objetos del proyecto Base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## <a name="multi-level-aggregation"></a>Agregación de varios nivel  
 Una implementación de subtipo de proyecto que contiene un subtipo de proyecto de nivel inferior debe programarse de forma cooperativa para permitir que el subtipo de proyecto interno funcionar correctamente. Incluye una lista de las responsabilidades de programación:  
  
-   El <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementación del subtipo de proyecto que se ajuste el subtipo interno debe delegar en el <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementación de subtipo interno del proyecto para ambos <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> métodos.  
  
-   El <xref:EnvDTE80.IInternalExtenderProvider> implementación del subtipo de proyecto de contenedor debe delegar a la de su subtipo interno del proyecto. En concreto, la implementación de <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> debe obtener la cadena de nombres de subtipo interno del proyecto y, a continuación, concatenar las cadenas desea agregar como extensores.  
  
-   El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> debe crear una instancia de la implementación de un subtipo de proyecto contenedor la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> objeto de su interior subtipo de proyecto y mantenerlo como un delegado privado, ya que sólo el objeto de configuración del proyecto del proyecto base directamente sabe que el contenedor existe el objeto de configuración del subtipo de proyecto. El subtipo de proyecto externo puede elegir inicialmente interfaces de configuración desea controlar directamente y, a continuación, delegar el resto de la implementación del subtipo interno del proyecto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## <a name="supporting-interfaces"></a>Interfaces admitidas  
 El proyecto de base delega las llamadas a admitir interfaces agregadas por un subtipo de proyecto para ampliar los diversos aspectos de su implementación. Esto incluye la ampliación de los objetos de configuración de proyecto y varios objetos del explorador de propiedades. Estas interfaces se recuperan mediante una llamada a `QueryInterface` en `punkOuter` (un puntero a la `IUnknown`) del agregador de subtipo de proyecto más externo.  
  
|Interfaz|Subtipo de proyecto|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Permite que el subtipo de proyecto para:<br /><br /> -Proporcione una implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />-Controlar el lanzamiento del depurador, ya que permite el subtipo de proyecto proporcionar su propia implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />-Deshabilitar la evaluación de expresiones en tiempo de diseño al tratar de forma adecuada el `DBGLAUNCH_DesignTimeExprEval` mayúsculas en su implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|Permite que el subtipo de proyecto para:<br /><br /> -Ampliar la <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> del proyecto para agregar o quitar propiedades de configuración independientes del proyecto.<br />-Extender el objeto de automatización de proyecto (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) del proyecto.<br /><br /> Los valores de propiedad anteriores se toman de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> enumeración.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Permite que el subtipo de proyecto asignar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objeto según el objeto de exploración de la configuración de proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Permite que el subtipo de proyecto asignar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> o `VSITEMID` objeto, dado el objeto de exploración de la configuración de proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Permite que el subtipo de proyecto conservar los datos XML estructurado arbitrarios al archivo de proyecto (.vbproj o .csproj). Estos datos no son visibles para MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Permite que el subtipo de proyecto para:<br /><br /> -Agregue nuevas propiedades de MSBuild que se deben conservar.<br />-Quitar propiedades innecesarias de MSBuild.<br />-Query para un valor actual de una propiedad de MSBuild.<br />-Cambiar el valor actual de una propiedad de MSBuild.|  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>

