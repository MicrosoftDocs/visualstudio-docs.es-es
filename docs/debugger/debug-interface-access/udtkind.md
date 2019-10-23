---
title: UdtKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45ed43bf65c38890ca7ebda1a6b1719532697eae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738442"
---
# <a name="udtkind"></a>UdtKind
Describe la variedad de tipos definidos por el usuario (UDT).

## <a name="syntax"></a>Sintaxis

```C++
enum UdtKind {
    UdtStruct,
    UdtClass,
    UdtUnion,
    UdtInterface
};
```

## <a name="elements"></a>Elementos
UdtStruct UDT es una estructura.

UdtClass UDT es una clase.

UdtUnion UDT es una Unión.

UdtInterface UDT es una interfaz.

## <a name="remarks"></a>Comentarios
El método [IDiaSymbol:: get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) devuelve los valores de esta enumeración.

## <a name="requirements"></a>Requisitos
Encabezado: cvconst. h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
