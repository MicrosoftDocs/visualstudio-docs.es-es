---
title: "IDiaSectionContrib::get_dataCrc | Microsoft Docs"
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
  - "IDiaSectionContrib::get_dataCrc (método)"
ms.assetid: 33b7488f-dc9c-47b3-b08c-737e0eb1bf7d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSectionContrib::get_dataCrc
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera la prueba cíclica \(CRC\) de redundancia de los datos de la sección.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_dataCrc (   
   DWORD* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve CRC de los datos de la sección.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si esta propiedad no se admite.  De lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)