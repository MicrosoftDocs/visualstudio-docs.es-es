---
title: "MESSAGETYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MESSAGETYPE"
helpviewer_keywords: 
  - "Enumeración MESSAGETYPE"
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# MESSAGETYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

especifica el tipo de mensaje y la razón.  
  
## Sintaxis  
  
```cpp#  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```c#  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## Members  
 MT\_OUTPUTSTRING  
 Indica que el mensaje se debe enviar a la ventana de salida.  Es mutuamente excluyentes de `MT_MESSAGEBOX`.  
  
 MT\_MESSAGEBOX  
 indica que el mensaje se debe mostrar en un cuadro de mensaje.  Es mutuamente excluyentes de `MT_OUTPUTSTRING`.  
  
 MT\_TYPE\_MASK  
 Un valor de máscara para aislar el destino del mensaje.  
  
 MT\_REASON\_EXCEPTION  
 indica que un cuadro de mensaje se está mostrando como resultado de una excepción.  Es mutuamente excluyentes de `MT_REASON_TRACEPOINT`.  
  
 MT\_REASON\_TRACEPOINT  
 Indica que un cuadro de mensaje se está mostrando como resultado de alcanzar un punto.  Es mutuamente excluyentes a `MT_REASON_EXCEPTION`.  
  
 MT\_REASON\_MASK  
 Un valor de máscara para aislar la razón del mensaje que se muestra.  
  
## Comentarios  
 estos valores se devuelven de los métodos de [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) y de [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) .  
  
 Uno de los valores de la razón se puede combinar con uno de los valores de destino de salida mediante `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)