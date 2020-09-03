---
title: IDiaAddressMap::set_imageHeaders | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18fa69929f78d5ae661169a09db97697d98f4d94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198639"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Establece los encabezados de la imagen para habilitar la traducción de direcciones virtuales relativa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 cbData  
 de Número de bytes de datos de encabezado. Debe ser `n*sizeof(IMAGE_SECTION_HEADER)` donde `n` es el número de encabezados de sección del archivo ejecutable.  
  
 data[]  
 de Matriz de  `IMAGE_SECTION_HEADER` estructuras que se va a usar como encabezado de la imagen.  
  
 originalHeaders  
 de Se establece en `FALSE` si los encabezados de la imagen son de la nueva imagen, `TRUE` si reflejan la imagen original antes de una actualización. Normalmente, esto se establecería en `TRUE` solo en combinación con llamadas al método [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La `IMAGE_SECTION_HEADER` estructura se declara en Winnt. h y representa el formato del encabezado de la sección de la imagen del archivo ejecutable.  
  
 Los cálculos de direcciones virtuales relativas dependen de los `IMAGE_SECTION_HEADER` valores. Normalmente, el DIA los recupera del archivo de base de datos de programa (. pdb). Si faltan estos valores, DIA no puede calcular las direcciones virtuales relativas y el método [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) devuelve `FALSE` . Después, el cliente debe llamar al método [IDiaAddressMap::p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) para habilitar los cálculos de direcciones virtuales relativas después de proporcionar los encabezados de imagen que faltan de la propia imagen.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)
