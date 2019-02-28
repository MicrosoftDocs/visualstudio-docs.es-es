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
ms.openlocfilehash: 397873a65176024327f371e9727b15984cd7d03f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56632113"
---
# <a name="idialinenumbergetstatement"></a>IDiaLineNumber::get_statement
Recupera una marca que indica que esta información de línea describe el principio de una instrucción, en lugar de una expresión, en el código fuente del programa.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_statement ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

[out] Devuelve `TRUE` si esta información de línea describe al principio de una instrucción en el código fuente del programa.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Las instrucciones pueden abarcar varias líneas. Este método indica si el número de línea asociado marca el principio de este tipo en una instrucción multilínea.

## <a name="see-also"></a>Vea también
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)