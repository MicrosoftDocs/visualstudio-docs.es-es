---
title: Set_addressmap | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1d097ccbe5c893c603aaa2a018f8fcd422f15ac2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834536"
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
Proporciona un mapa de direcciones para admitir las traducciones de diseño de imagen.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cbData`  
 [in] El número de elementos de la `data` parámetro.  
  
 `data[]`  
 [in] Una matriz de [DiaAddressMapEntry estructura](../../debugger/debug-interface-access/diaaddressmapentry.md) estructuras que definen la asignación de traducción.  
  
 `imagetoSymbols`  
 [in] `TRUE` si el `data` parámetro define una asignación desde el nuevo diseño de la imagen al diseño original (como se describe en los símbolos de depuración). `FALSE` Si `data` es un mapa para el nuevo diseño de imagen procedente del diseño original.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, el DIA recupera asignaciones de traducción de direcciones desde el archivo de programa (.pdb) de la base de datos. Si faltan estos valores, el [Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) se llama al método dos veces, una vez con el `imagetoSymbols` parámetro establecido en `TRUE` y una vez con el `imagetoSymbols` parámetro establecido en `FALSE`. Traducciones de asignación de direcciones no pueden habilitarse mediante la [Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) método a menos que se proporcionan ambos mapas de traducción.  
  
## <a name="see-also"></a>Vea también  
 [DiaAddressMapEntry estructura](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)