---
title: IDiaSession::findChildren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cca6778e5697c5f8821322c19d706d733d7f2b9f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742300"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
Recupera todos los elementos secundarios de un identificador primario especificado que coinciden con el nombre y el tipo de símbolo.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT findChildren ( 
   IDiaSymbol*       parent,
   SymTagEnum        symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parámetros
 `parent`

de Un objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el elemento primario. Si este símbolo primario es una función, módulo o bloque, se devuelven sus elementos secundarios léxicos en `ppResult`. Si el símbolo primario es un tipo, se devuelven los elementos secundarios de su clase. Si este parámetro es `NULL`, `symtag` debe establecerse en `SymTagExe` o `SymTagNull`, que devuelve el ámbito global (archivo. exe).

 `symtag`

de Especifica la etiqueta Symbol de los elementos secundarios que se van a recuperar. Los valores se toman de la enumeración de [enumeración symtagenum (](../../debugger/debug-interface-access/symtagenum.md) . Establezca en `SymTagNull` para recuperar todos los elementos secundarios.

 `name`

de Especifica el nombre de los elementos secundarios que se van a recuperar. Se establece en `NULL` para que se recuperen todos los elementos secundarios.

 `compareFlags`

de Especifica las opciones de comparación aplicadas a la coincidencia de nombres. Los valores de la enumeración [namesearchoptions (](../../debugger/debug-interface-access/namesearchoptions.md) se pueden usar solos o en combinación.

 `ppResult`

enuncia Devuelve un objeto [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) que contiene la lista de símbolos secundarios recuperados.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra cómo buscar variables locales de la función `pFunc` que coincidan con el nombre `szVarName`.

```C++
IDiaEnumSymbols* pEnum;
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );
```

## <a name="see-also"></a>Vea también
- [Información general](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeración NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)
- [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)