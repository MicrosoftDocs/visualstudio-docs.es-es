---
title: Función JsGetDataViewStorage | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 7c2180e0-51d5-4cc8-ad21-8bf29ff7c583
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b405fc22e411c343dcd5214495deb0275f5db52
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568125"
---
# <a name="jsgetdataviewstorage-function"></a>Función JsGetDataViewStorage
Obtiene el almacenamiento de memoria subyacente utilizado por un `DataView`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
STDAPI_(JsErrorCode) JsGetDataViewStorage(  
   _In_ JsValueRef dataView,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dataView`  
 La instancia de DataView.  
  
 `buffer`  
 El búfer de DataView. La duración del búfer devuelto es la misma que la duración del `DataView`. El puntero de búfer no se considera una referencia al `DataView` para la recolección de elementos no utilizados.  
  
 `bufferLength`  
 El número de bytes en el búfer.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
 Esta API solo es compatible en modo perimetral.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)