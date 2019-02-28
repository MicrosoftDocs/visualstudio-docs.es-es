---
title: IDiaSectionContrib::get_nopad | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_nopad method
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51fb2c4ff2f27cee8fcc989139f5ae14c2641394
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642149"
---
# <a name="idiasectioncontribgetnopad"></a>IDiaSectionContrib::get_nopad
Recupera una marca que indica si la sección debe no se rellenan hasta completar el siguiente límite de memoria.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_nopad(
   BOOL* pRetVal
};
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

[out] Devuelve `TRUE` si no se debe controlar la sección en el siguiente límite de memoria; en caso contrario, devuelve `FALSE`.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Se trata de una propiedad suele aparecer sólo en los archivos antiguos.

## <a name="see-also"></a>Vea también
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)