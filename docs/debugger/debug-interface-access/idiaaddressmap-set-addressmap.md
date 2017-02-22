---
title: "IDiaAddressMap::set_addressMap | Microsoft Docs"
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
  - "IDiaAddressMap::set_addressMap (método)"
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Proporciona una configuración de direcciones las traducciones admiten el diseño de la imagen.  
  
## Sintaxis  
  
```cpp#  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### Parámetros  
 `cbData`  
 \[in\]  el número de elementos en el parámetro de `data` .  
  
 `data[]`  
 \[in\]  Una matriz de estructuras de [DiaAddressMapEntry Structure](../../debugger/debug-interface-access/diaaddressmapentry.md) que definen el mapa de traducción.  
  
 `imagetoSymbols`  
 \[in\]  `TRUE` si el parámetro de `data` define un mapa del nuevo diseño de la imagen al diseño original \(descrito por los símbolos de depuración\).  `FALSE` si `data` es una asignación al nuevo diseño de imagen tomado de diseño original.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Normalmente, el diámetro recupera asigna la traducción de direcciones del archivo de base de datos de programa \(.pdb\).  Si faltan estos valores, el método de [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) se llama dos veces, una vez con el parámetro de `imagetoSymbols` establecido en `TRUE` y otra con el parámetro de `imagetoSymbols` establecido en `FALSE`.  Las traducciones de la configuración de direcciones no se pueden habilitar mediante el método de [IDiaAddressMap::put\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) a menos que se proporcionan los mapas de traducción.  
  
## Vea también  
 [DiaAddressMapEntry Structure](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)