---
title: Extender el modelo de objetos del proyecto Base | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: db8ec193b49b7b72e922d2e4f715061d78be37ad
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783290"
---
# <a name="extending-the-object-model-of-the-base-project"></a>Ampliación del modelo de objetos del proyecto de base
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un subtipo de proyecto puede extender el modelo de objetos de automatización del proyecto base en los lugares siguientes:  
  
-   Project.Extender ("\<ProjectSubtypeName >"): Esto permite un subtipo de proyecto ofrecer un objeto con métodos personalizados desde el <xref:EnvDTE.Project>. Un subtipo de proyecto puede usar extensores de automatización para exponer el `Project` objeto. El <xref:EnvDTE80.IInternalExtenderProvider>interfaz implementada en el agregador de subtipo de proyecto principal debe ofrecer su objeto para el `VSHPROPID_ExtObjectCATID` desde <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (correspondiente a un `itemid` VSITEMID_ROOT, valor de `VSITEMID`) CATID.  
  
-   ProjectItem.Extender ("\<ProjectSubtypeName >"): Esto permite ofrecer un objeto con métodos personalizados de un determinado un subtipo de proyecto <xref:EnvDTE.ProjectItem> objeto dentro del proyecto. Un subtipo de proyecto puede usar extensores de automatización para exponer este objeto. El <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de proyecto principal necesita ofrecer su objeto para el `VSHPROPID_ExtObjectCATID` desde <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondiente a un deseado `VSITEMID`) CATID.  
  
-   Esta colección de Project.Properties: expone las propiedades independientes de la configuración de la `Project` objeto. Para obtener más información sobre las propiedades del proyecto, vea <xref:EnvDTE.Project.Properties%2A>. Un subtipo de proyecto puede usar extensores de automatización para agregar sus propiedades a esta colección. El <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de proyecto principal necesita ofrecer su objeto para el `VSHPROPID_BrowseObjectCATID` desde VSHPROPID2 (correspondiente a un `itemid` valor VSITEMID_ROOT, desde <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.  
  
-   Configuration.Properties: en esta colección se expone las propiedades dependientes de la configuración del proyecto para una configuración concreta (por ejemplo, depuración). Para obtener más información, consulte <xref:EnvDTE.Configuration>. Un subtipo de proyecto puede usar extensores de automatización para agregar sus propiedades a esta colección. El <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de proyecto principal ofrece su objeto para el CATID `VSHPROPID_CfgBrowseObjectCATID` (correspondiente a un `itemid` valor <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>). El <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>interfaz se utiliza para distinguir un objeto de examen de configuración del otro.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>

