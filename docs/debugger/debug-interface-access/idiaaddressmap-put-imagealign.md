---
title: "IDiaAddressMap::put_imageAlign | Microsoft Docs"
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
  - "IDiaAddressMap::put_imageAlign (método)"
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

establece la alineación de la imagen.  
  
## Sintaxis  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### Parámetros  
 NewVal  
 \[in\]  El nuevo valor de la alineación de la imagen para el ejecutable.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Las imágenes \(ejecutables cargan\) se alinean a los límites especificados de memoria.  Esta alineación se puede afectar a la arquitectura del sistema actual y por opciones de compilación y en tiempo de vinculación.  la alineación de la imagen está siempre en límites de byte.  Los valores de la alineación de la imagen son válidos: 1, 2, 4, 8, 16, 32, y límites de 64 bytes.  
  
 La alineación actual de la imagen se puede recuperar con una llamada al método de [IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) .  
  
> [!NOTE]
>  La imagen ya se ha cargado en el momento en que este método puede llamar.  El método de `put_imageAlign` se utiliza normalmente cuando se ha movido o se ha cambiado la imagen y se necesita una nueva alineación.  
  
## Vea también  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)