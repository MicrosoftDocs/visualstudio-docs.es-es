---
title: FRAMEINFO | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FRAMEINFO
helpviewer_keywords: FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 31f87c5261db32e19c9382d4d9cd95f4081cbe19
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="frameinfo"></a>FRAMEINFO
Describe un marco de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
  
```csharp  
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
  
## <a name="members"></a>Miembros  
 m_dwValidFields  
 Una combinación de indicadores de la [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) enumeración que especifica qué campos se rellenen.  
  
 m_bstrFuncName  
 El nombre de función asociado con el marco de pila.  
  
 m_bstrReturnType  
 El tipo de valor devuelto asociado con el marco de pila.  
  
 m_bstrArgs  
 Los argumentos a la función asociada con el marco de pila.  
  
 m_bstrLanguage  
 El idioma en el que se implementa la función.  
  
 m_bstrModule  
 El nombre de módulo asociado con el marco de pila.  
  
 m_addrMin  
 La dirección de pila física mínima.  
  
 m_addrMAX  
 La dirección de pila física máximo.  
  
 m_pFrame  
 El [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) objeto que representa este marco de pila.  
  
 m_pFrame  
 El [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) objeto que representa el módulo que contiene este marco de pila.  
  
 m_fHasDebugInfo  
 Es distinto de cero (`TRUE`) si no existe información de depuración en el periodo especificado.  
  
 m_fHasDebugInfo  
 Es distinto de cero (`TRUE`) si el marco de pila está asociado con el código que ya no es válido.  
  
 m_fHasDebugInfo  
 Es distinto de cero (`TRUE`) si el marco de pila se anota por el Administrador de sesión de depuración (SDM).  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura se pasa a la [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) método que deben rellenarse. Esta estructura también está incluida en una lista que se encuentra en la [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfaz que, a su vez, se devuelve de una llamada a la [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)