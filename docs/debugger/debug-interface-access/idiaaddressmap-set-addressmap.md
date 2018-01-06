---
title: 'Idiaaddressmap:: Set_addressmap | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 681e0bae46497d9b581e89340069937370831777
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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
 [in] `TRUE` si el `data` parámetro define una asignación desde el nuevo diseño de imagen al diseño original (como se describe en los símbolos de depuración). `FALSE`Si `data` es un mapa para el nuevo diseño de imagen que se toma del diseño original.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, el DIA recupera asignaciones de traducción de direcciones desde el archivo de programa (.pdb) de la base de datos. Si faltan estos valores, el [idiaaddressmap:: Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) método se llama dos veces, una vez con la `imagetoSymbols` parámetro establecido en `TRUE` y una vez con la `imagetoSymbols` parámetro establecido en `FALSE`. Traducciones de asignación de direcciones no se puede habilitar mediante el [idiaaddressmap:: Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) método a menos que se proporcionan dos asignaciones de traducción.  
  
## <a name="see-also"></a>Vea también  
 [DiaAddressMapEntry estructura](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)