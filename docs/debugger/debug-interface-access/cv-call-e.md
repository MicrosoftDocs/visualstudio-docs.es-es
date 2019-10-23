---
title: CV_call_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5deb59d4bbee06e505ba10bf1d4f08b1b06aa62d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745354"
---
# <a name="cv_call_e"></a>CV_call_e
Especifica la Convención de llamada para una función.

> [!NOTE]
> Aquí solo se documentan los valores de enumeración más comunes. La enumeración complete está disponible en el archivo de encabezado cvconst. h.

## <a name="syntax"></a>Sintaxis

```C++
typedef enum CV_call_e {
    CV_CALL_NEAR_C    = 0x00,
    CV_CALL_NEAR_FAST = 0x04,
    CV_CALL_NEAR_STD  = 0x07,
    CV_CALL_NEAR_SYS  = 0x09,
    CV_CALL_THISCALL  = 0x0b,
    CV_CALL_CLRCALL   = 0x16
} CV_call_e;
```

## <a name="elements"></a>Elementos
CV_CALL_NEAR_C especifica una Convención de llamada de función mediante una inserciones casi de derecha a izquierda. La función de llamada borra la pila.

CV_CALL_NEAR_FAST especifica una Convención de llamada de función mediante una inserciones casi de izquierda a derecha con registros. La función llamada usa la suma de bytes de parámetro para borrar la pila.

CV_CALL_NEAR_STD especifica una Convención de llamada de función mediante una llamada casi estándar (inserciones de derecha a izquierda).

CV_CALL_NEAR_SYS especifica una Convención de llamada de función mediante una llamada al sistema cercana.

CV_CALL_THISCALL especifica una Convención de llamada de función mediante `this` llamada (el puntero `this` pasado en el registro).

CV_CALL_CLRCALL especifica una Convención de llamada de función utilizada por Common Language Runtime (CLR) (también conocida como Convención de llamada a código administrado).

## <a name="remarks"></a>Comentarios
Los valores de esta enumeración son devueltos por una llamada al método [IDiaSymbol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) .

## <a name="requirements"></a>Requisitos
Encabezado: cvconst. h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
