---
title: "CANSTOP_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CANSTOP_REASON"
helpviewer_keywords: 
  - "Enumeración CANSTOP_REASON"
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# CANSTOP_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Se utiliza para determinar si un programa puede detener la ejecución después de llegar a un punto determinado de la ejecución.  
  
## Sintaxis  
  
```cpp#  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```c#  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## Members  
 CANSTOP\_ENTRYPOINT  
 Especifica el punto de entrada del programa dado.  
  
 CANSTOP\_STEPIN  
 Especifica que entra en una función.  
  
## Comentarios  
 Pasado como argumento al método de [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) para confirmar con el administrador de depuración de la sesión \(SDM\) si es aceptable detener después de alcanzar el punto de entrada del programa o después de entrar en una función o un método.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)