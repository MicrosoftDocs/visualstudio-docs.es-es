---
title: Debug.msTraceAsyncOperationStarting (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c8458264-07e0-4cd6-8528-ff7cf009cf9e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a50c58e352d40a06192664cdf7424348be02d466
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636275"
---
# <a name="debugmstraceasyncoperationstarting-function"></a>Debug.msTraceAsyncOperationStarting (Función)
Inicia un seguimiento de una operación asincrónica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.msTraceAsyncOperationStarting(operationName)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `operationName`  
 Obligatorio. Cadena que identifica la operación asincrónica. Si `operationName` es null o undefined, se usa una cadena vacía como nombre de la operación.  
  
## <a name="return-value"></a>Valor devuelto  
 Entero que representa el identificador de operación.  
  
## <a name="remarks"></a>Comentarios  
 Llame a este método antes de que se inicie la operación asincrónica.  
  
> [!NOTE]
>  Algunas herramientas de depuración no muestran la información que se envía al depurador.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente proporciona un ejemplo de instrumentación de una llamada asincrónica para una aplicación de la [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
```JavaScript  
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
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]