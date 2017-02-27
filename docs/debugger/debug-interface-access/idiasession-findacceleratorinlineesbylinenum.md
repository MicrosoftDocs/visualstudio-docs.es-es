---
title: "IDiaSession::findAcceleratorInlineesByLinenum | Microsoft Docs"
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
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findAcceleratorInlineesByLinenum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Devuelve una enumeración de los símbolos para los marcos de punto flotante que corresponden a la ubicación especificada del origen.  
  
## Sintaxis  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   IDiaSymbol*           parent,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 colnum,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parámetros  
 `parent`  
 \[in\] `IDiaSymbol` que corresponde a la función de código auxiliar de aceleradores que necesita ser buscada.  
  
 `file`  
 \[in\] `IDiaSourceFile` de la ubicación de origen.  
  
 `linenum`  
 \[in\] número de línea de la ubicación de origen.  
  
 `colnum`  
 \[in\] número de columnas de la ubicación de origen.  
  
 `ppResult`  
 \[out\] puntero A un puntero de interfaz de `IDiaEnumLineNumbers` inicializar con el resultado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)