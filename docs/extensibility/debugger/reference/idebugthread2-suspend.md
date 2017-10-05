---
title: IDebugThread2::Suspend | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 3926456c8b625102dfc5df4d8818f3cacc3a2ce3
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Suspende un subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Suspend (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
HRESULT Suspend (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdwSuspendCount`  
 [out] Devuelve el recuento de suspensión después de la operación de suspensión.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cada llamada a este método aumenta el recuento de suspensión superior a 0. Este recuento de suspensión se muestra en el **subprocesos** ventana de depuración.  
  
 Para cada llamada a este método, debe haber una llamada posterior a la [reanudar](../../../extensibility/debugger/reference/idebugthread2-resume.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)
