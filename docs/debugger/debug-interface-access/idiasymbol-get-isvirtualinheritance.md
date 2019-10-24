---
title: IDiaSymbol::get_isVirtualInheritance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 72906b92-dd4a-42e3-9b24-b77628fa48c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7716d9688677eb12d603b208decc0f737bb1c6ca
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740009"
---
# <a name="idiasymbolget_isvirtualinheritance"></a>IDiaSymbol::get_isVirtualInheritance
Especifica si el puntero `this` apunta a un miembro de datos con herencia virtual.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_isVirtualInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

enuncia Puntero a un `BOOL` que especifica si el puntero de `this` apunta a un miembro de datos con herencia virtual.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)