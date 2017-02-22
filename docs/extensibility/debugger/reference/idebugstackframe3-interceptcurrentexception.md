---
title: "IDebugStackFrame3::InterceptCurrentException | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame3::InterceptCurrentException"
helpviewer_keywords: 
  - "IDebugStackFrame3::InterceptCurrentException"
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Llamado por el depurador en el marco de pila actual cuando desee interceptar la excepción actual.  
  
## Sintaxis  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```c#  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### Parámetros  
 `dwFlags`  
 \[in\]  Especifica acciones diferentes.  Actualmente, sólo se `IEA_INTERCEPT` de [INTERCEPT\_EXCEPTION\_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) se admite y se debe especificar.  
  
 `pqwCookie`  
 \[out\]  valor único que identifica una excepción determinada.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
 Los siguientes son el error más común cambian.  
  
|Error|Descripción|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|La excepción actual no puede ser intercepta.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|El cuadro de ejecución actual no se haya buscado para un controlador todavía.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Este método no se admite en este cuadro.|  
  
## Comentarios  
 Cuando se produce una excepción, el control de las mejoras del depurador en tiempo de ejecución en puntos clave durante excepciones proceso.  En estos momentos clave, el depurador puede pedir al marco de pila actual si el cuadro desea interceptar la excepción.  De esta manera, una excepción intercepta es esencialmente controlador de excepciones en estado para un marco de pila, aunque ese marco de pila no tiene un controlador de excepciones \(por ejemplo, un bloque try\/catch en código de programa\).  
  
 Cuando el depurador desea saber si se intercepta la excepción, llama a este método en el objeto de marco de pila.  este método es responsable de administrar todos los detalles de la excepción.  Si la interfaz de [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) no se implementa o el método de `InterceptStackException` devuelve cualquier error, el depurador continúa procesando la excepción normalmente.  
  
> [!NOTE]
>  Las excepciones se pueden interceptar sólo en código administrado, es decir, cuando el programa que se está depurando se ejecuta en tiempo de ejecución.NET.  Por supuesto, los implementadores de terceros de lenguaje pueden implementar `InterceptStackException` en sus propios motores de depuración si elija hacerlo.  
  
 Una vez completada la interceptación, se designa [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) .  
  
## Vea también  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT\_EXCEPTION\_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)