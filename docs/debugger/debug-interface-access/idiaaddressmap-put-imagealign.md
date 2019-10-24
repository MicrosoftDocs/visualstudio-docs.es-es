---
title: IDiaAddressMap::put_imageAlign | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b1a6bf037dc87d84fab21622571158fb0682f60
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745048"
---
# <a name="idiaaddressmapput_imagealign"></a>IDiaAddressMap::put_imageAlign
Establece la alineación de la imagen.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT put_imageAlign ( 
   DWORD NewVal
);
```

#### <a name="parameters"></a>Parámetros
 NewVal

de Nuevo valor de alineación de imagen para el ejecutable.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Las imágenes (ejecutables cargados) se alinean con los límites de memoria especificados. Esta alineación puede verse afectada por la arquitectura actual del sistema y las opciones de tiempo de compilación y de vínculo. La alineación de la imagen siempre está en los límites de bytes. Los siguientes valores de alineación de imagen son válidos: 1, 2, 4, 8, 16, 32 y 64 bytes.

 La alineación de la imagen actual se puede recuperar con una llamada al método [IDiaAddressMap:: get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) .

> [!NOTE]
> La imagen ya se ha cargado en el momento en que se puede llamar a este método. El método `put_imageAlign` se utiliza normalmente cuando la imagen se ha cambiado o se ha cambiado y se requiere una nueva alineación.

## <a name="see-also"></a>Vea también
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)