---
title: Función JsHasIndexedPropertiesExternalData | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c676db20-3ef1-4f84-8b26-3e06fe0ab2bf
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3907d3122974c3081f2a33e84a7f70ee9308c7e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568265"
---
# <a name="jshasindexedpropertiesexternaldata-function"></a>Función JsHasIndexedPropertiesExternalData
Determina si un objeto tiene sus propiedades indizadas en datos externos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsHasIndexedPropertiesExternalData(  
   _In_ JsValueRef object,  
   _Out_ bool* value  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 El objeto.  
  
 `value`  
 Si el objeto tiene o no sus propiedades indizadas en datos externos.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Esta API solo es compatible en modo perimetral.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)