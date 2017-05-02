---
title: "Debug.msTraceAsyncOperationStarting (Funci&#243;n) | Microsoft Docs"
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
ms.assetid: c8458264-07e0-4cd6-8528-ff7cf009cf9e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Debug.msTraceAsyncOperationStarting (Funci&#243;n)
Inicia un seguimiento de una operación asincrónica.  
  
## Sintaxis  
  
```  
Debug.msTraceAsyncOperationStarting(operationName)  
```  
  
#### Parámetros  
 `operationName`  
 Requerido.  Cadena que identifica la operación asincrónica.  Si `operationName` es null o undefined, se usa una cadena vacía como nombre de la operación.  
  
## Valor devuelto  
 Entero que representa el identificador de operación.  
  
## Comentarios  
 Llame a este método antes de que se inicie la operación asincrónica.  
  
> [!NOTE]
>  Algunas herramientas de depuración no muestran la información que se envía al depurador.  
  
## Ejemplo  
 El código siguiente proporciona un ejemplo de instrumentación de una llamada asincrónica para una aplicación de la [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
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