---
title: IDiaLineNumber::get_compiland | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_compiland method
ms.assetid: c476d0b8-c473-47eb-96f5-c4e8f577b1c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d6ae842d4717bdc0bd989327f07d9566d1161b8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743230"
---
# <a name="idialinenumberget_compiland"></a>IDiaLineNumber::get_compiland
Recupera una referencia al símbolo de la operación de compilación que contribuyó los bytes del texto de la imagen.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_compiland ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 pRetVal

enuncia Devuelve un objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) para la operación de compilación que aportaba los bytes del texto de la imagen.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)