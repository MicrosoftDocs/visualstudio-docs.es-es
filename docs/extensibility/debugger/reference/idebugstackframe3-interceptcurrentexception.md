---
title: IDebugStackFrame3::InterceptCurrentException | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d46ae2f3ae0c63c798fc42b93d50e5aee398ccf5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Llamado por el depurador en el marco de pila actual cuando quiera interceptar la excepción actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```csharp  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwFlags`  
 [in] Especifica las diferentes acciones. Actualmente, solo el [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) valor `IEA_INTERCEPT` se admite y se debe especificar.  
  
 `pqwCookie`  
 [out] Valor único que identifica una excepción determinada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
 La devolución de errores más comunes son las siguientes:  
  
|Error|Descripción|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|No se puede interceptar la excepción actual.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|El marco actual de ejecución no haya buscado en para un controlador todavía.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Este método no se admite para este marco.|  
  
## <a name="remarks"></a>Comentarios  
 Cuando se produce una excepción, el depurador toma el control de tiempo de ejecución en determinados puntos clave durante el proceso de control de excepciones. Durante estas claves instantes, el depurador puede pedir el marco de pila actual si desea que el marco interceptar la excepción. De esta manera, una excepción interceptada es básicamente un controlador de excepciones de sobre la marcha para un marco de pila, incluso si ese marco de pila no tiene un controlador de excepciones (por ejemplo, un bloque try/catch en el código de programa).  
  
 Cuando el depurador desea saber si se debe interceptar la excepción, llama a este método en el objeto de marco de pila actual. Este método es responsable de controlar todos los detalles de la excepción. Si el [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) no se implementa la interfaz o la `InterceptStackException` método devuelve un error, a continuación, el depurador continúa procesando la excepción normalmente.  
  
> [!NOTE]
>  Las excepciones se pueden interceptar solo en código administrado, es decir, cuando se ejecuta el programa que se está depurando en tiempo de ejecución de .NET. Por supuesto, pueden implementar los implementadores de lenguaje de terceros `InterceptStackException` en sus propios motores de depuración si así lo deciden.  
  
 Una vez completada, la intercepción de una [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) se señala.  
  
## <a name="see-also"></a>Vea también  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)