---
title: "IDiaSymbol::get_framePointerPresent | Microsoft Docs"
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
  - "IDiaSymbol::get_framePointerPresent (método)"
ms.assetid: d036090a-1651-454d-9130-b798f58ba053
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDiaSymbol::get_framePointerPresent
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un indicador que especifica si el puntero de marco está presente.  Utilice cuando [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md) se establece en `SymTagFunction`.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_framePointerPresent(   
   BOOL* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  \] Devuelve `TRUE` si el puntero de marco presente; de lo contrario, devuelve `FALSE`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## Comentarios  
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia100.dll  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)