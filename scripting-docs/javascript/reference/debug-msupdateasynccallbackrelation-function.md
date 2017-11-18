---
title: "Debug.msUpdateAsyncCallbackRelation (función) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee6a1efc-375c-4ce8-a4e8-8896ee29f849
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c47ed7f6313646dddf86dd766d7f1027b2d38ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="debugmsupdateasynccallbackrelation-function"></a>Debug.msUpdateAsyncCallbackRelation (Función)
Actualiza el estado de la relación entre un elemento de trabajo sincrónico y la operación asincrónica asociada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.msUpdateAsyncCallbackRelation(relatedAsyncOperationId, relationType)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `relatedAsyncOperationId`  
 Obligatorio. El identificador asociado a la operación asincrónica.  
  
 `relationType`  
 Opcional. El valor que especifica el estado de la relación.  
  
## <a name="remarks"></a>Comentarios  
 El elemento de trabajo sincrónico es normalmente la función de devolución de llamada de la operación asincrónica. Esta función se puede llamar cuando se anula una operación asincrónica, cuando se usa una operación de combinación o en otros escenarios.  
  
 Entre los posibles valores para `relationType` se incluyen:  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`  
  
 Para obtener más información, consulte [constantes de depuración](../../javascript/reference/debug-constants.md).  
  
> [!NOTE]
>  Algunas herramientas de depuración no muestran la información enviada al depurador por esta función.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]