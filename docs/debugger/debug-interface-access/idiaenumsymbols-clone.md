---
title: IDiaEnumSymbols::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Clone method
ms.assetid: 5c542025-98cf-4307-901f-b9430f780cf0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07e3823a62ca6fdb81fa6916eec6a1de5598a748
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743988"
---
# <a name="idiaenumsymbolsclone"></a>IDiaEnumSymbols::Clone
Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT Clone ( 
   IDiaEnumSymbols** ppenum
);
```

#### <a name="parameters"></a>Parámetros
 ppenum

enuncia Devuelve un objeto [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) que contiene un duplicado del enumerador. Los símbolos no están duplicados, solo el enumerador.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)