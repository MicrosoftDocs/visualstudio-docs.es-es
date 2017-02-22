---
title: "IDiaSymbol::get_thunkOrdinal | Microsoft Docs"
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
  - "IDiaSymbol::get_thunkOrdinal (método)"
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera el tipo de procesador de una función.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve un valor de enumeración de [THUNK\_ORDINAL \(Enumeración\)](../../debugger/debug-interface-access/thunk-ordinal.md) que especifica el tipo de procesador de una función.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## Comentarios  
 Esta propiedad solo es válida si el símbolo como valor de [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md) de `SymTagThunk`.  
  
 Un “procesador” es un fragmento de código que convierte entre un espacio de dirección de memoria de 32 bits \(también conocido como espacio de direcciones plano\) y un espacio de direcciones de 16 bits \(conocido como espacio segmentado de direcciones\).  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [THUNK\_ORDINAL \(Enumeración\)](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md)