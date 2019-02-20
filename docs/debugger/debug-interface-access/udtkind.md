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
ms.openlocfilehash: bb649915179bc6e6b767970150df99caff306b4c
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317736"
---
# <a name="udtkind"></a>UdtKind
Describe la variedad de tipo definido por el usuario (UDT).

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
UdtStruct  
UDT es una estructura.

UdtClass  
UDT es una clase.

UdtUnion  
UDT es una unión.

UdtInterface  
UDT es una interfaz.

## <a name="remarks"></a>Comentarios
Devuelven los valores de esta enumeración la [Get_udtkind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: cvconst.h

## <a name="see-also"></a>Vea también
[Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
