---
title: IDiaAddressMap::set_addressMap | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 693ecf6e8fd4f0b55936bde371b7baa6975b8f2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198652"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Proporciona un mapa de direcciones para admitir las traducciones del diseño de la imagen.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cbData`  
 de Número de elementos del `data` parámetro.  
  
 `data[]`  
 de Matriz de estructuras de [estructura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md) que definen el mapa de traslación.  
  
 `imagetoSymbols`  
 [in] `TRUE` Si el `data` parámetro define una asignación del nuevo diseño de imagen al diseño original (como se describe en los símbolos de depuración). `FALSE``data`es si es un mapa del nuevo diseño de imagen tomado del diseño original.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 Normalmente, el DIA recupera las asignaciones de traducción de direcciones del archivo de base de datos de programa (. pdb). Si faltan estos valores, se llama al método [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) dos veces, una vez con el `imagetoSymbols` parámetro establecido en `TRUE` y una vez con el `imagetoSymbols` parámetro establecido en `FALSE` . Las traducciones de mapa de direcciones no se pueden habilitar con el método [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) a menos que se proporcionen ambos mapas de traducción.  
  
## <a name="see-also"></a>Consulte también  
 [Estructura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
