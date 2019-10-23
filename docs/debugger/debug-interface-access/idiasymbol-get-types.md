---
title: IDiaSymbol::get_types | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d23ea3c4d885b3f7575c998999814d0808d03bc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739053"
---
# <a name="idiasymbolget_types"></a>IDiaSymbol::get_types
Recupera una matriz de tipos específicos del compilador para este símbolo.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_types ( 
   DWORD       cTypes,
   DWORD*      pcTypes,
   IDiaSymbol* types[]
);
```

#### <a name="parameters"></a>Parámetros
 `cTypes`

de Tamaño del búfer que va a contener los datos.

 `pcTypes`

enuncia Devuelve el número de tipos escritos, o bien, si el parámetro `types` es `NULL`, entonces el número total de tipos disponibles.

 `types[]`

enuncia Matriz que se va a rellenar con los objetos [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representan todos los tipos de este símbolo.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)