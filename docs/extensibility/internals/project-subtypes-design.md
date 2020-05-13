---
title: Diseño de subtipos de proyecto ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b939d197bfd7e58b555ca7698f08643e3d38ef2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706443"
---
# <a name="project-subtypes-design"></a>Diseño de subtipos de proyecto

Los subtipos de proyecto permiten a VSPackages extender proyectos basados en el motor de compilación de Microsoft (MSBuild). El uso de la agregación le permite reutilizar la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mayor parte del sistema de proyecto administrado principal implementado en, pero aún así personalizar el comportamiento para un escenario determinado.

 Los temas siguientes detallan el diseño básico y la implementación de subtipos de proyecto:

- Diseño de subtipos de proyecto.

- Agregación de varios niveles.

- Interfaces de apoyo.

## <a name="project-subtype-design"></a>Diseño de subtipos de proyecto

La inicialización de un subtipo de proyecto se <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> logra agregando el principal y los objetos. Esta agregación permite que un subtipo de proyecto invalide o mejore la mayoría de las capacidades del proyecto base. Los subtipos de proyecto obtienen <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> primera <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>oportunidad de controlar <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>las propiedades mediante , comandos mediante y , y la administración de elementos de proyecto mediante . Los subtipos de proyecto también pueden ampliar:

- Objetos de configuración del proyecto.

- Objetos dependientes de la configuración.

- Objetos de exploración independientes de la configuración.

- Objetos de automatización de proyectos.

- Colecciones de propiedades de automatización de proyectos.

Para obtener más información sobre la extensibilidad por subtipos de proyecto, vea [Propiedades y métodos extendidos por subtipos](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)de proyecto .

### <a name="policy-files"></a>Archivos de directivas

El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno proporciona un ejemplo de extensión del sistema de proyecto base con un subtipo de proyecto en su implementación de archivos de directivas. Un archivo de directiva [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] permite dar forma al entorno mediante la administración de características que incluyen el Explorador de soluciones, **Agregar proyecto** cuadro de diálogo, **Agregar nuevo elemento** cuadro de diálogo y el **propiedades** cuadro de diálogo. El subtipo de directiva invalida <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>y `IOleCommandTarget` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> mejora estas características a través de , y las implementaciones.

### <a name="aggregation-mechanism"></a>Mecanismo de Agregación

El mecanismo de agregación de subtipos de proyecto del entorno admite varios niveles de agregación, lo que permite implementar un subtipo avanzado saborificando aún más un proyecto con sabor. Además, los objetos auxiliares de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>un subtipo de proyecto, como , están diseñados para permitir varios niveles de capas. De acuerdo con las restricciones de las reglas de agregación COM y COM, los subtipos de proyecto y los proyectos base deben programarse de forma cooperativa para permitir que el subtipo interno o el proyecto base participen correctamente en la delegación de llamadas a métodos y la administración de recuentos de referencias. Es decir, el proyecto a punto de ser agregado tiene que ser programado para admitir la agregación.

En la ilustración siguiente se muestra una representación esquemática de una agregación de subtipos de proyecto de varios niveles.

![Gráfico Visual Studio multilevel projectflavor](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Una agregación de subtipos de proyecto de varios niveles consta de tres niveles, un proyecto base, que se agrega mediante un subtipo de proyecto y, a continuación, se agrega por un subtipo de proyecto avanzado. La figura se centra en algunas de las interfaces [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] auxiliares que se proporcionan como parte de la arquitectura de subtipo según el proyecto.

### <a name="deployment-mechanisms"></a>Mecanismos de despliegue

Entre muchas de las funcionalidades del sistema de proyecto base mejoradas por un subtipo de proyecto se encuentran los mecanismos de implementación. Un subtipo de proyecto influye en los mecanismos <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>de implementación mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>implementación de interfaces de configuración (como <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> y ) que se recuperan mediante una llamada a QueryInterface en . En un escenario donde tanto el subtipo de proyecto como el subtipo `QueryInterface` de proyecto avanzado agregan `IUnknown`implementaciones de configuración diferentes, el proyecto base llama al subtipo de proyecto avanzado . Si el subtipo de proyecto interno contiene la implementación de configuración que el proyecto base está solicitando, el subtipo de proyecto avanzado delega en la implementación proporcionada por el subtipo de proyecto interno. Como mecanismo para conservar el estado de un nivel de agregación a otro, todos los niveles de subtipos de proyecto se implementan <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> para conservar los datos XML no relacionados con la compilación en los archivos de proyecto. Para obtener más información, vea [Persisting Data in the MSBuild Project File](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider>se implementa como un mecanismo para recuperar extensores de automatización de los subtipos del proyecto.

La siguiente ilustración se centra en la implementación del extensor de automatización, el objeto de exploración de configuración del proyecto en particular, utilizado por los subtipos de proyecto para ampliar el sistema de proyecto base.

![Gráfico VS Project Project Auto Extender](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Los subtipos de proyecto pueden ampliar aún más el sistema de proyecto base ampliando el modelo de objetos de automatización. Se definen como una parte del objeto de automatización DTE `ProjectItem` y `Configuration` se utilizan para extender el objeto Project, el objeto y el objeto. Para obtener más información, consulte [Ampliación del modelo de objetos del proyecto base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Agregación multinivel

Una implementación de subtipo de proyecto que envuelve un subtipo de proyecto de nivel inferior debe programarse de forma cooperativa para permitir que el subtipo de proyecto interno funcione correctamente. Una lista de responsabilidades de programación incluye:

- La <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementación del subtipo de proyecto que está <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> ajustando el subtipo interno <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> debe delegar en la implementación del subtipo de proyecto interno para ambos y métodos.

- La <xref:EnvDTE80.IInternalExtenderProvider> implementación del subtipo de proyecto contenedor debe delegar al de su subtipo de proyecto interno. En particular, la <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> implementación de necesita obtener la cadena de nombres del subtipo de proyecto interno y, a continuación, concatenar las cadenas que desea agregar como extensores.

- La <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> implementación de un subtipo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> de proyecto contenedor debe crear una instancia del objeto de su subtipo de proyecto interno y mantenerlo como un delegado privado, ya que solo el objeto de configuración del proyecto base sabe directamente que existe el objeto de configuración de subtipo del proyecto contenedor. El subtipo de proyecto externo puede elegir inicialmente interfaces de configuración que desea controlar directamente <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>y, a continuación, delegar el resto en la implementación del subtipo de proyecto interno de .

## <a name="supporting-interfaces"></a>Interfaces de apoyo

El proyecto base delega las llamadas a las interfaces de soporte agregadas por un subtipo de proyecto, para ampliar varios aspectos de su implementación. Esto incluye extender los objetos de configuración del proyecto y varios objetos del explorador de propiedades. Estas interfaces se recuperan llamando a `QueryInterface` `IUnknown` `punkOuter` (un puntero al ) del agregador de subtipo de proyecto más externo.

|Interfaz|Subtipo de proyecto|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Permite que el subtipo del proyecto:<br /><br /> - Proporcionar una <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>implementación de .<br />- Controlar el inicio del depurador permitiendo que el subtipo de proyecto proporcione su propia implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />- Deshabilitar la evaluación de expresiones en tiempo de diseño manejando adecuadamente el `DBGLAUNCH_DesignTimeExprEval` caso en su implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|
|<xref:EnvDTE80.IInternalExtenderProvider>|Permite que el subtipo del proyecto:<br /><br /> - Ampliar <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> el proyecto para añadir o eliminar propiedades independientes de configuración del proyecto.<br />- Ampliar el objeto<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject>de automatización del proyecto ( ) del proyecto.<br /><br /> Los valores de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> propiedad anteriores se toman de la enumeración.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Permite que el subtipo de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> proyecto se asigne de nuevo al objeto dado el objeto de exploración de configuración del proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Permite que el subtipo de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> proyecto `VSITEMID` se asigne de nuevo al objeto o al objeto, dado el objeto de exploración de configuración del proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Permite que el subtipo del proyecto conserve datos estructurados XML arbitrarios en el archivo de proyecto (.vbproj o .csproj). Estos datos no son visibles para MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Permite que el subtipo del proyecto:<br /><br /> - Agregar nuevas propiedades de MSBuild que se conservarán.<br />- Quitar propiedades innecesarias de MSBuild.<br />- Consulta para un valor actual de una propiedad mSBuild.<br />- Cambiar el valor actual de una propiedad MSBuild.|

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
