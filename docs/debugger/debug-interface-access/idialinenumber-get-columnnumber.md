---
title: IDiaLineNumber::get_columnNumber | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumber method
ms.assetid: e317f29a-6525-46a7-8421-33985392f8fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ac6eea93daf9b0ef7d8169a4f765c249f3b9ee4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743256"
---
# <a name="idialinenumberget_columnnumber"></a>IDiaLineNumber::get_columnNumber
Recupera el número de columna donde comienza la expresión o instrucción.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT get_columnNumber ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

enuncia Devuelve el número de columna donde comienza la expresión o instrucción. Si el valor es cero, la información de la columna no está presente.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 El valor de columna devuelto por este método es un desplazamiento de bytes en la línea hasta el primer carácter de la instrucción de la línea.

## <a name="see-also"></a>Vea también
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)