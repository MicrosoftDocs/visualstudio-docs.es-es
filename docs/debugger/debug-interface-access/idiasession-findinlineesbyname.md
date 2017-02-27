---
title: "IDiaSession::findInlineesByName | Microsoft Docs"
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
ms.assetid: 9860336d-f703-4ecb-bfc4-3f5beb175a76
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findInlineesByName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una enumeración que permite que un cliente recorra la información de número de línea de todas las funciones inline que coinciden con el nombre especificado.  
  
## Sintaxis  
  
```cpp#  
HRESULT findInlineesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parámetros  
 `name`  
 \[in\] especifica el nombre para utilizar para la comparación.  
  
 `option`  
 \[in\] especifica las opciones de comparación aplicado para llamar a buscar.  Los valores de enumeración de [NameSearchOptions \(Enumeración\)](../../debugger/debug-interface-access/namesearchoptions.md) sólo se pueden utilizar o en combinación.  
  
 `ppResult`  
 \[out\] devuelve un objeto de [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) que contiene una lista de los números de línea que se recuperaron.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)