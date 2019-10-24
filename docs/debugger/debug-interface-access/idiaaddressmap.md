---
title: IDiaAddressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e06acf045ce1893762d5c898752dd6bc40de50a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744988"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
Proporciona control sobre cómo el SDK de DIA calcula las direcciones virtuales virtuales y relativas para los objetos de depuración.

## <a name="syntax"></a>Sintaxis

```
IDiaAddressMap : IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDiaAddressMap`.

|Método|Descripción|
|------------|-----------------|
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Indica si se ha establecido un mapa de direcciones para una sesión determinada.|
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Especifica si se debe usar el mapa de direcciones para traducir direcciones de símbolos.|
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Indica si el cálculo y el uso de direcciones virtuales relativas están habilitadas.|
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Permite al cliente habilitar o deshabilitar el cálculo de direcciones virtuales relativas.|
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Recupera la alineación de la imagen actual.|
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Establece la alineación de la imagen.|
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Establece los encabezados de la imagen para habilitar la traducción de direcciones virtuales relativas.|
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Proporciona un mapa de direcciones para admitir las traducciones del diseño de la imagen.|

## <a name="remarks"></a>Comentarios
 El control proporcionado por esta interfaz se encapsula en dos conjuntos de datos que se proporcionan: encabezados de imagen y mapas de direcciones. La mayoría de los clientes usan el método [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) para encontrar la información de depuración adecuada para una imagen y el método normalmente puede detectar todos los encabezados necesarios y asigna los datos en sí. Sin embargo, algunos clientes implementan el procesamiento especializado y buscan datos. Estos clientes usan los métodos de la interfaz `IDiaAddressMap` para proporcionar el SDK de DIA con los resultados de la búsqueda.

## <a name="notes-for-callers"></a>Notas para llamadores
 Esta interfaz está disponible desde el objeto de sesión DIA. El cliente llama al método `QueryInterface` en la interfaz de objeto de sesión DIA, normalmente [IDiaSession](../../debugger/debug-interface-access/idiasession.md), para recuperar la interfaz `IDiaAddressMap`.

## <a name="requirements"></a>Requisitos
 Encabezado: Dia2. h

 Biblioteca: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Vea también
- [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)