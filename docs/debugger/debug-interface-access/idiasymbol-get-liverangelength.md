---
title: "IDiaSymbol::get_liveRangeLength | Microsoft Docs"
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
  - "IDiaSymbol::get_liveRangeLength"
ms.assetid: ffcce3cc-085c-44eb-8145-46e3819c54f9
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaSymbol::get_liveRangeLength
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Devuelve la longitud del intervalo de dirección en el que el símbolo local es válido.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_liveRangeLength (   
   ULONGLONG* length  
);  
```  
  
#### Parámetros  
 `length`  
 \[out\]  Devuelve la longitud del intervalo de direcciones.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
> [!NOTE]
>  Un código de error devuelto indica que el token no tiene información activa del intervalo.  
  
## Comentarios  
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia100.dll  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)