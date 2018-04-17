---
title: EXCEPTION_INFO | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c48772ed5835daeff9d47773e6e48526993fa425
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="exceptioninfo"></a>EXCEPTION_INFO
Describe una excepción o error de tiempo de ejecución que se produce por el programa que se está depurando.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```csharp  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## <a name="members"></a>Miembros  
 pProgram  
 El [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa el programa en el que se produjo la excepción.  
  
 bstrProgramName  
 El nombre del programa en el que se produjo la excepción.  
  
 bstrExceptionName  
 El nombre de la excepción.  
  
 dwCode  
 El código de identificación para el error de excepción o tiempo de ejecución.  
  
 "_mfc_CTabCtrl.3a3a.GetItem"  
 Un valor de la [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) enumeración que define el estado de la excepción.  
  
 guidType  
 El identificador de idioma GUID, ya sea `guidLang` o `guidEng`.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura se pasa como un parámetro a la [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) y [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) métodos. Esta estructura también se pasa a la [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) método que deben rellenarse.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)