---
title: "IDiaSymbol::get_liveRangeStartAddressOffset | Microsoft Docs"
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
  - "IDiaSymbol::get_liveRangeStartAddressOffset"
ms.assetid: f5b28914-0a14-4b22-8259-59d7f97ee610
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_liveRangeStartAddressOffset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Devuelve el desplazamiento de dirección inicial del intervalo en el que el símbolo local es válido.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_liveRangeStartAddressOffset (   
   DWORD* offset  
);  
```  
  
#### Parámetros  
 `offset`  
 \[out\]  Devuelve el desplazamiento de intervalo de dirección inicial.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
> [!NOTE]
>  Un código de error devuelto indica que el token no tiene información activa del intervalo.  
  
## Comentarios  
 La dirección formada por la sección y el desplazamiento es el inicio del intervalo en el que el token es válido.  
  
 Para obtener la parte de la sección de la dirección, utilice [IDiaSymbol::get\_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).  
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia100.dll  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)