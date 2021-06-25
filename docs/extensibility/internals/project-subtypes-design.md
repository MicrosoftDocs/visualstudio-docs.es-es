---
title: Diseño de subtipos de proyecto | Microsoft Docs
description: Obtenga información sobre cómo los subtipos de proyecto permiten a los VSPackages ampliar los proyectos en función de Microsoft Build Engine (MSBuild).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c04c8e681646aed6816c645defe7ffd87ac7033c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899698"
---
# <a name="project-subtypes-design"></a>Diseño de subtipos de proyecto

Los subtipos de proyecto permiten a los VSPackages ampliar los proyectos en función Microsoft Build Engine (MSBuild). El uso de agregación le permite reutilizar la mayor parte del sistema de proyectos administrados principal implementado en y, sin embargo, personalizar el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comportamiento para un escenario determinado.

 En los temas siguientes se detalla el diseño básico y la implementación de subtipos de proyecto:

- Diseño de subtipo de proyecto.

- Agregación de varios niveles.

- Interfaces de compatibilidad.

## <a name="project-subtype-design"></a>Diseño de subtipos de proyecto

La inicialización de un subtipo de proyecto se logra agregando los objetos <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> main y <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> . Esta agregación permite que un subtipo de proyecto invalide o mejore la mayoría de las funcionalidades del proyecto base. Los subtipos de proyecto obtienen la primera oportunidad de controlar las propiedades mediante , comandos mediante y , y la administración <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> de elementos de proyecto mediante <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> . Los subtipos de proyecto también pueden ampliar:

- Objetos de configuración del proyecto.

- Objetos dependientes de la configuración.

- Objetos de exploración independientes de la configuración.

- Objetos de automatización de proyectos.

- Colecciones de propiedades de automatización de proyectos.

Para obtener más información sobre la extensibilidad por subtipos de proyecto, vea [Propiedades y métodos extendidos por subtipos de proyecto.](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

### <a name="policy-files"></a>Archivos de directivas

El entorno proporciona un ejemplo de ampliación del sistema de proyectos base con un subtipo de proyecto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en su implementación de archivos de directiva. Un archivo de directiva permite dar forma al entorno mediante la administración de características que incluyen el Explorador de soluciones, el cuadro de diálogo Agregar proyecto, el cuadro de diálogo Agregar nuevo elemento y el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]  cuadro **de** diálogo Propiedades .  El subtipo de directiva invalida y mejora estas características a través <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> de las `IOleCommandTarget` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementaciones , y .

### <a name="aggregation-mechanism"></a>Mecanismo de agregación

El mecanismo de agregación de subtipos de proyecto del entorno admite varios niveles de agregación, lo que permite implementar un subtipo avanzado mediante el control adicional de un proyecto con tipo. Además, los objetos compatibles de un subtipo de proyecto, como , están diseñados para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> permitir varios niveles de capas. De acuerdo con las restricciones de las reglas de agregación COM y COM, los subtipos de proyecto y los proyectos base deben programarse de forma cooperativa para permitir que el subtipo interno o el proyecto base participen correctamente en la delegación de llamadas a métodos y la administración de recuentos de referencias. Es decir, el proyecto que está a punto de agregarse debe programarse para admitir la agregación.

En la ilustración siguiente se muestra una representación esquemática de una agregación de subtipo de proyecto de varios niveles.

