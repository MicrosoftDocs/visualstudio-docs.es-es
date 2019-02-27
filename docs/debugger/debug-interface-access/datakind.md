---
title: DataKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21630bea3022769d18748190c2a2d24c0e519a3c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608505"
---
# <a name="datakind"></a>DataKind
Indica el ámbito de un valor de datos determinado.

## <a name="syntax"></a>Sintaxis

```C++
enum DataKind {
    DataIsUnknown,
    DataIsLocal,
    DataIsStaticLocal,
    DataIsParam,
    DataIsObjectPtr,
    DataIsFileStatic,
    DataIsGlobal,
    DataIsMember,
    DataIsStaticMember,
    DataIsConstant
};
```

## <a name="elements"></a>Elementos
No se puede determinar el símbolo de datos DataIsUnknown.

Elemento de datos DataIsLocal es una variable local.

Elemento de datos de DataIsStaticLocal es una variable local estática.

Elemento de datos de DataIsParam es un parámetro formal.

Elemento de datos de DataIsObjectPtr es un puntero de objeto (`this`).

Elemento de datos DataIsFileStatic es una variable con ámbito de archivo.

Elemento de datos DataIsGlobal es una variable global.

Elemento de datos de DataIsMember es una variable de miembro de objeto.

Elemento de datos de DataIsStaticMember es una variable estática de la clase.

Elemento de datos DataIsConstant es un valor constante.

## <a name="remarks"></a>Comentarios
Devuelven los valores de esta enumeración la [Get_datakind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: cvconst.h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
