---
title: "IDiaPropertyStorage::ReadBOOL | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadBOOL"
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaPropertyStorage::ReadBOOL
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lee los valores de `BOOL` en un conjunto de propiedades.  
  
## Sintaxis  
  
```cpp#  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### Parámetros  
 `id`  
 \[in\]  Identificador de la propiedad que se leerá \(`PROPID` se define en WTypes.h como `ULONG`\).  
  
 `pValue`  
 \[out\]  devuelve el valor de propiedad.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; si no devuelve un código de error.  Devuelve `E_INVALIDARG` si la propiedad no es de `BOOL`escrito.  
  
## Comentarios  
 Para los resultados coherentes, interpreta el valor de `BOOL` de modo que los valores distintos de cero se `TRUE` y cero es `FALSE`.  
  
## Vea también  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)