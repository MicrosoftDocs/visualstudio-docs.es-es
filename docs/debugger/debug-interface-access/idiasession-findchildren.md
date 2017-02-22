---
title: "IDiaSession::findChildren | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSession::findChildren (método)"
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera todos los elementos secundarios de un identificador primario especificado que coincidan con el nombre y el tipo de token.  
  
## Sintaxis  
  
```cpp#  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parámetros  
 `parent`  
 \[in\]  Un objeto de [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el elemento primario.  Si este token primario es una función, módulo, o bloque, después devuelven sus elementos secundarios léxicos en `ppResult`.  Si el token primario es un tipo, después devuelven sus derivados de la clase.  Si este parámetro es `NULL`, después `symtag` establecido en `SymTagExe` o a `SymTagNull`, que devuelve el ámbito global \(archivo .exe\).  
  
 `symtag`  
 \[in\]  Especifica la etiqueta del token de los elementos secundarios que se recuperarán.  los valores se toman de la enumeración de [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md) .  Establezca en `SymTagNull` para recuperar todos los elementos secundarios.  
  
 `name`  
 \[in\]  especifica el nombre de los elementos secundarios que se recuperarán.  Establezca en `NULL` para que todos los elementos secundarios se recuperen.  
  
 `compareFlags`  
 \[in\]  Especifica las opciones de comparación aplicado para llamar a coincidir.  Los valores de enumeración de [NameSearchOptions \(Enumeración\)](../../debugger/debug-interface-access/namesearchoptions.md) sólo se pueden utilizar o en combinación.  
  
 `ppResult`  
 \[out\]  Devuelve un objeto de [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) que contiene la lista de símbolos secundarios recuperados.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo buscar variables locales de la función `pFunc` que nombre `szVarName`match.  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## Vea también  
 [Información general](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions \(Enumeración\)](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md)