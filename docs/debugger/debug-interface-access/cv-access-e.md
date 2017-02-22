---
title: "CV_access_e | Microsoft Docs"
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
  - "CV_access_e (enumeración)"
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CV_access_e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica el ámbito de visibilidad \(nivel de acceso\) de las funciones y variables miembro.  
  
## Sintaxis  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## Elementos \(Elements\)  
 CV\_private  
 Acceso a miembro privado.  
  
 CV\_protected  
 el miembro ha protegido el acceso.  
  
 CV\_public  
 Acceso a miembro público.  
  
## Comentarios  
 No se incluye el especificador de acceso de `friend` aquí porque normalmente usan las funciones de no miembro que tienen acceso a los elementos privados y protegidos de la clase.  Utilice el método de [IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) para buscar símbolos con acceso de `SymTagFriend` .  
  
## Requisitos  
 encabezado: cvconst.h  
  
## Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)