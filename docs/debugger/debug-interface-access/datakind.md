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
ms.openlocfilehash: 31be0615fd7d1da279ecf414260af21cb8239dc8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745287"
---
# <a name="datakind"></a>DataKind
Indica el ámbito determinado de un valor de datos.

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

El elemento de datos DataIsLocal es una variable local.

El elemento de datos DataIsStaticLocal es una variable local estática.

El elemento de datos DataIsParam es un parámetro formal.

El elemento de datos DataIsObjectPtr es un puntero de objeto (`this`).

El elemento de datos DataIsFileStatic es una variable de ámbito de archivo.

El elemento de datos DataIsGlobal es una variable global.

El elemento de datos DataIsMember es una variable de miembro de objeto.

El elemento de datos DataIsStaticMember es una variable estática de clase.

El elemento de datos DataIsConstant es un valor constante.

## <a name="remarks"></a>Comentarios
El método [IDiaSymbol:: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) devuelve los valores de esta enumeración.

## <a name="requirements"></a>Requisitos
Encabezado: cvconst. h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
