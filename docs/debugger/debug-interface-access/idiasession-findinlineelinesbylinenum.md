---
title: "IDiaSession::findInlineeLinesByLinenum | Microsoft Docs"
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
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findInlineeLinesByLinenum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una enumeración que permite que un cliente recorra la información de número de línea de todas las funciones que inline, directa o indirectamente, del archivo de código fuente y el número de línea especificados.  
  
## Sintaxis  
  
```cpp#  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 column,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parámetros  
 `compiland`  
 \[in\] objeto de [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el compilando en el que buscar los números de línea.  Este parámetro no puede ser `NULL`.  
  
 `file`  
 \[in\] objeto de [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) que representa el archivo de código fuente en el cual buscar.  Este parámetro no puede ser `NULL`.  
  
 `linenum`  
 \[in\] especifica un número de línea basada en uno.  
  
> [!NOTE]
>  No puede utilizar cero para especificar todas las líneas \(utilice el método de [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md) para buscar todas las líneas\).  
  
 `column`  
 \[in\] especifica el número de columnas.  Uso cero de especificar todas las columnas.  Una columna es un desplazamiento de bytes en una línea.  
  
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