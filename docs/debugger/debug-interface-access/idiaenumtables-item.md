---
title: "IDiaEnumTables::Item | Microsoft Docs"
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
helpviewer_keywords: 
  - "IDiaEnumTables::Item (método)"
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaEnumTables::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una tabla mediante un índice o nombre.  
  
## Sintaxis  
  
```cpp#  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### Parámetros  
 `index`  
 \[in\]  índice o nombre de [IDiaTable](../../debugger/debug-interface-access/idiatable.md) que se recuperará.  Si se utiliza un tipo Variant entero, debe estar en el intervalo 0 a `count`\-1, donde es `count` que devuelve el método de [IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) .  
  
 `table`  
 \[out\]  devuelve un objeto de [IDiaTable](../../debugger/debug-interface-access/idiatable.md) que representa la tabla deseada.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Si se especifica un tipo Variant de la cadena, entonces los nombres de cadena en una tabla determinada.  el nombre debe ser uno de los nombres de tabla como definido en [Constantes \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
## Ejemplo  
  
```cpp#  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## Vea también  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Constantes \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)