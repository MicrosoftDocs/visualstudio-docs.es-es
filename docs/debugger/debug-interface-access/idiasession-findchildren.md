---
title: Findchildren | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 16033fc289e5a1fe2a8331e927bba51ce1671fd2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896177"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
Recupera a todos los elementos secundarios de un identificador de elemento primario especificado que coinciden con el tipo de nombre y el símbolo.  
  
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
 [in] Un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa el elemento primario. Si este símbolo primario es una función, un módulo o un bloque, a continuación, se devuelven sus elementos secundarios léxicos en `ppResult`. Si el símbolo de elemento primario es un tipo, se devuelven sus elementos secundarios de la clase. Si este parámetro es `NULL`, a continuación, `symtag` debe establecerse en `SymTagExe` o `SymTagNull`, que devuelve el ámbito global (archivo .exe).  
  
 `symtag`  
 [in] Especifica la etiqueta del símbolo de los elementos secundarios van a recuperar. Los valores se toman de la [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) enumeración. Establecido en `SymTagNull` para recuperar todos los elementos secundarios.  
  
 `name`  
 [in] Especifica el nombre de los elementos secundarios van a recuperar. Establecido en `NULL` todos los elementos secundarios van a recuperar.  
  
 `compareFlags`  
 [in] Especifica las opciones de comparación que se aplica a la coincidencia de nombres. Los valores de la [NameSearchOptions (enumeración)](../../debugger/debug-interface-access/namesearchoptions.md) enumeración puede usarse por sí solo o en combinación.  
  
 `ppResult`  
 [out] Devuelve un [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) recupera el objeto que contiene la lista de símbolos secundarios.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo buscar las variables locales de función `pFunc` ese nombre coincidencia `szVarName`.  
  
```C++  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>Vea también  
 [Información general](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions (enumeración)](../../debugger/debug-interface-access/namesearchoptions.md)   
 [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)