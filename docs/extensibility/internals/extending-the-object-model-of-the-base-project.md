---
title: Ampliación del modelo de objetos del proyecto base Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33186cd477ade7f562f6191393dabe8e94f4f194
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708396"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Ampliar el modelo de objetos del proyecto base

Un subtipo de proyecto puede ampliar el modelo de objetos de automatización del proyecto base en los siguientes lugares:

- Project.Extender("\<ProjectSubtypeName>"): esto permite que un subtipo de <xref:EnvDTE.Project> proyecto ofrezca un objeto con métodos personalizados del objeto. Un subtipo de proyecto puede utilizar `Project` extensores de automatización para exponer el objeto. La <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> proyecto principal `itemid` debe ofrecer su objeto para el from (correspondiente a un valor de [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem.Extender("\<ProjectSubtypeName>"): permite que un subtipo de proyecto <xref:EnvDTE.ProjectItem> ofrezca un objeto con métodos personalizados de un objeto determinado dentro del proyecto. Un subtipo de proyecto puede utilizar extensores de automatización para exponer este objeto. La <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de `VSHPROPID_ExtObjectCATID` proyecto <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> principal debe <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>ofrecer su objeto para el CATID from (correspondiente a un deseado).

- Project.Properties: esta colección expone las propiedades `Project` independientes de la configuración del objeto. Para más información sobre propiedades `Project`, vea <xref:EnvDTE.Project.Properties%2A>. Un subtipo de proyecto puede usar Extensores de automatización para agregar sus propiedades a esta colección. La <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de `VSHPROPID_BrowseObjectCATID` proyecto <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> principal debe `itemid` ofrecer su objeto para el from (correspondiente a un valor de [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration.Properties: esta colección expone las propiedades dependientes de la configuración del proyecto para una configuración determinada (por ejemplo, Depurar). Para obtener más información, vea <xref:EnvDTE.Configuration>. Un subtipo de proyecto puede usar Extensores de automatización para agregar sus propiedades a esta colección. La <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipos de `VSHPROPID_CfgBrowseObjectCATID` proyecto principal `itemid` ofrece su objeto para el CATID (correspondiente a un valor de [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). La <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> interfaz se utiliza para distinguir un objeto de exploración de configuración de otro.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
