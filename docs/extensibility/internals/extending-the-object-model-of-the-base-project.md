---
title: Extender el modelo de objetos del proyecto Base | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b92fe7fece58dd2006507f0285d3c440af437ee4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-object-model-of-the-base-project"></a>Extender el modelo de objetos del proyecto de Base
Un subtipo de proyecto puede extender el modelo de objetos de automatización del objeto base en los lugares siguientes:  
  
-   Project.Extender ("\<ProjectSubtypeName >")-Esto permite un subtipo de proyecto ofrecer un objeto con métodos personalizados de la <xref:EnvDTE.Project>. Un subtipo de proyecto puede utilizar extensores de automatización para exponer la `Project` objeto. El <xref:EnvDTE80.IInternalExtenderProvider>interfaz implementada en el agregador de subtipo de proyecto principal debe ofrecer su objeto para el `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (correspondiente a un `itemid` valo VSITEMID_ROOT, de `VSITEMID`) CATID.  
  
-   ProjectItem.Extender ("\<ProjectSubtypeName >")-Esto permite un subtipo de proyecto ofrecer un objeto con métodos personalizados de un determinado <xref:EnvDTE.ProjectItem> objeto dentro del proyecto. Un subtipo de proyecto puede utilizar extensores de automatización para exponer este objeto. El <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de proyecto principal debe ofrecer su objeto para el `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondiente a un deseado `VSITEMID`) CATID.  
  
-   Esta colección de Project.Properties - expone las propiedades independientes de la configuración de la `Project` objeto. Para obtener más información sobre propiedades de proyecto, vea <xref:EnvDTE.Project.Properties%2A>. Un subtipo de proyecto puede utilizar extensores de automatización para agregar sus propiedades a esta colección. El <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de proyecto principal debe ofrecer su objeto para el `VSHPROPID_BrowseObjectCATID` de VSHPROPID2 (correspondiente a un `itemid` valo VSITEMID_ROOT, de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.  
  
-   Configuration.Properties - en esta colección se expone las propiedades dependientes de la configuración del proyecto para una configuración concreta (por ejemplo, Debug). Para obtener más información, consulte <xref:EnvDTE.Configuration>. Un subtipo de proyecto puede utilizar extensores de automatización para agregar sus propiedades a esta colección. El <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de proyecto principal ofrece su objeto para el identificador de categoría `VSHPROPID_CfgBrowseObjectCATID` (correspondiente a un `itemid` valo <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>). El <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>interfaz se utiliza para distinguir un objeto de búsqueda de configuración de otro.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>