![Gráfico Visual Studio multilevel projectflavor](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Una agregación de subtipo de proyecto de varios niveles consta de tres niveles, un proyecto base, que se agrega mediante un subtipo de proyecto y, a continuación, se agrega mediante un subtipo de proyecto avanzado. La ilustración se centra en algunas de las interfaces compatibles que se proporcionan como parte de la arquitectura [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de subtipo del proyecto.

### <a name="deployment-mechanisms"></a>Mecanismos de implementación

Entre muchas de las funcionalidades del sistema de proyecto base mejoradas por un subtipo de proyecto se encuentran los mecanismos de implementación. Un subtipo de proyecto influye en los mecanismos de implementación mediante la implementación de interfaces de configuración (como y ) que se recuperan mediante una llamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> a QueryInterface en <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> . En un escenario en el que el subtipo de proyecto y el subtipo de proyecto avanzado agregan implementaciones de configuración diferentes, el proyecto base llama a en el `QueryInterface` subtipo de proyecto `IUnknown` avanzado. Si el subtipo de proyecto interno contiene la implementación de configuración que el proyecto base solicita, el subtipo de proyecto avanzado delega en la implementación proporcionada por el subtipo de proyecto interno. Como mecanismo para conservar el estado de un nivel de agregación a otro, todos los niveles de subtipos de proyecto implementan para conservar datos XML no relacionados con la compilación en los archivos <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> del proyecto. Para obtener más información, vea [Conservar datos en el archivo de proyecto de MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> se implementa como un mecanismo para recuperar extensores de automatización de los subtipos del proyecto.

La siguiente ilustración se centra en la implementación del extensor de automatización, el objeto de exploración de la configuración del proyecto en particular, que usan los subtipos de proyecto para ampliar el sistema de proyecto base.

![Gráfico VS Project Project Auto Extender](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Los subtipos de proyecto pueden ampliar aún más el sistema de proyectos base mediante la ampliación del modelo de objetos de automatización. Se definen como parte del objeto de automatización de DTE y se usan para extender el objeto Project, el objeto `ProjectItem` y el `Configuration` objeto . Para obtener más información, vea [Extender el modelo de objetos del proyecto base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Agregación de varios niveles

Una implementación de subtipo de proyecto que encapsula un subtipo de proyecto de nivel inferior debe programarse de forma cooperativa para permitir que el subtipo de proyecto interno funcione correctamente. Una lista de responsabilidades de programación incluye:

- La implementación del subtipo de proyecto que encapsula el subtipo interno debe delegar en la implementación del subtipo de proyecto interno <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> para los métodos y <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> .

- La <xref:EnvDTE80.IInternalExtenderProvider> implementación del subtipo de proyecto contenedor debe delegar en el de su subtipo de proyecto interno. En concreto, la implementación de debe obtener la cadena de nombres del subtipo de proyecto interno y, a continuación, concatenar las cadenas que quiere <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> agregar como extensores.

- La implementación de un subtipo de proyecto contenedor debe crear una instancia del objeto de su subtipo de proyecto interno y contenerlo como delegado privado, ya que solo el objeto de configuración del proyecto base sabe directamente que el objeto de configuración del subtipo del proyecto contenedor <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> existe. El subtipo de proyecto externo puede elegir inicialmente las interfaces de configuración que quiere controlar directamente y, a continuación, delegar el resto en la implementación del subtipo de proyecto interno de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A> .

## <a name="supporting-interfaces"></a>Interfaces de compatibilidad

El proyecto base delega las llamadas a interfaces de compatibilidad agregadas por un subtipo de proyecto para ampliar varios aspectos de su implementación. Esto incluye la extensión de objetos de configuración del proyecto y varios objetos del explorador de propiedades. Estas interfaces se recuperan llamando a en (un puntero a ) del `QueryInterface` `punkOuter` `IUnknown` agregador de subtipo de proyecto más externo.

|Interfaz|Subtipo de proyecto|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Permite que el subtipo del proyecto:<br /><br /> : proporcione una implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .<br />- Controlar el inicio del depurador permitiendo que el subtipo de proyecto proporcione su propia implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> .<br />- Deshabilite la evaluación de expresiones en tiempo de diseño controlando adecuadamente `DBGLAUNCH_DesignTimeExprEval` el caso en su implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A> .|
|<xref:EnvDTE80.IInternalExtenderProvider>|Permite que el subtipo del proyecto:<br /><br /> - Amplíe el <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> del proyecto para agregar o quitar propiedades independientes de la configuración del proyecto.<br />- Extender el objeto de automatización del proyecto ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject> ) del proyecto.<br /><br /> Los valores de propiedad anteriores se toman de la <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> enumeración .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Permite que el subtipo de proyecto vuelva a asignarse al <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objeto dado el objeto de exploración de configuración del proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Permite que el subtipo de proyecto vuelva a asignarse al objeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> o , dado el objeto de exploración de configuración del `VSITEMID` proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Permite que el subtipo de proyecto conserve datos estructurados XML arbitrarios en el archivo de proyecto (.vbproj o .csproj). Estos datos no son visibles para MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Permite que el subtipo del proyecto:<br /><br /> - Agregar nuevas propiedades de MSBuild que se conservarán.<br />- Quitar propiedades innecesarias de MSBuild.<br />: consulta un valor actual de una propiedad de MSBuild.<br />: cambia el valor actual de una propiedad de MSBuild.|

## <a name="see-also"></a>Consulte también

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
