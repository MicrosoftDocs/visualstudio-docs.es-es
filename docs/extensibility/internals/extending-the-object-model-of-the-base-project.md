---
title: Extender el modelo de objetos del proyecto Base | Microsoft Docs
ms.date: 03/22/2018
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
ms.openlocfilehash: e746ce8bf6d109d4cd1d96c531f30106f20d9c07
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882473"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Extender el modelo de objetos del proyecto base

Un subtipo de proyecto puede extender el modelo de objetos de automatización del proyecto base en los lugares siguientes:

-   Project.Extender ("\<ProjectSubtypeName >"): Esto permite un subtipo de proyecto ofrecer un objeto con métodos personalizados desde la <xref:EnvDTE.Project> objeto. Un subtipo de proyecto puede usar extensores de automatización para exponer el `Project` objeto. El <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de proyecto principal debe ofrecer su objeto para el `VSHPROPID_ExtObjectCATID` desde <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (correspondiente a un `itemid` valor [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)) CATID.

-   ProjectItem.Extender ("\<ProjectSubtypeName >"): Esto permite ofrecer un objeto con métodos personalizados de un determinado un subtipo de proyecto <xref:EnvDTE.ProjectItem> objeto dentro del proyecto. Un subtipo de proyecto puede usar extensores de automatización para exponer este objeto. El <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de proyecto principal necesita ofrecer su objeto para el `VSHPROPID_ExtObjectCATID` desde <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondiente a un deseado <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID.

-   Project.Properties: Esta colección expone las propiedades independientes de la configuración de la `Project` objeto. Para más información sobre las propiedades de `Project`, vea <xref:EnvDTE.Project.Properties%2A>. Un subtipo de proyecto puede usar extensores de automatización para agregar sus propiedades a esta colección. El <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de proyecto principal necesita ofrecer su objeto para el `VSHPROPID_BrowseObjectCATID` desde VSHPROPID2 (correspondiente a un `itemid` valor de [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>), desde <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.

-   Configuration.Properties: Esta colección expone las propiedades dependientes de la configuración del proyecto para una configuración concreta (por ejemplo, depuración). Para obtener más información, consulta <xref:EnvDTE.Configuration>. Un subtipo de proyecto puede usar extensores de automatización para agregar sus propiedades a esta colección. El <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de proyecto principal ofrece su objeto para el CATID `VSHPROPID_CfgBrowseObjectCATID` (correspondiente a un `itemid` valor [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)). El <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>interfaz se utiliza para distinguir un objeto de examen de configuración del otro.

## <a name="see-also"></a>Vea también

<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>