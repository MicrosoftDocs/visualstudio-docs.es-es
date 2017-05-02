---
title: "Debug.msTraceAsyncOperationCompleted (Funci&#243;n) | Microsoft Docs"
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
ms.assetid: 9b628b71-61f1-478a-857f-5e1f607db56c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Debug.msTraceAsyncOperationCompleted (Funci&#243;n)
Indica que se ha completado una operación asincrónica.  
  
## Sintaxis  
  
```  
Debug.msTraceAsyncOperationCompleted(asyncOperationId, status)  
```  
  
#### Parámetros  
 `asyncOperationId`  
 Requerido.  El identificador asociado a una operación asincrónica.  
  
 `status`  
 Opcional.  El estado de la operación asincrónica.  Si no se especifica, se utiliza `Debug.MS_ASYNC_OP_STATUS_SUCCESS`.  
  
## Comentarios  
 Llame a esta función cuando se complete la operación asincrónica.  
  
 `asyncOperationId` debe corresponder al identificador de operación devuelto anteriormente desde `Debug.msTraceAsyncOperationStarting`.  
  
 Entre los posibles valores para `status` se incluyen:  
  
-   `Debug.MS_ASYNC_OP_STATUS_SUCCESS`  
  
-   `Debug.MS_ASYNC_OP_STATUS_CANCELED`  
  
-   `Debug.MS_ASYNC_OP_STATUS_ERROR`  
  
> [!NOTE]
>  Algunas herramientas de depuración no muestran la información que se envía al depurador.  
  
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