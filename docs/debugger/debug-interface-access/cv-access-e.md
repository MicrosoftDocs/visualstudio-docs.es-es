---
title: CV_access_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbe338ba9d3aa6cbc795606c3fa285526afdfd36
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745368"
---
# <a name="cv_access_e"></a>CV_access_e
Especifica el ámbito de visibilidad (nivel de acceso) de las funciones miembro y variables.

## <a name="syntax"></a>Sintaxis

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>Elementos
El miembro CV_private tiene acceso privado.

El miembro CV_protected tiene acceso protegido.

El miembro CV_public tiene acceso público.

## <a name="remarks"></a>Comentarios
El especificador de acceso `friend` no se incluye aquí porque normalmente lo usan las funciones no miembro que tienen acceso a los elementos privados y protegidos de la clase. Use el método [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) para buscar símbolos con acceso `SymTagFriend`.

## <a name="requirements"></a>Requisitos
Encabezado: cvconst. h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
