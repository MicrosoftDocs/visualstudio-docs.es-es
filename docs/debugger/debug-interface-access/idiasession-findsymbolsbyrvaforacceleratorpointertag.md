---
title: 'IDiaSession:: findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb1b24d24de35de30b24937a6cfbf59d12f69482
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742001"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
Dado un valor de etiqueta correspondiente, este método devuelve una enumeración de símbolos contenidos en una función de código auxiliar de acelerador primaria especificada en una dirección virtual relativa especificada.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   DWORD                 rva,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parámetros
 `parent`

de @No__t_0 que corresponde a la función de código auxiliar de acelerador que se va a buscar.

 `tagValue`

de Valor de la etiqueta de puntero.

 `rva`

de Dirección virtual relativa.

 `ppResult`

enuncia Puntero a un puntero de interfaz de `IDiaEnumSymbols` que se inicializa con el resultado.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Llame a este método solo en una interfaz de `IDiaSymbol` que se corresponda con una función de código auxiliar de acelerador.

## <a name="see-also"></a>Vea también
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)