---
title: "FIELD_MODIFIERS | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_MODIFIERS"
helpviewer_keywords: 
  - "Enumeración FIELD_MODIFIERS"
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# FIELD_MODIFIERS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica modificadores para un tipo de campo.  
  
## Sintaxis  
  
```cpp#  
enum enum_FIELD_MODIFIERS {   
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
typedef DWORD FIELD_MODIFIERS;  
```  
  
```c#  
public enum enum_FIELD_MODIFIERS {  
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
```  
  
## Members  
 FIELD\_MOD\_ACCESS\_TYPE  
 Indica que el campo no se puede obtener acceso.  
  
 FIELD\_MOD\_ACCESS\_PUBLIC  
 indica que el campo tiene acceso público.  
  
 FIELD\_MOD\_ACCESS\_PROTECTED  
 indica que el campo ha protegido el acceso.  
  
 FIELD\_MOD\_ACCESS\_PRIVATE  
 indica que el campo tiene acceso privado.  
  
 FIELD\_MOD\_NOMODIFIERS  
 indica que el campo no tiene ningún modificador.  
  
 FIELD\_MOD\_STATIC  
 indica que el campo es estático.  
  
 FIELD\_MOD\_CONSTANT  
 indica que el campo es una constante.  
  
 FIELD\_MOD\_TRANSIENT  
 indica que el campo es transitorio.  
  
 FIELD\_MOD\_VOLATILE  
 Indica que el campo son volátiles.  
  
 FIELD\_MOD\_ABSTRACT  
 indica que el campo es abstracto.  
  
 FIELD\_MOD\_NATIVE  
 Indica que el campo está nativo.  
  
 FIELD\_MOD\_SYNCHRONIZED  
 indica que el campo está sincronizado.  
  
 FIELD\_MOD\_VIRTUAL  
 indica que el campo es virtual.  
  
 FIELD\_MOD\_INTERFACE  
 indica que el campo es una interfaz.  
  
 FIELD\_MOD\_FINAL  
 Indica que el campo es definitiva.  
  
 FIELD\_MOD\_SENTINEL  
 Indica que el campo está centinela.  
  
 FIELD\_MOD\_INNERCLASS  
 indica que el campo es una clase interna.  
  
 FIELD\_TYPE\_OPTIONAL  
 indica que el campo es opcional.  
  
 FIELD\_MOD\_BYREF  
 Indica que el campo es un argumento de referencia.  esto está específicamente para los argumentos de método.  
  
 FIELD\_MOD\_HIDDEN  
 Indica que el campo se debe ocultar o mostrar en otro contexto; por ejemplo, valores locales de estático de [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] .  
  
 FIELD\_MOD\_MARSHALASOBJECT  
 indica que el campo representa un objeto con una interfaz de `IUnknown` .  
  
 FIELD\_MOD\_SPECIAL\_NAME  
 Indica que el campo tiene un nombre especial, por ejemplo, `.ctor` para un constructor \([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] solo\).  
  
 FIELD\_MOD\_HIDEBYSIG  
 Indica que el campo tiene la palabra clave de `Overloads` aplicado al \([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] solo\).  
  
 FIELD\_MOD\_WRITEONLY  
 Indica que el campo es de solo escritura.  Este valor no se incluye en `FIELD_MOD_ALL`, como el único uso de como campos de solo escritura es para la evaluación de la función.  Un usuario debe explícitamente ordenar los campos de `FIELD_MOD_WRITEONLY` .  
  
 FIELD\_MOD\_ACCESS\_MASK  
 Indica una máscara para el acceso de campo.  
  
 FIELD\_MOD\_MASK  
 Indica una máscara para los modificadores de campo.  
  
## Comentarios  
 utilizado para el miembro de `dwModifiers` de la estructura de [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) .  
  
 Esta configuración también se pasan al método de [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) el filtro para los campos concretos.  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)