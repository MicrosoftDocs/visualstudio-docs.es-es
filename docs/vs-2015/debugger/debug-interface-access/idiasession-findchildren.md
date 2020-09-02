---
title: IDiaSession::findChildren | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf274bb0f572da11a9aa43248da7eaa72a2e73c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150425"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera todos los elementos secundarios de un identificador primario especificado que coinciden con el nombre y el tipo de símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 de Un objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el elemento primario. Si este símbolo primario es una función, módulo o bloque, se devuelven sus elementos secundarios léxicos en `ppResult` . Si el símbolo primario es un tipo, se devuelven los elementos secundarios de su clase. Si este parámetro es `NULL` , `symtag` debe establecerse en `SymTagExe` o `SymTagNull` , que devuelve el ámbito global (archivo. exe).  
  
 `symtag`  
 de Especifica la etiqueta Symbol de los elementos secundarios que se van a recuperar. Los valores se toman de la enumeración de [enumeración symtagenum (](../../debugger/debug-interface-access/symtagenum.md) . Establezca en `SymTagNull` para recuperar todos los elementos secundarios.  
  
 `name`  
 de Especifica el nombre de los elementos secundarios que se van a recuperar. Se establece en `NULL` para todos los elementos secundarios que se van a recuperar.  
  
 `compareFlags`  
 de Especifica las opciones de comparación aplicadas a la coincidencia de nombres. Los valores de la enumeración [namesearchoptions (](../../debugger/debug-interface-access/namesearchoptions.md) se pueden usar solos o en combinación.  
  
 `ppResult`  
 enuncia Devuelve un objeto [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) que contiene la lista de símbolos secundarios recuperados.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo buscar variables locales de la función `pFunc` que coinciden con el nombre `szVarName` .  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>Consulte también  
 [Visión](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeración Namesearchoptions (](../../debugger/debug-interface-access/namesearchoptions.md)   
 [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
