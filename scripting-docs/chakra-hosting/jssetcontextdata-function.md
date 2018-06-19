---
title: Función JsSetContextData | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be90aa6a-b001-4a6f-90c5-c2135e913be0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c03c34578855cf5ed6de10a43b8295a8273a4319
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568935"
---
# <a name="jssetcontextdata-function"></a>Función JsSetContextData
Establece los datos internos de JsrtContext.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsSetContextData(  
  _In_ JsContextRef context,  
  _In_ void *data  
);  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `context`  
 El contexto en el que se establecen los datos.  
  
 `data`  
 El puntero a los datos que se establecerán.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)