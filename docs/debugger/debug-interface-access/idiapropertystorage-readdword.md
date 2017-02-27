---
title: "IDiaPropertyStorage::ReadDWORD | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadDWORD"
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaPropertyStorage::ReadDWORD
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lee los valores de `DWORD` en un conjunto de propiedades.  
  
## Sintaxis  
  
```cpp#  
HRESULT ReadDWORD (   
   PROPID id,  
   DWORD* pValue  
);  
```  
  
#### Parámetros  
 `id`  
 \[in\]  Identificador de la propiedad que se leerá \(`PROPID` se define en WTypes.h como `ULONG`\).  
  
 `pValue`  
 \[out\]  devuelve el valor de propiedad.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; si no devuelve un código de error.  Devuelve `E_INVALIDARG` si la propiedad no es de `DWORD`escrito.  
  
## Comentarios  
 `DWORD` está definido por Windows como entero sin signo de 32 bits.  
  
## Vea también  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)