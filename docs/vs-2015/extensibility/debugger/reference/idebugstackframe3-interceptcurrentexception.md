---
title: 'IDebugStackFrame3:: Interceptcurrentexception (| Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42472690431d48a9baafbb0abee27c1a07d24fcd
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "91403859"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Lo llama el depurador en el marco de pila actual cuando desea interceptar la excepción actual.  
  
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
 de Especifica acciones diferentes. Actualmente, solo se admite el valor [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) `IEA_INTERCEPT` y se debe especificar.  
  
 `pqwCookie`  
 enuncia Valor único que identifica una excepción determinada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.  
  
 A continuación se devuelven los errores más comunes.  
  
|Error|Descripción|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|No se puede interceptar la excepción actual.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Todavía no se ha buscado un controlador en el marco de ejecución actual.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Este método no es compatible con este marco.|  
  
## <a name="remarks"></a>Observaciones  
 Cuando se produce una excepción, el depurador obtiene el control del tiempo de ejecución en los puntos clave durante el proceso de control de excepciones. Durante estos momentos clave, el depurador puede preguntar al marco de pila actual si el marco desea interceptar la excepción. De esta manera, una excepción interceptada es esencialmente un controlador de excepciones en la marcha para un marco de pila, incluso si ese marco de pila no tiene un controlador de excepciones (por ejemplo, un bloque try/catch en el código del programa).  
  
 Cuando el depurador desea saber si se debe interceptar la excepción, llama a este método en el objeto de marco de pila actual. Este método es responsable de controlar todos los detalles de la excepción. Si no se implementa la interfaz [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) o el `InterceptStackException` método devuelve un error, el depurador continúa procesando la excepción con normalidad.  
  
> [!NOTE]
> Las excepciones solo se pueden interceptar en código administrado, es decir, cuando el programa que se está depurando se está ejecutando en el tiempo de ejecución de .NET. Por supuesto, los implementadores de lenguaje de terceros pueden implementar `InterceptStackException` en sus propios motores de depuración si así lo desean.  
  
 Una vez completada la intercepción, se señala un [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) .  
  
## <a name="see-also"></a>Vea también  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
