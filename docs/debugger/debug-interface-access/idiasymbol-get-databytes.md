---
title: "IDiaSymbol::get_dataBytes | Microsoft Docs"
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
  - "IDiaSymbol::get_dataBytes (método)"
ms.assetid: 5eb37179-20d8-44ae-a72a-405c1b0435c4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_dataBytes
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera los bytes de datos desde un símbolo de OEM.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_dataBytes (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Parámetros  
 `cbData`  
 \[in\]  Tamaño del búfer para contener los datos.  
  
 `pcbData`  
 \[out\]  devuelve el número de bytes escritos, o, si el parámetro de `data` es `NULL`, devuelve el número de bytes disponible.  
  
 `data[]`  
 \[out,\] búfer de En que se completa con los bytes de datos.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## Requisitos  
  
|Requisito|Descripción|  
|---------------|-----------------|  
|encabezado:|dia2.h|  
|versión:|diámetro SDK v7.0|  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)