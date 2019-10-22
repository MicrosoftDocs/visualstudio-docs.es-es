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
ms.openlocfilehash: ec5fea99994b891250dad85cfc43320848df98f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555109"
---
# <a name="cvcalle"></a>CV_call_e
Especifica la convención de llamada para una función.

> [!NOTE]
> Solo los valores de enumeración más comunes se documentan aquí. La enumeración completa está disponible en el archivo de encabezado cvconst.h.

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
CV_CALL_NEAR_C especifica una convención de llamada a función mediante una inserción casi de derecha a izquierda. La función llamada borra la pila.

Una convención de llamada de función usando un casi izquierda a derecha de inserción con registra CV_CALL_NEAR_FAST especifica. La función llamada utiliza la suma de bytes de parámetro para borrar la pila.

CV_CALL_NEAR_STD especifica una convención de llamada a función mediante una llamada estándar casi (inserción de derecha a izquierda).

Especifica CV_CALL_NEAR_SYS llamar una convención de llamada a función mediante un sistema de casi.

CV_CALL_THISCALL especifica una convención de llamada de función usando `this` llamar (`this` puntero pasa en el registro).

CV_CALL_CLRCALL especifica una convención de llamada de función utilizada por el Common Language Runtime (CLR) (también conocido como un código administrado convención de llamada).

## <a name="remarks"></a>Comentarios
Los valores de esta enumeración se devuelven mediante una llamada a la [Get_callingconvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: cvconst.h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
