---
title: "OBJECT_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OBJECT_TYPE"
helpviewer_keywords: 
  - "Enumeración de OBJECT_TYPE"
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# OBJECT_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica el tipo de un objeto del evaluador de expresiones.  
  
## Sintaxis  
  
```cpp#  
enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
typedef DWORD OBJECT_TYPE;  
```  
  
```c#  
public enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
```  
  
## Members  
 OBJECT\_TYPE\_BOOLEAN  
 Indica que el objeto es un valor booleano.  
  
 OBJECT\_TYPE\_CHAR  
 indica que el objeto es un carácter.  
  
 OBJECT\_TYPE\_I1  
 Indica que el objeto es un entero con signo un byte.  
  
 OBJECT\_TYPE\_U1  
 Indica que el objeto es un entero sin signo de un byte.  
  
 OBJECT\_TYPE\_I2  
 Indica que el objeto es un entero de dos bytes.  
  
 OBJECT\_TYPE\_U2  
 indica que el objeto es un entero sin signo de dos bytes.  
  
 OBJECT\_TYPE\_I4  
 Indica que el objeto es un entero con signo cuatro bytes.  
  
 OBJECT\_TYPE\_U4  
 Indica que el objeto es un entero sin signo de cuatro bytes.  
  
 OBJECT\_TYPE\_I8  
 Indica que el objeto es un entero con signo ocho\-byte.  
  
 OBJECT\_TYPE\_U8  
 Indica que el objeto es un entero sin signo de ocho\-byte.  
  
 OBJECT\_TYPE\_R4  
 Indica que el objeto es un número de punto flotante de cuatro bytes.  
  
 OBJECT\_TYPE\_R8  
 Indica que el objeto es un número de punto flotante de ocho\-byte.  
  
 OBJECT\_TYPE\_OBJECT  
 indica que el objeto es un objeto.  
  
 OBJECT\_TYPE\_NULL  
 indica que el objeto es NULL.  
  
 OBJECT\_TYPE\_CLASS  
 indica que el objeto es una clase.  
  
## Comentarios  
 pasado como argumento a los métodos de [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) y de [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) .  
  
## Requisitos  
 encabezado: ee.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)