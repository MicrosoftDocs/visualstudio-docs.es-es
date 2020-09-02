---
title: 'IDebugThread2:: GetLogicalThread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f430ea7ba69ca55bc76543d853396e22b193cf02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153059"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Los motores de depuración no implementan este método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetLogicalThread(   
   IDebugStackFrame2*     pStackFrame,  
   IDebugLogicalThread2** ppLogicalThread  
);  
```  
  
```csharp  
int GetLogicalThread(   
   IDebugStackFrame2        pStackFrame,  
   out IDebugLogicalThread2 ppLogicalThread  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pStackFrame`  
 de Un objeto [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) que representa el marco de pila.  
  
 `ppLogicalThread`  
 enuncia Devuelve una `IDebugLogicalThread2` interfaz que representa el subproceso lógico asociado. Una implementación del motor de depuración debe establecerlo en un valor null.  
  
## <a name="return-value"></a>Valor devuelto  
 Las implementaciones del motor de depuración siempre devuelven `E_NOTIMPL` .  
  
## <a name="see-also"></a>Consulte también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
