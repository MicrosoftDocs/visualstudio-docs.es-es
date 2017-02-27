---
title: "IDiaStackWalkHelper::readMemory | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::readMemory (método)"
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lee un bloque de datos de la imagen del ejecutable en memoria.  
  
## Sintaxis  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### Parámetros  
 `type`  
 \[in\]  Un valor de enumeración de [MemoryTypeEnum \(Enumeración\)](../../debugger/debug-interface-access/memorytypeenum.md) que especifica el tipo de memoria a la lectura.  
  
 va  
 \[in\]  Dirección virtual en la imagen de la que se empiezan a lectura.  
  
 `cbData`  
 \[in\]  El tamaño del búfer de datos en bytes.  
  
 `pcbData`  
 \[out\]  Devuelve el número de bytes leídos realmente.  Si `pbData` es `NULL`, entonces es el número total de bytes de datos disponibles.  
  
 `pbData`  
 \[in, out\]  un búfer que se completa con la lectura de memoria.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum \(Enumeración\)](../../debugger/debug-interface-access/memorytypeenum.md)