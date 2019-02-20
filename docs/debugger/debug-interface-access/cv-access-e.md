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
ms.openlocfilehash: 2b5fa908692167b49c6bb92c892fb143b882d231
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318581"
---
# <a name="cvaccesse"></a>CV_access_e
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
CV_private  
Miembro tiene acceso privado.

CV_protected  
Miembro de acceso protegido.

CV_public  
Miembro tiene acceso público.

## <a name="remarks"></a>Comentarios
El `friend` especificador de acceso no se incluye aquí porque se usa normalmente por funciones no miembro que tienen acceso a elementos privados y protegidos de la clase. Use la [Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) método para buscar símbolos con `SymTagFriend` acceso.

## <a name="requirements"></a>Requisitos
Encabezado: cvconst.h

## <a name="see-also"></a>Vea también
[Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)  
[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
