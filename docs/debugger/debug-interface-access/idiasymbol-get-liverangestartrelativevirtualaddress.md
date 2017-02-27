---
title: "IDiaSymbol::get_liveRangeStartRelativeVirtualAddress | Microsoft Docs"
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
  - "IDiaSymbol::get_liveRangeStartRelativeVirtualAddress"
ms.assetid: 1da52539-9872-4c20-8eaa-74b6cb5f3b02
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Devuelve el inicio del intervalo del que el símbolo local es válido.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_liveRangeStartRelativeVirtualAddress (   
   DWORD* address  
);  
```  
  
#### Parámetros  
 `address`  
 \[out\]  Devuelve el inicio del intervalo de direcciones.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  La dirección relativa virtual devuelto es el principio del intervalo en el que el token es válido.  
  
> [!NOTE]
>  Un código de error devuelto indica que el token no tiene información activa del intervalo.  
  
## Comentarios  
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia100.dll  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)