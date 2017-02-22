---
title: "DataKind | Microsoft Docs"
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
  - "DataKind (enumeración)"
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DataKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Indica el ámbito determinado de un valor de datos.  
  
## Sintaxis  
  
```cpp#  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## Elementos \(Elements\)  
 DataIsUnknown  
 El símbolo de datos no puede determinarse.  
  
 DataIsLocal  
 el elemento de datos es una variable local.  
  
 DataIsStaticLocal  
 el elemento de datos es una variable local estática.  
  
 DataIsParam  
 el elemento de datos es un parámetro formal.  
  
 DataIsObjectPtr  
 El elemento de datos es un puntero de objeto \(`this`\).  
  
 DataIsFileStatic  
 El elemento de datos es una variable de archivo\-scoped.  
  
 DataIsGlobal  
 el elemento de datos es una variable global.  
  
 DataIsMember  
 El elemento de datos es una variable miembro del objeto.  
  
 DataIsStaticMember  
 el elemento de datos es una variable estática de la clase.  
  
 DataIsConstant  
 el elemento de datos es un valor constante.  
  
## Comentarios  
 Los valores de esta enumeración son devueltos por el método de [IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) .  
  
## Requisitos  
 encabezado: cvconst.h  
  
## Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)