---
title: "IDiaSymbol::get_liveRangeStartAddressSection | Microsoft Docs"
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
  - "IDiaSymbol::get_liveRangeStartAddressSection"
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_liveRangeStartAddressSection
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Devuelve la parte de la sección de la dirección inicial del intervalo en el que el símbolo local es válido.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_liveRangeStartAddressSection (   
   DWORD* section  
);  
```  
  
#### Parámetros  
 `section`  
 \[out\]  Devuelve la parte de la sección de intervalos de dirección inicial.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
> [!NOTE]
>  Un código de error devuelto indica que el token no tiene información activa del intervalo.  
  
## Comentarios  
 La dirección formada por la sección y el desplazamiento es el inicio del intervalo en el que el token es válido.  
  
 Para obtener el desplazamiento de dirección, utilice [IDiaSymbol::get\_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md).  
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia100.dll  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)