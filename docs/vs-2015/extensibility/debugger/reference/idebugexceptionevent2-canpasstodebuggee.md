---
title: 'IDebugExceptionEvent2:: CanPassToDebuggee | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 383287a027a75adfb4c58020675e08a46198eacf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163806"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Determina si el motor de depuración (DE) admite o no la opción de pasar esta excepción al programa que se está depurando cuando se reanuda la ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` (la excepción se puede pasar al programa) o `S_FALSE` (no se puede pasar la excepción).  
  
## <a name="remarks"></a>Observaciones  
 El DE debe tener una acción predeterminada para pasar al código depurado. El IDE puede recibir el evento [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) y llamar al método [continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) sin llamar al `CanPassToDebuggee` método. Por lo tanto, el valor DE debe tener un caso predeterminado para pasar la excepción en o no.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
