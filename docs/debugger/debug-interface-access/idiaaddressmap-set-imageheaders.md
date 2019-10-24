---
title: IDiaAddressMap::set_imageHeaders | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef17e1073c67ede75d075b18773129c287349c0d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745011"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
Establece los encabezados de la imagen para habilitar la traducción de direcciones virtuales relativa.

## <a name="syntax"></a>Sintaxis

```C++
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

de Matriz de estructuras `IMAGE_SECTION_HEADER` que se van a usar como encabezados de la imagen.

 originalHeaders

de Establezca en `FALSE` si los encabezados de la imagen son de la nueva imagen, `TRUE` si reflejan la imagen original antes de una actualización. Normalmente, esto se establecería en `TRUE` solo en combinación con llamadas al método [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 La estructura de `IMAGE_SECTION_HEADER` se declara en Winnt. h y representa el formato de encabezado de la sección de imagen del archivo ejecutable.

 Los cálculos de direcciones virtuales relativas dependen de los valores de `IMAGE_SECTION_HEADER`. Normalmente, el DIA los recupera del archivo de base de datos de programa (. pdb). Si faltan estos valores, DIA no puede calcular las direcciones virtuales relativas y el método [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) devuelve `FALSE`. Después, el cliente debe llamar al método [IDiaAddressMap::P ut_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) para habilitar los cálculos de direcciones virtuales relativas después de proporcionar los encabezados de imagen que faltan de la propia imagen.

## <a name="see-also"></a>Vea también
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)