---
title: "IDiaAddressMap::get_addressMapEnabled | Microsoft Docs"
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
  - "IDiaAddressMap::get_addressMapEnabled (método)"
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaAddressMap::get_addressMapEnabled
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Indica si la configuración de direcciones se ha establecido para una sesión determinada.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### Parámetros  
 pRetVal  
 \[out\]  devuelve `TRUE` si se habilita la reproducción de direcciones.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Los postprocesadores ejecutables actualizan a veces el ejecutable.  El diámetro contiene un mecanismo para admitir la traducción de símbolos al nuevo diseño.  
  
 Las aplicaciones cliente pueden establecer la configuración de direcciones de una determinada sesión obtener la interfaz de [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) de la interfaz de [IDiaSession](../../debugger/debug-interface-access/idiasession.md) y llamando al método de [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) seguido por una llamada al método de [IDiaAddressMap::put\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) .  El método de `get_addressMapEnabled` devuelve los resultados de llamar al método de `put_addressMapEnabled` .  
  
## Vea también  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)