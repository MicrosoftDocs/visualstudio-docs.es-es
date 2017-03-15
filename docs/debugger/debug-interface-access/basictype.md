---
title: "BasicType | Microsoft Docs"
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
  - "BasicType (enumeración)"
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# BasicType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica el tipo básico de símbolos.  
  
## Sintaxis  
  
```cpp#  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## Elementos \(Elements\)  
 btNoType  
 No se especifica ningún tipo básico.  
  
 btVoid  
 el tipo básico es `void`.  
  
 btChar  
 El tipo básico es `char` \(C\/C\+\+ tipo\).  
  
 btWChar  
 El tipo básico es un carácter ancho \(Unicode\) \(`WCHAR`\).  
  
 btInt  
 El tipo básico es `signed int` \(C\/C\+\+ tipo\).  
  
 btUInt  
 El tipo básico es `unsigned int` \(C\/C\+\+ tipo\).  
  
 btFloat  
 El tipo básico es un número de punto flotante \(`FLOAT`\).  
  
 btBCD  
 el tipo básico es decimal codificado en binario \(`BCD`\).  
  
 btBool  
 El tipo básico es un valor booleano \(`BOOL`\).  
  
 btLong  
 El tipo básico es `long int` \(C\/C\+\+ tipo\).  
  
 btULong  
 El tipo básico es `unsigned long int` \(C\/C\+\+ tipo\).  
  
 btCurrency  
 El tipo básico es divisa.  
  
 btDate  
 El tipo básico es fecha y hora \(`DATE`\).  
  
 btVariant  
 El tipo básico es una estructura del tipo de la variable \(`VARIANT`\).  
  
 btComplex  
 el tipo básico es un número complejo.  
  
 btBit  
 el tipo básico es un bit.  
  
 btBSTR  
 el tipo básico es una cadena básica o binaria \(`BSTR`\).  
  
 btHresult  
 el tipo básico es `HRESULT`.  
  
## Comentarios  
 Los valores de esta enumeración son devueltos por el método de [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) .  
  
## Requisitos  
 encabezado: cvconst.h  
  
## Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)