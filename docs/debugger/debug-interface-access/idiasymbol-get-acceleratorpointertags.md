---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f36b4bf9fdd362f4941e33745d59d481a473c607
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741112"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Devuelve todos los valores de etiqueta de puntero de acelerador que corresponden a una C++ función de código auxiliar de acelerador amp.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Parámetros
 `cnt`

de Tamaño de la matriz de salida `pPointerTags`.

 `pcnt`

enuncia Recuento de etiquetas de puntero de acelerador en la función de código auxiliar del C++ acelerador amp.

 `pPointerTags`

enuncia @No__t_0 puntero de matriz que se rellena con los valores de la etiqueta de puntero C++ de acelerador en la función de código auxiliar del acelerador amp.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.

## <a name="remarks"></a>Comentarios
 Se llama a este método en una interfaz de `IDiaSymbol` que corresponde C++ a una función de código auxiliar del acelerador amp.

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)