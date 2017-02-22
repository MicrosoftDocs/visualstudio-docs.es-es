---
title: "StackFrameTypeEnum | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "StackFrameTypeEnum (enumeración)"
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

especifica el tipo de marco de pila.  
  
## Sintaxis  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## Elementos \(Elements\)  
 `FrameTypeFPO`  
 Puntero de capítulo omitida; Información de FPO disponibles.  
  
 `FrameTypeTrap`  
 Cuadro de Kernel.  
  
 `FrameTypeTSS`  
 Cuadro de Kernel.  
  
 `FrameTypeStandard`  
 Marco de pila estándar EBP.  
  
 `FrameTypeFrameData`  
 Puntero de capítulo omitida; Información de datos frame disponibles.  
  
 `FrameTypeUnknown`  
 Capítulo que no tiene información de depuración.  
  
## Comentarios  
 Los valores de esta enumeración son devueltos por una llamada al método de [IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) .  
  
## Requisitos  
 encabezado: cvconst.h  
  
## Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)