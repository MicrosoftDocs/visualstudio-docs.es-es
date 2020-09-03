---
title: Diseño de subtipos de proyecto | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706443"
---
# <a name="project-subtypes-design"></a>Diseño de subtipos de proyecto

Los subtipos de proyecto permiten a los VSPackages extender proyectos basados en el Microsoft Build Engine (MSBuild). El uso de la agregación permite volver a utilizar la mayor parte del sistema de proyectos administrados principal implementado en todavía [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] personalizar el comportamiento de un escenario determinado.

 En los temas siguientes se detalla el diseño y la implementación básicos de los subtipos de proyecto:

- Diseño del subtipo de proyecto.

- Agregación de varios niveles.

- Interfaces auxiliares.

## <a name="project-subtype-design"></a>Diseño del subtipo de proyecto

La inicialización de un subtipo de proyecto se logra agregando los <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objetos y principales <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> . Esta agregación permite a un subtipo de proyecto invalidar o mejorar la mayoría de las capacidades del proyecto base. Los subtipos de proyecto obtienen la primera oportunidad de controlar las propiedades mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , los comandos que usan <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> , y la administración de elementos de proyecto mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> . Los subtipos de proyecto también pueden extender:

- Objetos de configuración de proyecto.

- Objetos dependientes de la configuración.

- Objetos de exploración independientes de la configuración.

- Objetos de automatización del proyecto.

- Colecciones de propiedades de automatización del proyecto.

Para obtener más información sobre la extensibilidad por subtipos de proyecto, vea [propiedades y métodos extendidos por subtipos de proyecto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).

### <a name="policy-files"></a>Archivos de directivas

El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno proporciona un ejemplo de cómo extender el sistema de proyectos base con un subtipo de proyecto en su implementación de archivos de directivas. Un archivo de directiva permite la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] forma del entorno mediante la administración de características que incluyen el cuadro de diálogo explorador de soluciones, **Agregar proyecto** , **Agregar nuevo elemento** y el cuadro de diálogo **propiedades** . El subtipo de directiva invalida y mejora estas características a través <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> de las `IOleCommandTarget` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementaciones de y.

### <a name="aggregation-mechanism"></a>Mecanismo de agregación

El mecanismo de agregación de subtipos de proyecto del entorno admite varios niveles de agregación, lo que permite que se implemente un subtipo avanzado mediante la aplicación de un proyecto calificado. Además, los objetos auxiliares de un subtipo de proyecto, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> , están diseñados para permitir varios niveles de capas. Teniendo en cuenta las restricciones de las reglas de agregación COM y COM, los subtipos de proyecto y los proyectos base deben programarse de forma cooperativa para permitir que el subtipo interno o el proyecto base participen correctamente en la delegación de llamadas a métodos y la administración de recuentos de referencias. Es decir, el proyecto que se va a agregar tiene que programarse para admitir la agregación.

En la ilustración siguiente se muestra una representación esquemática de una agregación de subtipos de proyecto de varios niveles.

![Gráfico Visual Studio multilevel projectflavor](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Una agregación de subtipos de proyecto de nivel múltiple consta de tres niveles: un proyecto base, que se agrega mediante un subtipo de proyecto, y se agrega posteriormente mediante un subtipo de proyecto avanzado. La ilustración se centra en algunas de las interfaces auxiliares que se proporcionan como parte de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] arquitectura del subtipo de proyecto.

### <a name="deployment-mechanisms"></a>Mecanismos de implementación

