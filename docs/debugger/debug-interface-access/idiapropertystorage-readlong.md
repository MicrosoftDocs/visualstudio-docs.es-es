---
title: "IDiaPropertyStorage::ReadLONG | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadLONG"
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaPropertyStorage::ReadLONG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lee los valores de `LONG` en un conjunto de propiedades.  
  
## Sintaxis  
  
```cpp#  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### Parámetros  
 `id`  
 \[in\]  Identificador de la propiedad que se leerá \(`PROPID` se define en WTypes.h como `ULONG`\).  
  
 `pValue`  
 \[out\]  devuelve el valor de propiedad.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; si no devuelve un código de error.  Devuelve `E_INVALIDARG` si la propiedad no es de `LONG`escrito.  
  
## Comentarios  
 `LONG` está definido por Windows como un entero de 32 bits.  
  
## Vea también  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)