---
title: "FRAMEINFO | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FRAMEINFO"
helpviewer_keywords: 
  - "Estructura FRAMEINFO"
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# FRAMEINFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

describe un marco de pila.  
  
## Sintaxis  
  
```cpp#  
typedef struct tagFRAMEINFO {   
   FRAMEINFO_FLAGS    m_dwValidFields;  
   BSTR               m_bstrFuncName;  
   BSTR               m_bstrReturnType;  
   BSTR               m_bstrArgs;  
   BSTR               m_bstrLanguage;  
   BSTR               m_bstrModule;  
   UINT64             m_addrMin;  
   UINT64             m_addrMax;  
   IDebugStackFrame2* m_pFrame;  
   IDebugModule2*     m_pModule;  
   BOOL               m_fHasDebugInfo;  
   BOOL               m_fStaleCode;  
   BOOL               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
```c#  
public struct FRAMEINFO {   
   public uint              m_dwValidFields;  
   public string            m_bstrFuncName;  
   public string            m_bstrReturnType;  
   public string            m_bstrArgs;  
   public string            m_bstrLanguage;  
   public string            m_bstrModule;  
   public ulong             m_addrMin;  
   public ulong             m_addrMax;  
   public IDebugStackFrame2 m_pFrame;  
   public IDebugModule2     m_pModule;  
   public int               m_fHasDebugInfo;  
   public int               m_fStaleCode;  
   public int               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
## Members  
 m\_dwValidFields  
 Una combinación de marcadores de enumeración de [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) que especifica se completan los campos.  
  
 m\_bstrFuncName  
 El nombre de función asociado al marco de pila.  
  
 m\_bstrReturnType  
 El tipo de valor devuelto asociado al marco de pila.  
  
 m\_bstrArgs  
 Los argumentos a la función asociado al marco de pila.  
  
 m\_bstrLanguage  
 El lenguaje en el que se implementa la función.  
  
 m\_bstrModule  
 El nombre del módulo asociado con el marco de pila.  
  
 m\_addrMin  
 la dirección física mínima de la pila.  
  
 m\_addrMAX  
 la dirección física máxima de la pila.  
  
 m\_pFrame  
 el objeto de [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) que representa este marco de pila.  
  
 m\_pFrame  
 el objeto de [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) que representa el módulo que contiene este marco de pila.  
  
 m\_fHasDebugInfo  
 Cero \(`TRUE`\) si la información de depuración existe en el cuadro especificado.  
  
 m\_fHasDebugInfo  
 Cero \(`TRUE`\) si el marco de pila está asociado al código que ya no es válido.  
  
 m\_fHasDebugInfo  
 Cero \(`TRUE`\) si el marco de pila es anotado por el administrador de depuración de la sesión \(SDM\).  
  
## Comentarios  
 Esta estructura se pasa al método de [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) que se completará.  Esta estructura también se contiene en una lista incluida en la interfaz de [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) que, a su vez, se devuelve de una llamada al método de [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)