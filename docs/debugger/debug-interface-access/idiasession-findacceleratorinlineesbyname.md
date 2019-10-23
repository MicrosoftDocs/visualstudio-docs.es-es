---
title: IDiaSession::findAcceleratorInlineesByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 007477d3f0de3767b0c5ef0af977f969505884ed
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742312"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Devuelve una enumeración de símbolos para los marcos insertados correspondientes al nombre de función insertada especificado.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT findAcceleratorInlineeLinesByName ( 
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parámetros
 `name`

de Nombre de la función insertada que se va a buscar.

 `option`

de Las opciones de búsqueda de nombres que se usarán al buscar fotogramas insertados que se correspondan con `name`. Para obtener más información, vea [enumeración namesearchoptions (](../../debugger/debug-interface-access/namesearchoptions.md).

 `ppResult`

enuncia Puntero a un puntero de interfaz de `IDiaEnumSymbols` que se inicializa con el resultado.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Esta función busca Inlines solo dentro de las funciones de código auxiliar de acelerador. Omite los registros de C++ procedimientos nativos.

## <a name="see-also"></a>Vea también
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)