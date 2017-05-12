---
title: "Debug.msUpdateAsyncCallbackRelation (Funci&#243;n) | Microsoft Docs"
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
ms.assetid: ee6a1efc-375c-4ce8-a4e8-8896ee29f849
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Debug.msUpdateAsyncCallbackRelation (Funci&#243;n)
Actualiza el estado de la relación entre un elemento de trabajo sincrónico y la operación asincrónica asociada.  
  
## Sintaxis  
  
```  
Debug.msUpdateAsyncCallbackRelation(relatedAsyncOperationId, relationType)  
```  
  
#### Parámetros  
 `relatedAsyncOperationId`  
 Requerido.  El identificador asociado a la operación asincrónica.  
  
 `relationType`  
 Opcional.  El valor que especifica el estado de la relación.  
  
## Comentarios  
 El elemento de trabajo sincrónico es normalmente la función de devolución de llamada de la operación asincrónica.  Esta función se puede llamar cuando se anula una operación asincrónica, cuando se usa una operación de combinación o en otros escenarios.  
  
 Entre los posibles valores para `relationType` se incluyen:  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`  
  
 Para obtener más información, vea [Constantes de depuración](../../javascript/reference/debug-constants.md).  
  
> [!NOTE]
>  Algunas herramientas de depuración no muestran la información enviada al depurador por esta función.  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]