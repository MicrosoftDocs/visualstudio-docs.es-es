---
title: IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs
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
ms.openlocfilehash: 673ca8137244fed933df0be3fa0221115951a9c1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618112"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
Dado un valor de la etiqueta correspondiente, este método devuelve una enumeración de los símbolos que se encuentran en esta función de código auxiliar en una dirección virtual relativa especificada.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag (
   DWORD             tagValue,
   DWORD             rva,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Parámetros
 `tagValue`

[in] El valor de etiqueta de puntero para el que se encuentran los registros de símbolos el puntero.

 `rva`

[in] La rva que se utiliza para filtrar los símbolos que corresponden a la variable el puntero con el valor de etiqueta especificado.

 `ppResult`

[out] Un puntero a un `IDiaEnumSymbols` puntero de interfaz que se inicializa con el resultado.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.

## <a name="remarks"></a>Comentarios
 Llame a este método solo en un `IDiaSymbol` interfaz que corresponde a una función de código auxiliar del acelerador.

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)