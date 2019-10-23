---
title: IDiaFrameData::get_program | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 135f2b0a042dd74b573a0746831a48fb27e7c2a9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743521"
---
# <a name="idiaframedataget_program"></a>IDiaFrameData::get_program
Recupera la cadena de programa que se usa para calcular el conjunto de registros antes de la llamada a la función actual.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_program ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

enuncia Devuelve la cadena de programa.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 La cadena de programa es una secuencia de macros que se interpreta para establecer el prólogo. Por ejemplo, un marco de pila típico podría usar la cadena de programa `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. El formato es la notación de polaco inversa, donde los operadores siguen los operandos. `T0` representa una variable temporal en la pila. En este ejemplo se realizan los pasos siguientes:

1. Mueva el contenido de la `ebp` de registro a `T0`.

2. Agregue `4` al valor de `T0` para generar una dirección, obtener el valor de esa dirección y almacenar el valor en el registro `eip`.

3. Obtiene el valor de la dirección almacenada en `T0` y almacena ese valor en el registro `ebp`.

4. Agregue `8` al valor de `T0` y almacene ese valor en el `esp` de registro.

   Tenga en cuenta que la cadena de programa es específica de la CPU y de la Convención de llamada configurada para la función representada por el marco de pila actual.

## <a name="see-also"></a>Vea también
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)