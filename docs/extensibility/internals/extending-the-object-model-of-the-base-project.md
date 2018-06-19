---
title: Extender el modelo de objetos del proyecto Base | Documentos de Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9cffbecf585f6f8be4174531a91e466f65ab9a72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130562"
---
# <a name="extending-the-object-model-of-the-base-project"></a>Extender el modelo de objetos del proyecto de Base

Un subtipo de proyecto puede extender el modelo de objetos de automatización del objeto base en los lugares siguientes:

-   Project.Extender ("\<ProjectSubtypeName >")-Esto permite un subtipo de proyecto ofrecer un objeto con métodos personalizados de la <xref:EnvDTE.Project>. Un subtipo de proyecto puede utilizar extensores de automatización para exponer la `Project` objeto. El <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de proyecto principal debe ofrecer su objeto para el `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (correspondiente a un `itemid` valo [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)) CATID.

-   ProjectItem.Extender ("\<ProjectSubtypeName >")-Esto permite un subtipo de proyecto ofrecer un objeto con métodos personalizados de un determinado <xref:EnvDTE.ProjectItem> objeto dentro del proyecto. Un subtipo de proyecto puede utilizar extensores de automatización para exponer este objeto. El <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de proyecto principal debe ofrecer su objeto para el `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondiente a un deseado <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID.

-   Esta colección de Project.Properties - expone las propiedades independientes de la configuración de la `Project` objeto. Para obtener más información sobre propiedades de proyecto, vea <xref:EnvDTE.Project.Properties%2A>. Un subtipo de proyecto puede utilizar extensores de automatización para agregar sus propiedades a esta colección. El <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de proyecto principal debe ofrecer su objeto para el `VSHPROPID_BrowseObjectCATID` de VSHPROPID2 (correspondiente a un `itemid` valo [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>), de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.

-   Configuration.Properties - en esta colección se expone las propiedades dependientes de la configuración del proyecto para una configuración concreta (por ejemplo, Debug). Para obtener más información, consulta <xref:EnvDTE.Configuration>. Un subtipo de proyecto puede utilizar extensores de automatización para agregar sus propiedades a esta colección. El <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de proyecto principal ofrece su objeto para el identificador de categoría `VSHPROPID_CfgBrowseObjectCATID` (correspondiente a un `itemid` valo [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)). El <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>interfaz se utiliza para distinguir un objeto de búsqueda de configuración de otro.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>