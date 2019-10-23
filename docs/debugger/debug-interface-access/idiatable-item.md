---
title: IDiaTable::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d402f5ad54d5c0f487cebb3a8c53f68d17828ed4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738724"
---
# <a name="idiatableitem"></a>IDiaTable::Item
Recupera una referencia a la entrada especificada en la tabla.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT Item ( 
   DWORD      index,
   IUnknown** element
);
```

#### <a name="parameters"></a>Parámetros
 `index`

de Índice de la entrada de tabla en el intervalo comprendido entre 0 y `count`-1, donde el método [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)devuelve `count`.

 `element`

enuncia Devuelve un objeto `IUnknown` que representa la entrada de la tabla especificada.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Una tabla representa una colección de objetos. Dependiendo de estos objetos, el parámetro de elemento se puede convertir en la interfaz adecuada. Por ejemplo, si una tabla contiene objetos [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , el parámetro Element se puede convertir a la interfaz `IDiaSegment`.

 Es un enfoque más común llamar al método `QueryInterface` de la interfaz [IDiaTable](../../debugger/debug-interface-access/idiatable.md) para la interfaz del enumerador adecuada y usar los métodos específicos del enumerador para tener acceso al contenido de la tabla. Vea la interfaz [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) para obtener un ejemplo.

## <a name="see-also"></a>Vea también
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)