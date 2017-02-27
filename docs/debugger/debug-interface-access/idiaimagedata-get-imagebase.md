---
title: "IDiaImageData::get_imageBase | Microsoft Docs"
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
  - "IDiaImageData::get_imageBase (método)"
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaImageData::get_imageBase
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera la ubicación de memoria donde la imagen debe ser basada en.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  devuelve el valor sugerido de la base de la imagen.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Debido a la base de la imagen está en conflicto, una imagen puede ser afirmativo automáticamente a una ubicación de memoria no utilizada cuando se carga.  Este método devuelve la sugerencia base \(ubicación de memoria sugerida\) que se almacenara en el módulo en tiempo de compilación.  
  
## Vea también  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)