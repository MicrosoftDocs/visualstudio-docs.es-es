---
title: "UdtKind | Microsoft Docs"
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
  - "UdtKind (enumeración)"
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# UdtKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Describe la variedad de tipo definido por el usuario \(UDT\).  
  
## Sintaxis  
  
```cpp#  
enum UdtKind {   
   UdtStruct,  
   UdtClass,  
   UdtUnion,  
   UdtInterface  
};  
```  
  
## Elementos \(Elements\)  
 UdtStruct  
 UDT es una estructura.  
  
 UdtClass  
 UDT es una clase.  
  
 UdtUnion  
 UDT es la unión.  
  
 UdtInterface  
 UDT es una interfaz.  
  
## Comentarios  
 Los valores de esta enumeración se devuelven por el [IDiaSymbol::get\_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) método.  
  
## Requisitos  
 Encabezado: cvconst.h  
  
## Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)