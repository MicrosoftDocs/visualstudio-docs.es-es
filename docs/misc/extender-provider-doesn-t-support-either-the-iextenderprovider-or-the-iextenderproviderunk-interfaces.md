---
title: "Extender Provider doesn&#39;t support either the IExtenderProvider or the IExtenderProviderUnk interfaces. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_EXT_EXTPROVINVALID"
ms.assetid: 77d596cd-28db-4ad5-bd4d-e451276e869c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Extender Provider doesn&#39;t support either the IExtenderProvider or the IExtenderProviderUnk interfaces.
El proveedor extensor no admite la interfaz implementada.  
  
### Para corregir este error  
  
1.  Implemente IExtenderProvider si el objeto Extendee admite la interfaz de automatización IDispatch.  
  
     \-O bien\-  
  
     Implemente IExtenderProviderUnk si el objeto Extendee se basa en IUnknown.  
  
## Vea también  
 <xref:EnvDTE.IExtenderProviderUnk>   
 <xref:EnvDTE.IExtenderProvider>   
 <xref:EnvDTE.ObjectExtenders>