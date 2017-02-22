---
title: "MemoryTypeEnum | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MemoryTypeEnum (enumeración)"
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# MemoryTypeEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica el tipo de memoria de acceso.  
  
## Sintaxis  
  
```cpp#  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### Parámetros  
 `MemTypeCode`  
 Memoria del código de acceso únicamente.  
  
 `MemTypeData`  
 Datos de acceso o memoria de montón.  
  
 `MemTypeStack`  
 Memoria del montón de acceso únicamente.  
  
 `MemTypeAny`  
 Acceso a cualquier clase de memoria.  
  
## Comentarios  
 Los valores de esta enumeración se pasan al método de [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) para limitar el acceso a diferentes tipos de memoria.  
  
## Requisitos  
 encabezado: cvconst.h  
  
## Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)