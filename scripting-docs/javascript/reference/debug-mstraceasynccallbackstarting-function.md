---
title: "Debug.msTraceAsyncCallbackStarting (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 0e2ca7c4-103c-44f2-b76c-102fb1e42543
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Debug.msTraceAsyncCallbackStarting (Funci&#243;n)
Asocia la pila de devolución de llamada a una operación asincrónica especificada anteriormente.  
  
## Sintaxis  
  
```  
Debug.msTraceAsyncCallbackStarting(asyncOperationId)  
```  
  
#### Parámetros  
 `asyncOperationId`  
 Requerido.  El identificador asociado a la operación asincrónica.  
  
## Comentarios  
 Llame a esta función en la función de devolución de llamada para la operación asincrónica después de la llamada a `Debug.msTraceAsyncOperationCompleted`.  
  
> [!NOTE]
>  Algunas herramientas de depuración no muestran la información que se envía al depurador.  
  
 `asyncOperationId` debe corresponder con el nombre de operación devuelto anteriormente desde `Debug.msTraceAsyncOperationStarting`.  
  
## Ejemplo  
 El código siguiente proporciona un ejemplo de seguimiento de una llamada asincrónica para una aplicación de la [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
```javascript  
function asyncWrapperFunction() {  
    var opID = Debug.msTraceAsyncOperationStarting('async trace');  
    doSomethingAsync().then(function (result) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_SUCCESS);  
        Debug.msTraceAsyncCallbackStarting(opID);  
        // Process result of async operation.  
    }, function (error) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_ERROR);  
        Debug.msTraceAsyncCallbackStarting(opID);  
    });  
  
    Debug.msTraceAsyncCallbackCompleted();  
}  
  
function doSomethingAsync() {  
    return WinJS.Promise.as(true);  
}  
  
asyncWrapperFunction();  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]