---
title: FIELD_KIND | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FIELD_KIND
helpviewer_keywords:
- FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 095a02edb0a462e2fdbdca0f7f92018861b3d6bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="fieldkind"></a>FIELD_KIND
Especifica el tipo de campo de un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_FIELD_KIND {   
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
   FIELD_SYM_MEMBER      = 0x01000000,  
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
  
```csharp  
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
   FIELD_SYM_MEMBER      = 0x01000000,  
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
  
## <a name="members"></a>Miembros  
 FIELD_KIND_TYPE  
 Indica que el campo es solo un tipo.  
  
 FIELD_KIND_SYMBOL  
 Indica que el campo es un símbolo con tipo, nombre y otra información.  
  
 FIELD_TYPE_PRIMITIVE  
 Indica que el campo es un tipo de datos primitivo.  
  
 FIELD_TYPE_STRUCT  
 Indica que el campo es una estructura.  
  
 FIELD_TYPE_CLASS  
 Indica que el campo es una clase.  
  
 FIELD_TYPE_INTERFACE  
 Indica que el campo es una interfaz.  
  
 FIELD_TYPE_UNION  
 Indica que el campo es una unión.  
  
 FIELD_TYPE_ARRAY  
 Indica que el campo es una matriz.  
  
 FIELD_TYPE_METHOD  
 Indica que el campo es un método.  
  
 FIELD_TYPE_BLOCK  
 Indica que el campo es un bloque.  
  
 FIELD_TYPE_POINTER  
 Indica que el campo es un puntero.  
  
 FIELD_TYPE_ENUM  
 Indica que el campo es un tipo de datos enumerado.  
  
 FIELD_TYPE_LABEL  
 Indica que el campo es una etiqueta.  
  
 FIELD_TYPE_TYPEDEF  
 Indica que el campo es una definición de tipo.  
  
 FIELD_TYPE_BITFIELD  
 Indica que el campo es un campo de bits.  
  
 FIELD_TYPE_NAMESPACE  
 Indica que el campo es un espacio de nombres.  
  
 FIELD_TYPE_MODULE  
 Indica que el campo es un módulo.  
  
 FIELD_TYPE_DYNAMIC  
 Indica que el campo es dinámico.  
  
 FIELD_TYPE_PROP  
 Indica que el campo es una propiedad.  
  
 FIELD_TYPE_INNERCLASS  
 Indica que el campo es una clase interna.  
  
 FIELD_TYPE_REFERENCE  
 Indica que el campo es una referencia.  
  
 FIELD_TYPE_EXTENDED  
 Reservado para un uso futuro.  
  
 FIELD_SYM_MEMBER  
 Indica que el campo es un miembro.  
  
 FIELD_SYM_LOCAL  
 Indica que el campo es local.  
  
 FIELD_SYM_PARAMETER  
 Indica que el campo es un parámetro.  
  
 FIELD_SYM_THIS  
 Indica que el campo es el puntero "this".  
  
 FIELD_SYM_GLOBAL  
 Indica que el campo es global.  
  
 FIELD_SYM_PROP_GETTER  
 Indica que el campo recupera las propiedades.  
  
 FIELD_SYM_PROP_SETTER  
 Indica que el campo de conjuntos de propiedades.  
  
 FIELD_SYM_EXTENDED  
 Reservado para un uso futuro.  
  
 FIELD_KIND_MASK  
 Indica una máscara para los tipos de campo.  
  
 FIELD_TYPE_MASK  
 Indica una máscara para los tipos de campo.  
  
 FIELD_SYM_MASK  
 Indica una máscara para la información de símbolos.  
  
## <a name="remarks"></a>Comentarios  
 Devuelve una llamada a la [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) método.  
  
 Según el tipo de campo, [QueryInterface](/cpp/atl/queryinterface) puede llamarse en el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaz para una forma más específica de la interfaz. Por ejemplo, si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) devuelve `FIELD_TYPE_METHOD`, a continuación, puede llamar a `QueryInterface` en I`DebugField` para obtener la [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) interfaz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)