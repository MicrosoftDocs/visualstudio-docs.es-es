---
title: DBG_ATTRIB_FLAGS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c8b3f52eff80c187d3c43b87cea804ace483169
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737558"
---
# <a name="dbg_attrib_flags"></a>DBG_ATTRIB_FLAGS
Describe varios atributos para un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) o un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) interfaz. Miembro de la estructura [DEBUG_PROPERTY_INFO.](../../../extensibility/debugger/reference/debug-property-info.md)

## <a name="syntax"></a>Sintaxis

```cpp
#define DBG_ATTRIB_NONE                 0x0000000000000000,
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,

// Attributes about the object itself

#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,

// Attributes about the value of the object

#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,

// Attributes about field access types for the object

#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,

// Attributes for the storage types of the object

#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,

// Attributes for the type modifiers on the object

#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,

// Attributes that describe the type of object

#define DBG_ATTRIB_DATA                 0x0000010000000000,
#define DBG_ATTRIB_METHOD               0x0000020000000000,
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,
#define DBG_ATTRIB_CLASS                0x0000080000000000,
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,

// Miscellaneous attributes

#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000

typedef UINT64 DBG_ATTRIB_FLAGS;
```

```csharp
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,

// Attributes about the object itself

public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,

// Attributes about the value of the object

public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,

// Attributes about field access types for the object

public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,

// Attributes for the storage types of the object

public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,

// Attributes for the type modifiers on the object

public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,

// Attributes that describe the type of object

public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,

// Miscellaneous attributes

public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000
```

