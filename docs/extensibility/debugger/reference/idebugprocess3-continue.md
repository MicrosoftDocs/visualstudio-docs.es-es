---
title: IDebugProcess3::Continue | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 7
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
ms.openlocfilehash: c112a29d6b936b53aef5be5366f4066a66265e4f
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Continúa ejecutando este proceso desde un estado de detención. Se conserva un estado de ejecución anterior (por ejemplo, un paso), y el proceso empieza a ejecutarse de nuevo.  
  
> [!NOTE]
>  Este método debe utilizarse en lugar de [continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Continue(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pThread`  
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso para continuar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
## <a name="remarks"></a>Comentarios  
 Se llama a este método en este proceso sin tener en cuenta el número de procesos que se están depurando o proceso que generó el evento de detención. La implementación debe conservar el estado de ejecución anterior (por ejemplo, un paso) y continuar la ejecución como si nunca había dejado antes de completar su ejecución anterior. Es decir, si un subproceso de este proceso estaba realizando una operación de paso y se detuvo porque se detuvo de algún otro proceso y, a continuación, `Continue` se llamó, especificado subproceso debe completar la operación de paso original.  
  
 **Advertencia** no se envía ningún evento de detención o a un evento (sincrónico) inmediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) al controlar esta llamada; en caso contrario, el depurador puede dejar de responder.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