Entre muchas de las funcionalidades del sistema de proyecto base mejoradas por un subtipo de proyecto se encuentran los mecanismos de implementación. Un subtipo de proyecto influye en los mecanismos de implementación mediante la implementación de interfaces de configuración (como <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> ) que se recuperan llamando a QueryInterface en <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> . En un escenario en el que tanto el subtipo de proyecto como el subtipo de proyecto avanzado agregan implementaciones de configuración diferentes, el proyecto base llama `QueryInterface` a en el subtipo de proyecto avanzado `IUnknown` . Si el subtipo de proyecto interno contiene la implementación de configuración que el proyecto base está solicitando, el subtipo de proyecto avanzado delega en la implementación proporcionada por el subtipo de proyecto interno. Como mecanismo para conservar el estado de un nivel de agregación a otro, todos los niveles de subtipos de proyecto implementan <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> para conservar los datos XML relacionados sin compilación en los archivos de proyecto. Para obtener más información, vea [guardar datos en el archivo de proyecto de MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> se implementa como un mecanismo para recuperar los extensores de automatización de los subtipos de proyecto.

La siguiente ilustración se centra en la implementación del extensor de automatización, el objeto de exploración de configuración del proyecto en concreto, que usan los subtipos de proyecto para extender el sistema del proyecto base.

![Gráfico VS Project Project Auto Extender](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Los subtipos de proyecto pueden ampliar aún más el sistema del proyecto base extendiendo el modelo de objetos de automatización. Se definen como parte del objeto de automatización DTE y se utilizan para extender el objeto de proyecto, el `ProjectItem` objeto y el `Configuration` objeto. Para obtener más información, vea [extender el modelo de objetos del proyecto base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Agregación de varios niveles

Una implementación de subtipo de proyecto que contiene un subtipo de proyecto de nivel inferior debe programarse de forma cooperativa para permitir que el subtipo de proyecto interno funcione correctamente. Una lista de responsabilidades de programación incluye:

- La <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementación del subtipo de proyecto que está ajustando el subtipo interno debe delegar a la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementación del subtipo de proyecto interno para los <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> métodos y.

- La <xref:EnvDTE80.IInternalExtenderProvider> implementación del subtipo de proyecto contenedor debe delegar en el de su subtipo de proyecto interno. En concreto, la implementación de <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> necesita obtener la cadena de nombres del subtipo de proyecto interno y, a continuación, concatenar las cadenas que desea agregar como objetos extender.

- La <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> implementación de un subtipo de proyecto contenedor debe crear una instancia del <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> objeto de su subtipo de proyecto interno y mantenerlo como delegado privado, ya que solo el objeto de configuración de proyecto del proyecto base sabe directamente que existe el objeto de configuración de subtipo de proyecto de contenedor. El subtipo de proyecto externo puede elegir inicialmente interfaces de configuración que desea controlar directamente y delegar el resto en la implementación del subtipo de proyecto interno de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A> .

## <a name="supporting-interfaces"></a>Interfaces auxiliares

El proyecto base delega las llamadas a las interfaces auxiliares agregadas por un subtipo de proyecto para extender varios aspectos de su implementación. Esto incluye la extensión de objetos de configuración de proyecto y varios objetos de explorador de propiedades. Estas interfaces se recuperan llamando a `QueryInterface` en `punkOuter` (un puntero a `IUnknown` ) del agregador de subtipos de proyecto más externo.

|Interfaz|Subtipo de proyecto|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Permite que el subtipo de proyecto:<br /><br /> -Proporcione una implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .<br />-Controlar el inicio del depurador permitiendo que el subtipo de proyecto proporcione su propia implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> .<br />-Deshabilite la evaluación de expresiones en tiempo de diseño controlando correctamente el `DBGLAUNCH_DesignTimeExprEval` caso en su implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A> .|
|<xref:EnvDTE80.IInternalExtenderProvider>|Permite que el subtipo de proyecto:<br /><br /> -Extienda el <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> del proyecto para agregar o quitar propiedades independientes de la configuración del proyecto.<br />-Extienda el objeto de automatización del proyecto ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject> ) del proyecto.<br /><br /> Los valores de propiedad anteriores se toman de la <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> enumeración.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Permite que el subtipo de proyecto se asigne de nuevo al <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objeto dado el objeto de exploración de configuración del proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Permite que el subtipo de proyecto se asigne de nuevo al <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> `VSITEMID` objeto o, dado el objeto de exploración de configuración del proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Permite que el subtipo de proyecto conserve los datos estructurados XML arbitrarios en el archivo de proyecto (. vbproj o. csproj). Estos datos no son visibles para MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Permite que el subtipo de proyecto:<br /><br /> -Agregue las nuevas propiedades de MSBuild que se van a conservar.<br />-Quitar propiedades innecesarias de MSBuild.<br />: Consulta para obtener un valor actual de una propiedad de MSBuild.<br />-Cambiar el valor actual de una propiedad de MSBuild.|

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
