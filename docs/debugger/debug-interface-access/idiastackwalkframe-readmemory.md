---
title: "IDiaStackWalkFrame::readMemory | Microsoft Docs"
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
  - "IDiaStackWalkFrame::readMemory (método)"
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaStackWalkFrame::readMemory
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Memoria de lecturas de la imagen.  
  
## Sintaxis  
  
```cpp#  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### Parámetros  
 `type`  
 \[in\] Uno de los valores de enumeración de [MemoryTypeEnum \(Enumeración\)](../../debugger/debug-interface-access/memorytypeenum.md) que especifica la clase de memoria de acceso.  
  
 `va`  
 \[in\] ubicación de la dirección virtual de imagen a la lectura de inicio.  
  
 `cbData`  
 \[in\] tamaño del búfer de datos, en bytes.  
  
 `pcbData`  
 \[out\] devuelve el número de bytes devueltos.  Si `data` es `NULL`, después`pcbData` contiene el número total de bytes de datos disponibles.  
  
 `data`  
 \[out\] búfer de que debe ser completo con datos de la ubicación especificada.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)