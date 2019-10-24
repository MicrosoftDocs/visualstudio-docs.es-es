---
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20b0c9dd106e5744a369ddaa6cb870788f7464d3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738551"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Especifica el tipo de marco de pila.

## <a name="syntax"></a>Sintaxis

```C++
enum StackFrameTypeEnum {
    FrameTypeFPO,
    FrameTypeTrap,
    FrameTypeTSS,
    FrameTypeStandard,
    FrameTypeFrameData,
    FrameTypeUnknown = -1
};
```

## <a name="elements"></a>Elementos
`FrameTypeFPO` puntero de marco omitido; Información de FPO disponible.

`FrameTypeTrap` marco de captura de kernel.

`FrameTypeTSS` marco de captura de kernel.

`FrameTypeStandard` marco de pila EBP estándar.

`FrameTypeFrameData` puntero de marco omitido; Información de datos de marco disponible.

`FrameTypeUnknown` marco que no tiene ninguna información de depuración.

## <a name="remarks"></a>Comentarios
Los valores de esta enumeración son devueltos por una llamada al método [IDiaStackFrame:: GET_TYPE](../../debugger/debug-interface-access/idiastackframe-get-type.md) .

## <a name="requirements"></a>Requisitos
Encabezado: cvconst. h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
