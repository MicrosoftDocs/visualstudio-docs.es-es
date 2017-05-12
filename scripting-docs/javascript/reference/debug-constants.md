---
title: "Constantes DEBUG | Microsoft Docs"
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
ms.assetid: 76b572ee-bad0-404e-9fd4-841c9af35642
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Constantes DEBUG
Las constantes de depuración devuelven valores constantes que son propiedades del objeto `Debug`.  
  
## Constantes del objeto Debug  
 En la tabla siguiente se indican los valores constantes que son propiedades del [objeto Debug](../../javascript/reference/debug-object-javascript.md).  
  
|Constante|Descripción|Valor|  
|---------------|-----------------|-----------|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`|El elemento de trabajo sincrónico asignó una devolución de llamada o una continuación para que una operación asincrónica lo ejecute.|0|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`|El elemento de trabajo sincrónico satisfizo parte de una operación asincrónica de unión.|1|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`|El elemento de trabajo sincrónico satisfizo una operación asincrónica de opción.|2|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`|Se canceló el elemento de trabajo sincrónico.|3|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`|El elemento de trabajo sincrónico produjo un error en una operación asincrónica.|4|  
|`Debug.MS_ASYNC_OP_STATUS_SUCCESS`|La operación asincrónica se realizó correctamente.|1|  
|`Debug.MS_ASYNC_OP_STATUS_CANCELED`|La operación asincrónica se canceló.|2|  
|`Debug.MS_ASYNC_OP_STATUS_ERROR`|La operación asincrónica provocó un error.|3|  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vea también  
 [Debug.msTraceAsyncOperationCompleted \(Función\)](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md)   
 [Debug.msUpdateAsyncCallbackRelation \(Función\)](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md)