---
title: Extender el modelo de objetos del proyecto base | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7723881bce81824b66a936793175077a0ec67666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187164"
---
# <a name="extending-the-object-model-of-the-base-project"></a>Ampliación del modelo de objetos del proyecto de base
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un subtipo de proyecto puede extender el modelo de objetos de automatización del proyecto base en los lugares siguientes:  
  
- Project. extender (" \<ProjectSubtypeName> "): permite que un subtipo de proyecto ofrezca un objeto con métodos personalizados de <xref:EnvDTE.Project> . Un subtipo de proyecto puede usar extensores de automatización para exponer el `Project` objeto. La <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipos de proyecto principal debe ofrecer su objeto para el `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (correspondiente a un `itemid` valor de VSITEMID_ROOT, de `VSITEMID` ) CATID.  
  
- ProjectItem. extender (" \<ProjectSubtypeName> "): permite que un subtipo de proyecto ofrezca un objeto con métodos personalizados de un objeto determinado <xref:EnvDTE.ProjectItem> dentro del proyecto. Un subtipo de proyecto puede usar extensores de automatización para exponer este objeto. La <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipos de proyecto principal debe ofrecer su objeto para el `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> CATID de (correspondiente a un `VSITEMID` CATID).  
  
- Project. Properties: esta colección expone las propiedades independientes de la configuración del `Project` objeto. Para obtener más información sobre las propiedades del proyecto, vea <xref:EnvDTE.Project.Properties%2A> . Un subtipo de proyecto puede usar extensores de automatización para agregar sus propiedades a esta colección. La <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipos de proyecto principal debe ofrecer su objeto para la `VSHPROPID_BrowseObjectCATID` desde VSHPROPID2 (correspondiente a un `itemid` valor de VSITEMID_ROOT, de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> ) CATID.  
  
- Configuration. Properties: esta colección expone las propiedades dependientes de configuración del proyecto para una configuración determinada (por ejemplo, Debug). Para obtener más información, consulte <xref:EnvDTE.Configuration>. Un subtipo de proyecto puede usar extensores de automatización para agregar sus propiedades a esta colección. La <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipos de proyecto principal ofrece su objeto para el CATID `VSHPROPID_CfgBrowseObjectCATID` (correspondiente a un `itemid` valor de <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> ). La <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> interfaz se usa para distinguir un objeto de examen de configuración de otro.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
