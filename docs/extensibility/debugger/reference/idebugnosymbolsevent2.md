---
title: "IDebugNoSymbolsEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugNoSymbolsEvent2"
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugNoSymbolsEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Señala la interfaz de usuario del depurador de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] de advertir al usuario que los símbolos no se puede encontrar para el ejecutable iniciada.  
  
## Sintaxis  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## Notas para los implementadores  
 Implementado por los motores de depuración y usado por la interfaz de usuario del depurador de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .  
  
## Requisitos  
 encabezado: Msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll