---
title: "FIELD_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_KIND"
helpviewer_keywords: 
  - "Enumeración FIELD_KIND"
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# FIELD_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica el tipo de campo contenida en un objeto de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## Sintaxis  
  
```cpp#  
enum enum_FIELD_KIND {   
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
typedef DWORD FIELD_KIND;  
```  
  
```c#  
public enum enum_FIELD_KIND {  
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
```  
  
## Members  
 FIELD\_KIND\_TYPE  
 Indica que el campo es un tipo.  
  
 FIELD\_KIND\_SYMBOL  
 Indica que el campo es un símbolo, con el tipo, nombre, y otra información.  
  
 FIELD\_TYPE\_PRIMITIVE  
 indica que el campo es un tipo de datos primitivo.  
  
 FIELD\_TYPE\_STRUCT  
 indica que el campo es una estructura.  
  
 FIELD\_TYPE\_CLASS  
 indica que el campo es una clase.  
  
 FIELD\_TYPE\_INTERFACE  
 indica que el campo es una interfaz.  
  
 FIELD\_TYPE\_UNION  
 indica que el campo es una unión.  
  
 FIELD\_TYPE\_ARRAY  
 Indica que el campo es una matriz.  
  
 FIELD\_TYPE\_METHOD  
 indica que el campo es un método.  
  
 FIELD\_TYPE\_BLOCK  
 indica que el campo es un bloque.  
  
 FIELD\_TYPE\_POINTER  
 Indica que el campo es un puntero.  
  
 FIELD\_TYPE\_ENUM  
 indica que el campo es un tipo de datos enumerado.  
  
 FIELD\_TYPE\_LABEL  
 indica que el campo es una etiqueta.  
  
 FIELD\_TYPE\_TYPEDEF  
 Indica que el campo es un tipo typedef.  
  
 FIELD\_TYPE\_BITFIELD  
 indica que el campo es un campo de bits.  
  
 FIELD\_TYPE\_NAMESPACE  
 indica que el campo es un espacio de nombres.  
  
 FIELD\_TYPE\_MODULE  
 indica que el campo es un módulo.  
  
 FIELD\_TYPE\_DYNAMIC  
 indica que el campo es dinámico.  
  
 FIELD\_TYPE\_PROP  
 indica que el campo es una propiedad.  
  
 FIELD\_TYPE\_INNERCLASS  
 indica que el campo es una clase interna.  
  
 FIELD\_TYPE\_REFERENCE  
 indica que el campo es una referencia.  
  
 FIELD\_TYPE\_EXTENDED  
 Reservado para un uso futuro.  
  
 FIELD\_SYM\_MEMBER  
 Indica que el campo es miembro.  
  
 FIELD\_SYM\_LOCAL  
 indica que el campo es local.  
  
 FIELD\_SYM\_PARAMETER  
 indica que el campo es un parámetro.  
  
 FIELD\_SYM\_THIS  
 Indica que el campo es el puntero “this”.  
  
 FIELD\_SYM\_GLOBAL  
 indica que el campo es global.  
  
 FIELD\_SYM\_PROP\_GETTER  
 indica que el campo recupera propiedades.  
  
 FIELD\_SYM\_PROP\_SETTER  
 indica que las propiedades de los conjuntos de campos.  
  
 FIELD\_SYM\_EXTENDED  
 Reservado para un uso futuro.  
  
 FIELD\_KIND\_MASK  
 Indica una máscara para las clases de campo.  
  
 FIELD\_TYPE\_MASK  
 indica una máscara para los tipos de campo.  
  
 FIELD\_SYM\_MASK  
 Indica una máscara para la información de símbolos.  
  
## Comentarios  
 Devueltos de una llamada al método de [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) .  
  
 En función del tipo de campo, [QueryInterface](/visual-cpp/atl/queryinterface) se puede llamar en la interfaz de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) para un formulario más específico de interfaz.  Por ejemplo, si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) devuelve `FIELD_TYPE_METHOD`, puede llamar a `QueryInterface` en I`DebugField` para obtener la interfaz de [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) .  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)