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
ms.openlocfilehash: 4e07bdd71300ed485862a4a95f1f9cbc06b32772
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402645"
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
Establece la alineación de imagen.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT put_imageAlign ( 
   DWORD NewVal
);
```

#### <a name="parameters"></a>Parámetros
 NewVal

[in] El nuevo valor de alineación de imagen para el ejecutable.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Imágenes (cargar archivos ejecutables) se alinean en límites de memoria especificada. Esta alineación puede verse afectada por la arquitectura del sistema actual y por las opciones de tiempo de compilación y vinculación. Alineación de la imagen está siempre en límites de bytes. Los valores de alineación de imagen siguientes son válidos: límites de 1, 2, 4, 8, 16, 32 y 64 bytes.

 La alineación de imagen actual se puede recuperar con una llamada a la [Get_imagealign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) método.

> [!NOTE]
> La imagen ya está cargada en el momento en que puede llamar a este método. El `put_imageAlign` método se utiliza normalmente cuando la imagen se ha movido o cambiado y se requiere una alineación de nuevo.

## <a name="see-also"></a>Vea también
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)