---
title: "Función JsSetIndexedPropertiesToExternalData | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cee2d86d-ed42-4acb-86ef-95a67e63d0d6
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7180c5e233cfd5e448bc9f0d3eb1895e5dfd4aa8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jssetindexedpropertiestoexternaldata-function"></a>Función JsSetIndexedPropertiesToExternalData
Establece las propiedades indizadas de un objeto en datos externos. Los datos externos se utilizarán como almacén de reserva para las propiedades indizadas del objeto y se accederá a ellos como una matriz con tipo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsSetIndexedPropertiesToExternalData(  
   _In_ JsValueRef object,  
   _In_ void* data,  
   _In_ JsTypedArrayType arrayType,  
   _In_ unsigned int elementLength  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 El objeto en el que se va a trabajar.  
  
 `data`  
 Los datos externos que se utilizarán como almacén de reserva para las propiedades del objeto indizado.  
  
 `arrayType`  
 El tipo de elemento de matriz en los datos externos.  
  
 `elementLength`  
 El número de elementos de matriz en los datos externos.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
 Esta API solo es compatible en modo perimetral.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)