---
title: "IDiaInjectedSource::get_source | Microsoft Docs"
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
  - "IDiaInjectedSource::get_source (método)"
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaInjectedSource::get_source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera los bytes de código fuente.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Parámetros  
 `cbData`  
 \[in\]  El número de bytes que representa el tamaño del búfer de datos.  
  
 `pcbData`  
 \[out\]  devuelve el número de bytes que representa los bytes devueltos.  Si `data` es `NULL`, después `pcbData` es el número total de bytes de datos disponibles.  
  
 `data[]`  
 \[out\]  Un búfer que debe ser completo con los bytes de origen.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si esta propiedad no se admite.  De lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)