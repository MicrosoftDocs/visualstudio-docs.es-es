---
title: "Estructura JS_NATIVE_FRAME | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_NATIVE_FRAME
apilocation: jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Estructura JS_NATIVE_FRAME
Representa un marco de pila.  
  
## Sintaxis  
  
```  
typedef struct {  
    UINT64 InstructionOffset;  
    UINT64 ReturnOffset;  
    UINT64 FrameOffset;  
    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## Miembros  
 `InstructionOffset`  
 Puntero de instrucción.  
  
 `ReturnOffset`  
 Dirección de devolución.  
  
 `FrameOffset`  
 Puntero de marco.  
  
 `StackOffset`  
 Puntero de pila.  
  
## Comentarios  
 `IJsStackFrameEnumerator` utiliza el struct `JS_NATIVE_FRAME`.  
  
## Vea también  
 [Active Script Debugger \(Constantes, enumeraciones y estructuras\)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)