## <a name="members"></a>Miembros
 `DBG_ATTRIB_NONE`\
 Indica que no hay atributos.

 `DBG_ATTRIB_ALL`\
 Indica todos los atributos.

 `DBG_ATTRIB_OBJ_IS_EXPANDABLE`\
 Indica que la propiedad o referencia tiene elementos secundarios.

 `DBG_ATTRIB_OBJ_HAS_ID`\
 Indica que se ha creado un identificador para este objeto.

 `DBG_ATTRIB_OBJ_CAN_HAVE_ID`\
 Indica que se puede crear un identificador para este objeto.

 `DBG_ATTRIB_VALUE_READONLY`\
 Indica que el valor es de solo lectura.

 `DBG_ATTRIB_VALUE_ERROR`\
 Indica que el valor es un error.

 `DBG_ATTRIB_VALUE_SIDE_EFFECT`\
 Indica que la evaluación tuvo un efecto secundario.

 `DBG_ATTRIB_OVERLOADED_CONTAINER`\
 Indica que esta propiedad es realmente un contenedor de sobrecargas.

 `DBG_ATTRIB_VALUE_BOOLEAN`\
 Indica que el `DEBUG_PROPERTY_INFO::bstrValue` valor en es booleano.

 `DBG_ATTRIB_VALUE_BOOLEAN_TRUE`\
 Indica que el `DEBUG_PROPERTY_INFO::bstrValue` valor de `TRUE`es booleano y .

 `DBG_ATTRIB_VALUE_INVALID`\
 Indica que el valor de `DEBUG_PROPERTY_INFO::bstrValue` no es válido.

 `DBG_ATTRIB_VALUE_NAT`\
 Indica que el `DEBUG_PROPERTY_INFO::bstrValue` valor en es "*no una cosa*" (NAT). NAT describe una marca de registro en procesadores Intel de 64 bits que indica excepciones especulativas diferidas.

 `DBG_ATTRIB_VALUE_AUTOEXPANDED`\
 Indica que el `DEBUG_PROPERTY_INFO::bstrValue` valor en posiblemente se ha expandido automáticamente.

 `DBG_ATTRIB_VALUE_TIMEOUT`\
 Indica que se ha reducido el tiempo de espera de una evaluación.

 `DBG_ATTRIB_VALUE_RAW_STRING`\
 Indica que el `DEBUG_PROPERTY_INFO::bstrValue` valor en se puede representar mediante una cadena sin formato.

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`\
 Indica que esta propiedad tiene al menos un visor personalizado asociado.

 `DBG_ATTRIB_ACCESS_NONE`\
 Indica un objeto que `public` `private`no `protected` tiene acceso a ningún tipo , , ni a un tipo.

 `DBG_ATTRIB_ACCESS_PUBLIC`\
 Indica un objeto que tiene acceso público.

 `DBG_ATTRIB_ACCESS_PRIVATE`\
 Indica un objeto que tiene acceso privado.

 `DBG_ATTRIB_ACCESS_PROTECTED`\
 Indica un objeto que tiene acceso protegido.

 `DBG_ATTRIB_ACCESS_FINAL`\
 Indica un objeto que tiene acceso final.

 `DBG_ATTRIB_ACCESS_ALL`\
 Máscara para extraer los `DBG_ATTRIB_FLAGS`atributos de acceso de .

 `DBG_ATTRIB_STORAGE_NONE`\
 Indica que no se ha especificado ningún tipo de almacenamiento.

 `DBG_ATTRIB_STORAGE_GLOBAL`\
 Indica almacenamiento global.

 `DBG_ATTRIB_STORAGE_STATIC`\
 Indica almacenamiento estático.

 `DBG_ATTRIB_STORAGE_REGISTER`\
 Indica el almacenamiento en el registro.

 `DBG_ATTRIB_STORAGE_ALL`\
 Máscara para extraer los `DBG_ATTRIB_FLAGS`atributos de almacenamiento de .

 `DBG_ATTRIB_TYPE_NONE`\
 Indica que no hay ningún modificador de tipo.

 `DBG_ATTRIB_TYPE_VIRTUAL`\
 Indica que el tipo de objeto es virtual.

 `DBG_ATTRIB_TYPE_CONSTANT`\
 Indica que el tipo de objeto es constante.

 `DBG_ATTRIB_TYPE_SYNCHRONIZED`\
 Indica que el tipo de objeto está sincronizado.

 `DBG_ATTRIB_TYPE_VOLATILE`\
 Indica que el tipo de objeto es volátil.

 `DBG_ATTRIB_TYPE_ALL`\
 Máscara para extraer los `DBG_ATTRIB_FLAGS`atributos de tipo de .

 `DBG_ATTRIB_DATA`\
 Indica que este objeto es un campo de datos.

 `DBG_ATTRIB_METHOD`\
 Indica que este objeto es un método.

 `DBG_ATTRIB_PROPERTY`\
 Indica que este objeto es una propiedad.

 `DBG_ATTRIB_CLASS`\
 Indica que este objeto es una clase.

 `DBG_ATTRIB_BASECLASS`\
 Indica que este objeto es una clase base.

 `DBG_ATTRIB_INTERFACE`\
 Indica que este objeto es una interfaz.

 `DBG_ATTRIB_INNERCLASS`\
 Indica que este objeto es una clase interna.

 `DBG_ATTRIB_MOSTDERIVED`\
 Indica que este objeto es '*más derivado*'. El término *"más derivado"* significa el tipo real del objeto, y no el tipo de su referencia.

 `DBG_ATTRIB_CHILD_ALL`\
 Indica una máscara `DBG_ATTRIB_DATA` `DBG_ATTRIB_MOSTDERIVED`de a través de .

 `DBG_ATTRIB_MULTI_CUSTOM_VIEWERS`\
 Indica que el objeto tiene varios visores personalizados asociados.

## <a name="remarks"></a>Observaciones

> [!NOTE]
> Los valores de esta enumeración no se definen realmente en el ensamblado para C. En su lugar, debe copiar las definiciones en el archivo de origen.

 Estas marcas también se utilizan para filtrar elementos secundarios de un objeto, por ejemplo, cuando se pasan como argumento a [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md). Los valores se pueden combinar `OR`con un archivo .

 El `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` indicador es [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] una indicación para obtener el [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaz desde el [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaz y llame a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) para obtener una lista de visores personalizados.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
