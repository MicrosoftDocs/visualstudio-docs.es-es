---
title: IDiaAddressMap::put_addressMapEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5fe5589b667054ee75e3b01743553a2d60bef92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745063"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Especifica si se debe usar el mapa de direcciones para traducir direcciones de símbolos.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT put_addressMapEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Parámetros
 NewVal

de Establezca en `TRUE` para habilitar la traducción de símbolos o `FALSE` para deshabilitarlos.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Los postprocesadores ejecutables a veces actualizan el archivo ejecutable. DIA contiene un mecanismo para admitir la traducción de símbolos al nuevo diseño.

 Cuando se carga un archivo PDB, se habilita la asignación de direcciones almacenada en el archivo. Sin embargo, hay ocasiones en las que una aplicación cliente puede necesitar proporcionar su propio mapa de direcciones llamando al método [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) . Si el método `set_addressMap` es correcto, la aplicación cliente debe llamar al método `put_addressMapEnabled` con un parámetro `NewVal` de `TRUE` para habilitar el uso de ese mapa de direcciones.

 Se puede recuperar el estado actual del mapa de direcciones que se está habilitando con una llamada al método [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) .

## <a name="see-also"></a>Vea también
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)