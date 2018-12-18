---
title: FIELD_MODIFIERS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6403beec680341416940a2cb4f65476408e095be
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949089"
---
# <a name="fieldmodifiers"></a>FIELD_MODIFIERS
Especifica modificadores para un tipo de campo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_FIELD_MODIFIERS {   
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
  
```csharp  
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
  
## <a name="members"></a>Miembros  
 FIELD_MOD_ACCESS_TYPE  
 Indica que el campo no se puede acceder.  
  
 FIELD_MOD_ACCESS_PUBLIC  
 Indica que el campo tiene acceso público.  
  
 FIELD_MOD_ACCESS_PROTECTED  
 Indica que el campo tiene acceso protegido.  
  
 FIELD_MOD_ACCESS_PRIVATE  
 Indica que el campo tiene acceso privado.  
  
 FIELD_MOD_NOMODIFIERS  
 Indica que el campo no tiene modificadores.  
  
 FIELD_MOD_STATIC  
 Indica que el campo es estático.  
  
 FIELD_MOD_CONSTANT  
 Indica que el campo es una constante.  
  
 FIELD_MOD_TRANSIENT  
 Indica que el campo es transitorio.  
  
 FIELD_MOD_VOLATILE  
 Indica que el campo es volátil.  
  
 FIELD_MOD_ABSTRACT  
 Indica que el campo es abstracto.  
  
 FIELD_MOD_NATIVE  
 Indica que el campo es nativo.  
  
 FIELD_MOD_SYNCHRONIZED  
 Indica que el campo está sincronizado.  
  
 FIELD_MOD_VIRTUAL  
 Indica que el campo es virtual.  
  
 FIELD_MOD_INTERFACE  
 Indica que el campo es una interfaz.  
  
 FIELD_MOD_FINAL  
 Indica que el campo es final.  
  
 FIELD_MOD_SENTINEL  
 Indica que el campo es un valor de centinela.  
  
 FIELD_MOD_INNERCLASS  
 Indica que el campo es una clase interna.  
  
 FIELD_TYPE_OPTIONAL  
 Indica que el campo es opcional.  
  
 FIELD_MOD_BYREF  
 Indica que el campo es un argumento de referencia. Se trata específicamente para los argumentos de método.  
  
 FIELD_MOD_HIDDEN  
 Indica que el campo debe estar oculto o en otro contexto; Por ejemplo, [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] variables locales estáticas.  
  
 FIELD_MOD_MARSHALASOBJECT  
 Indica que el campo representa un objeto con un `IUnknown` interfaz.  
  
 FIELD_MOD_SPECIAL_NAME  
 Indica que el campo tiene un nombre especial, por ejemplo, `.ctor` para un constructor ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] solo).  
  
 FIELD_MOD_HIDEBYSIG  
 Indica que el campo tiene la `Overloads` palabra clave aplicada a él ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] solo).  
  
 FIELD_MOD_WRITEONLY  
 Indica que el campo es de solo escritura. Este valor no se incluye en `FIELD_MOD_ALL`, como el uso de esos campos de solo escritura solo es para la evaluación de función. Un usuario debe pedir explícitamente `FIELD_MOD_WRITEONLY` campos.  
  
 FIELD_MOD_ACCESS_MASK  
 Indica una máscara de acceso de campo.  
  
 FIELD_MOD_MASK  
 Indica una máscara para los modificadores de campo.  
  
## <a name="remarks"></a>Comentarios  
 Utilizado para la `dwModifiers` miembro de la [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) estructura.  
  
 Estos valores también se pasan a la [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) método filtrar por campos específicos.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)