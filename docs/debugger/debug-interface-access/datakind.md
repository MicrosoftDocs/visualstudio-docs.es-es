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
ms.openlocfilehash: bf8e59bf79355b4e610091ac8662b8d2a01af322
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318685"
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
DataIsUnknown  
No se puede determinar el símbolo de datos.

DataIsLocal  
Elemento de datos es una variable local.

DataIsStaticLocal  
Elemento de datos es una variable local estática.

DataIsParam  
Elemento de datos es un parámetro formal.

DataIsObjectPtr  
Elemento de datos es un puntero de objeto (`this`).

DataIsFileStatic  
Elemento de datos es una variable con ámbito de archivo.

DataIsGlobal  
Elemento de datos es una variable global.

DataIsMember  
Elemento de datos es una variable de miembro de objeto.

DataIsStaticMember  
Elemento de datos es una variable estática de la clase.

DataIsConstant  
Elemento de datos es un valor constante.

## <a name="remarks"></a>Comentarios
Devuelven los valores de esta enumeración la [Get_datakind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: cvconst.h

## <a name="see-also"></a>Vea también
[Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
