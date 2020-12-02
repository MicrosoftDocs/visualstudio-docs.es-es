---
title: Extender el modelo de objetos del proyecto base | Microsoft Docs
description: Obtenga información sobre cómo extender el modelo de objetos de automatización del proyecto base en Visual Studio mediante un subtipo de proyecto.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e4e3d7ad3f19aedc59288d6799e97d91499939c9
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479464"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Extender el modelo de objetos del proyecto base

Un subtipo de proyecto puede extender el modelo de objetos de automatización del proyecto base en los lugares siguientes:

- Project. extender (" \<ProjectSubtypeName> "): permite que un subtipo de proyecto ofrezca un objeto con métodos personalizados del <xref:EnvDTE.Project> objeto. Un subtipo de proyecto puede usar extensores de automatización para exponer el `Project` objeto. La <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipos de proyecto principal debe ofrecer su objeto para el `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (correspondiente a un `itemid` valor de [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)).

- ProjectItem. extender (" \<ProjectSubtypeName> "): permite que un subtipo de proyecto ofrezca un objeto con métodos personalizados de un objeto determinado <xref:EnvDTE.ProjectItem> dentro del proyecto. Un subtipo de proyecto puede usar extensores de automatización para exponer este objeto. La <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipos de proyecto principal debe ofrecer su objeto para el `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> CATID de (correspondiente a un <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> CATID).

- Project. Properties: esta colección expone las propiedades independientes de la configuración del `Project` objeto. Para más información sobre propiedades `Project`, vea <xref:EnvDTE.Project.Properties%2A>. Un subtipo de proyecto puede usar extensores de automatización para agregar sus propiedades a esta colección. La <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipos de proyecto principal debe ofrecer su objeto para el `VSHPROPID_BrowseObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondiente a un `itemid` valor de [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)).

- Configuration. Properties: esta colección expone las propiedades dependientes de la configuración del proyecto para una configuración determinada (por ejemplo, Debug). Para obtener más información, vea <xref:EnvDTE.Configuration>. Un subtipo de proyecto puede usar extensores de automatización para agregar sus propiedades a esta colección. La <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipos de proyecto principal ofrece su objeto para el CATID `VSHPROPID_CfgBrowseObjectCATID` (correspondiente a un `itemid` valor de [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). La <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> interfaz se usa para distinguir un objeto de examen de configuración de otro.

## <a name="see-also"></a>Consulte también

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
