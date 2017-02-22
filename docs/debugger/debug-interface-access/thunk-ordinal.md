---
title: "THUNK_ORDINAL | Microsoft Docs"
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
  - "Thunk_Ordinal (enumeración)"
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# THUNK_ORDINAL
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Seleccione tipos del procesador.  
  
## Sintaxis  
  
```cpp#  
typedef enum THUNK_ORDINAL {   
   THUNK_ORDINAL_NOTYPE,  
   THUNK_ORDINAL_ADJUSTOR,  
   THUNK_ORDINAL_VCALL,  
   THUNK_ORDINAL_PCODE,  
   THUNK_ORDINAL_LOAD   
  
   // trampoline thunk ordinals - only for use in Trampoline thunk symbols  
   THUNK_ORDINAL_TRAMP_INCREMENTAL,  
   THUNK_ORDINAL_TRAMP_BRANCHISLAND,  
} THUNK_ORDINAL;  
```  
  
## Elementos \(Elements\)  
 THUNK\_ORDINAL\_NOTYPE  
 procesador estándar.  
  
 THUNK\_ORDINAL\_ADJUSTOR  
 Un procesador de ajustador de `this` .  
  
 THUNK\_ORDINAL\_VCALL  
 Procesador de llamada virtual.  
  
 THUNK\_ORDINAL\_PCODE  
 procesador de P\-código.  
  
 THUNK\_ORDINAL\_LOAD  
 Procesador de carga retrasada.  
  
 THUNK\_ORDINAL\_TRAMP\_INCREMENTAL  
 Procesador incremental de trampolín \(un procesador de trampolín se utiliza para devolver llamadas de un espacio de memoria a otro\).  
  
 THUNK\_ORDINAL\_TRAMP\_BRANCHISLAND  
 Procesador de trampolín de punto de bifurcación.  
  
## Comentarios  
 Los valores de esta enumeración se devuelven de una llamada al método de [IDiaSymbol::get\_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) .  
  
## Requisitos  
 encabezado: cvconst.h  
  
## Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)