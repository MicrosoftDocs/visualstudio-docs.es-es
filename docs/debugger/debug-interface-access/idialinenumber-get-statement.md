---
title: IDiaLineNumber::get_statement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a37052944f74e36b488541074a0033f5b8aca9e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743132"
---
# <a name="idialinenumberget_statement"></a>IDiaLineNumber::get_statement
Recupera una marca que indica que esta información de línea describe el principio de una instrucción, en lugar de una expresión, en el origen del programa.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_statement ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

enuncia Devuelve `TRUE` si esta información de línea describe el principio de una instrucción en el origen del programa.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Las instrucciones pueden abarcar varias líneas. Este método indica si el número de línea asociado marca el principio de esta instrucción de varias líneas.

## <a name="see-also"></a>Vea también
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)