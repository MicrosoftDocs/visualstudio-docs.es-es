---
title: "IDiaAddressMap::put_addressMapEnabled | Microsoft Docs"
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
  - "IDiaAddressMap::put_addressMapEnabled (método)"
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica si la configuración de direcciones se debe utilizar para traducir a direcciones de símbolos.  
  
## Sintaxis  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### Parámetros  
 NewVal  
 \[in\]  Establezca en `TRUE` para habilitar la traducción de símbolos, o `FALSE` para deshabilitar.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Los postprocesadores ejecutables actualizan a veces el ejecutable.  El diámetro contiene un mecanismo para admitir la traducción de símbolos al nuevo diseño.  
  
 Cuando un archivo PDB se carga, la configuración de direcciones almacenada en el archivo está habilitada.  En ocasiones, sin embargo, cuando una aplicación cliente puede que necesite proporcionar su propia configuración de direcciones llamando al método de [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .  Si el método de `set_addressMap` es correcto, la aplicación cliente debe llamar al método de `put_addressMapEnabled` con un parámetro de `NewVal` de `TRUE` para habilitar el uso de esa configuración de direcciones.  
  
 El estado actual de la configuración de direcciones que está habilitada puede recuperarse con una llamada al método de [IDiaAddressMap::get\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) .  
  
## Vea también  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)