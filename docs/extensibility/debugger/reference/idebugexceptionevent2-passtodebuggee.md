---
title: IDebugExceptionEvent2::PassToDebuggee | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords: IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d10f01289fc0a5733586e19bb3b584fa0f95f4aa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Especifica si la excepción se debería pasar al programa que se está depurando cuando se reanuda la ejecución, o si se debería descartar la excepción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fPass`  
 [in] Es distinto de cero (`TRUE`) si la excepción se debería pasar al programa que se está depurando cuando se reanuda la ejecución, o cero (`FALSE`) si se debería descartar la excepción.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Llamar a este método no hacer que cualquier código que se ejecuta en el programa que se está depurando. La llamada consiste simplemente en establecer el estado para la ejecución del código siguiente. Por ejemplo, se llama a la [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) método puede devolver `S_OK` con el [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` campo establecido en `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 El IDE puede recibir el [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) eventos y llame al método el [continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md) método. El motor de depuración (Alemania) debe tener un comportamiento predeterminado para controlar el caso si la `PassToDebuggee` no se llama el método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)