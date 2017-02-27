---
title: "IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dado un valor de etiqueta correspondiente, este método devuelve una enumeración de los símbolos que se contienen en una función principal especificada de código auxiliar de aceleradores en una dirección relativa virtual especificada.  
  
## Sintaxis  
  
```cpp#  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   DWORD                 rva,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### Parámetros  
 `parent`  
 \[in\] `IDiaSymbol` que corresponde a la función de código auxiliar de aceleradores que se buscará.  
  
 `tagValue`  
 \[in\] valor de etiqueta del puntero de El.  
  
 `rva`  
 \[in\] dirección virtual de relativa de El.  
  
 `ppResult`  
 \[out\] puntero A un puntero de interfaz de `IDiaEnumSymbols` inicializar con el resultado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Llame a este método solo en una interfaz de `IDiaSymbol` correspondiente a una función de código auxiliar de aceleradores.  
  
## Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)