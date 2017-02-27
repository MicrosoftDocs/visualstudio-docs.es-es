---
title: "Extender el modelo de objetos del proyecto de Base | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modelo de objetos de automatización, extender"
  - "subtipos de proyecto, extender el modelo de objetos de automatización"
  - "modelo de objetos de automatización"
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Extender el modelo de objetos del proyecto de Base
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un subtipo de proyecto puede extender el modelo de objetos de automatización del objeto base en los lugares siguientes:  
  
-   Project.Extender ("\< ProjectSubtypeName>"): Esto permite un subtipo de proyecto ofrecer un objeto con métodos personalizados desde el <xref:EnvDTE.Project>. Un subtipo de proyecto puede utilizar extensores de automatización para exponer la `Project` objeto. El <xref:EnvDTE80.IInternalExtenderProvider>interfaz implementada en el agregador de subtipo de proyecto principal debe ofrecer su objeto para el `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (correspondiente a un `itemid` valo VSITEMID_ROOT, de `VSITEMID`) CATID.  
  
-   ProjectItem.Extender ("\< ProjectSubtypeName>"): Esto permite un subtipo de proyecto ofrecer un objeto con métodos personalizados de un determinado <xref:EnvDTE.ProjectItem> objeto dentro del proyecto. Un subtipo de proyecto puede utilizar extensores de automatización para exponer este objeto. El <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de proyecto principal debe ofrecer su objeto para el `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondiente a un deseado `VSITEMID`) CATID.  
  
-   Esta colección de Project.Properties: expone las propiedades independientes de la configuración de la `Project` objeto. Para obtener más información sobre propiedades de proyecto, vea <xref:EnvDTE.Project.Properties%2A>. Un subtipo de proyecto puede utilizar extensores de automatización para agregar sus propiedades a esta colección. El <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de proyecto principal debe ofrecer su objeto para el `VSHPROPID_BrowseObjectCATID` de VSHPROPID2 (correspondiente a un `itemid` valo VSITEMID_ROOT, de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.  
  
-   Configuration.Properties: en esta colección se expone las propiedades dependientes de la configuración del proyecto para una configuración concreta (por ejemplo, Debug). Para obtener más información, vea <xref:EnvDTE.Configuration>. Un subtipo de proyecto puede utilizar extensores de automatización para agregar sus propiedades a esta colección. El <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada en el agregador de subtipo de proyecto principal ofrece su objeto para el identificador de CATEGORÍA `VSHPROPID_CfgBrowseObjectCATID` (correspondiente a un `itemid` valo <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>). El <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>interfaz se utiliza para distinguir un objeto de búsqueda de configuración de otro.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>