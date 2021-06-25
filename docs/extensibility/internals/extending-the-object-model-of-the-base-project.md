---
title: Extender el modelo de objetos del proyecto base | Microsoft Docs
description: Obtenga información sobre cómo extender el modelo de objetos de automatización del proyecto base Visual Studio mediante un subtipo de proyecto.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 175571b374c6a54999b212b316301f3f775891ff
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899347"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Extensión del modelo de objetos del proyecto base

Un subtipo de proyecto puede extender el modelo de objetos de automatización del proyecto base en los siguientes lugares:

- Project.Extender(" "): permite que un subtipo de proyecto \<ProjectSubtypeName> ofrezca un objeto con métodos personalizados del objeto <xref:EnvDTE.Project> . Un subtipo de proyecto puede usar extensores de Automation para exponer el `Project` objeto. La interfaz implementada en el agregador de subtipos del proyecto principal debe ofrecer su objeto para el de (correspondiente a un <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_ExtObjectCATID` valor de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> `itemid` [VSITEMID. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem.Extender(" "): permite que un subtipo de proyecto ofrezca un objeto con métodos personalizados \<ProjectSubtypeName> de un objeto determinado dentro del <xref:EnvDTE.ProjectItem> proyecto. Un subtipo de proyecto puede usar extensores de automatización para exponer este objeto. La interfaz implementada en el agregador de subtipo de proyecto principal debe ofrecer su objeto para el CATID de <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondiente a <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> un elemento CATID deseado).

- Project.Properties: esta colección expone las propiedades independientes de la configuración del `Project` objeto . Para más información sobre propiedades `Project`, vea <xref:EnvDTE.Project.Properties%2A>. Un subtipo de proyecto puede usar extensores de Automation para agregar sus propiedades a esta colección. La interfaz implementada en el agregador de subtipos del proyecto principal debe ofrecer su objeto para el de (correspondiente a un <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_BrowseObjectCATID` valor de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> `itemid` [VSITEMID. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration.Properties: esta colección expone las propiedades dependientes de la configuración del proyecto para una configuración determinada (por ejemplo, Depurar). Para más información, consulte <xref:EnvDTE.Configuration>. Un subtipo de proyecto puede usar extensores de Automation para agregar sus propiedades a esta colección. La interfaz implementada en el agregador de subtipo de proyecto principal ofrece su objeto <xref:EnvDTE80.IInternalExtenderProvider> para el CATID (correspondiente a un valor de `VSHPROPID_CfgBrowseObjectCATID` `itemid` [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). La <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> interfaz se usa para distinguir un objeto de exploración de configuración de otro.

## <a name="see-also"></a>Consulte también

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
