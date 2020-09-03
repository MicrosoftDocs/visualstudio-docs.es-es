---
title: 'IDebugThread2:: resume | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5bdec7338864926187b3d5056ffd2f2c4e1d7824
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152991"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Reanuda la ejecución de un subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdwSuspendCount`  
 enuncia Devuelve el recuento de suspensión después de la operación de reanudación.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cada llamada a este método disminuye el recuento de suspensiones hasta que llega a 0 en el momento en el que se reanuda la ejecución. Este recuento de suspensión se muestra en la ventana de depuración de **subprocesos** .  
  
 Para cada llamada a este método, debe haber una llamada anterior al método [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) . El recuento de suspensión determina cuántas veces se ha llamado al método hasta el `IDebugThread2::Suspend` momento.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspender](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
