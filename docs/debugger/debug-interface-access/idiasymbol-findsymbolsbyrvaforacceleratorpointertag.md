---
title: 'IDiaSymbol:: findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0d05946db816e6bd209e364e11d5091163941a4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741157"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
Dado un valor de etiqueta correspondiente, este método devuelve una enumeración de símbolos contenidos en esta función de código auxiliar en una dirección virtual relativa especificada.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag (
   DWORD             tagValue,
   DWORD             rva,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Parámetros
 `tagValue`

de Valor de etiqueta de puntero para el que se encuentran los registros de símbolos de punto.

 `rva`

de RVA que se usa para filtrar los símbolos que corresponden a la variable de puntero con el valor de etiqueta especificado.

 `ppResult`

enuncia Puntero a un puntero de interfaz de `IDiaEnumSymbols` que se inicializa con el resultado.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.

## <a name="remarks"></a>Comentarios
 Llame a este método solo en una interfaz de `IDiaSymbol` que se corresponda con una función de código auxiliar de acelerador.

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)