---
title: DBG_ATTRIB_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 831d1326d88e70ffaba2cc0c242c55d7325be705
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689335"
---
# <a name="dbgattribflags"></a>DBG_ATTRIB_FLAGS
Describe los distintos atributos para un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) o un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) interfaz. Miembro de la [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estructura.

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
 DBG_ATTRIB_NONE no indica ningún atributo.

 DBG_ATTRIB_ALL indica todos los atributos.

 DBG_ATTRIB_OBJ_IS_EXPANDABLE indica que la propiedad o referencia tiene elementos secundarios.

 DBG_ATTRIB_OBJ_HAS_ID indica que se ha creado un identificador para este objeto.

 DBG_ATTRIB_OBJ_CAN_HAVE_ID indica que se puede crear un identificador para este objeto.

 DBG_ATTRIB_VALUE_READONLY indica que el valor es de solo lectura.

 DBG_ATTRIB_VALUE_ERROR indica que el valor es un error.

 DBG_ATTRIB_VALUE_SIDE_EFFECT indica que la evaluación ha tenido un efecto secundario.

 DBG_ATTRIB_OVERLOADED_CONTAINER indica que esta propiedad es realmente un contenedor de sobrecargas.

 DBG_ATTRIB_VALUE_BOOLEAN indica que el valor de `DEBUG_PROPERTY_INFO::bstrValue` es un valor booleano.

 DBG_ATTRIB_VALUE_BOOLEAN_TRUE indica que el valor de `DEBUG_PROPERTY_INFO::bstrValue` es booleano y `TRUE`.

 DBG_ATTRIB_VALUE_INVALID indica que el valor de `DEBUG_PROPERTY_INFO::bstrValue` no es válido.

 DBG_ATTRIB_VALUE_NAT indica que el valor de `DEBUG_PROPERTY_INFO::bstrValue` es "*no algo*" (NAT). NAT describe una marca de registro en procesadores Intel de 64 bits que indica excepciones especulativas aplazadas.

 DBG_ATTRIB_VALUE_AUTOEXPANDED indica que el valor de `DEBUG_PROPERTY_INFO::bstrValue` ha sido posiblemente expandidas automáticamente.

 DBG_ATTRIB_VALUE_TIMEOUT indica que una evaluación se ha superado el tiempo de espera.

 DBG_ATTRIB_VALUE_RAW_STRING indica que el valor de `DEBUG_PROPERTY_INFO::bstrValue` puede representarse mediante una cadena sin formato.

 DBG_ATTRIB_VALUE_CUSTOM_VIEWER indica que esta propiedad tiene al menos un visor personalizado asociado con él.

 DBG_ATTRIB_ACCESS_NONE indica un objeto que no haya ninguno `public`, `private`, ni `protected` escriba acceso.

 DBG_ATTRIB_ACCESS_PUBLIC indica un objeto que tiene acceso público.

 DBG_ATTRIB_ACCESS_PRIVATE indica un objeto que tiene acceso privado.

 DBG_ATTRIB_ACCESS_PROTECTED indica un objeto que tiene acceso protegido.

 DBG_ATTRIB_ACCESS_FINAL indica un objeto que tiene acceso final.

 Máscara de DBG_ATTRIB_ACCESS_ALL para extraer el acceso a los atributos de `DBG_ATTRIB_FLAGS`.

 DBG_ATTRIB_STORAGE_NONE indica que no hay ningún tipo de almacenamiento especificado.

 DBG_ATTRIB_STORAGE_GLOBAL indica almacenamiento global.

 DBG_ATTRIB_STORAGE_STATIC indica almacenamiento estático.

 Almacenamiento DBG_ATTRIB_STORAGE_REGISTER indica en el registro.

 Los atributos de máscara DBG_ATTRIB_STORAGE_ALL para extraer el almacenamiento de `DBG_ATTRIB_FLAGS`.

 DBG_ATTRIB_TYPE_NONE indica que no hay ningún modificador de tipo.

 DBG_ATTRIB_TYPE_VIRTUAL indica que el tipo de objeto es virtual.

 DBG_ATTRIB_TYPE_CONSTANT indica que el tipo de objeto es constante.

 DBG_ATTRIB_TYPE_SYNCHRONIZED indica que el tipo de objeto está sincronizado.

 DBG_ATTRIB_TYPE_VOLATILE indica que el tipo de objeto es volátil.

 Los atributos de máscara DBG_ATTRIB_TYPE_ALL para extraer el tipo de `DBG_ATTRIB_FLAGS`.

 DBG_ATTRIB_DATA indica que este objeto es un campo de datos.

 DBG_ATTRIB_METHOD indica que este objeto es un método.

 DBG_ATTRIB_PROPERTY indica que este objeto es una propiedad.

 DBG_ATTRIB_CLASS indica que este objeto es una clase.

 DBG_ATTRIB_BASECLASS indica que este objeto es una clase base.

 DBG_ATTRIB_INTERFACE indica que este objeto es una interfaz.

 DBG_ATTRIB_INNERCLASS indica que este objeto es una clase interna.

 DBG_ATTRIB_MOSTDERIVED indica que este objeto es '*más derivado*'. El término "*más derivado*" significa que el tipo real del objeto y no el tipo de su referencia.

 DBG_ATTRIB_CHILD_ALL indica una máscara de `DBG_ATTRIB_DATA` a través de `DBG_ATTRIB_MOSTDERIVED`.

 DBG_ATTRIB_MULTI_CUSTOM_VIEWERS indica que el objeto tiene varios visores personalizados asociados con él.

## <a name="remarks"></a>Comentarios

> [!NOTE]
>  Los valores de esta enumeración no están definidos realmente en el ensamblado de C#. En su lugar, debe copiar las definiciones en el archivo de origen.

 Estas marcas también se usan para filtrar los elementos secundarios de un objeto, por ejemplo, cuando se pasa como argumento a [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md). Los valores se pueden combinar con un bit a bit `OR`.

 El `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` indicador es una indicación para [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] para obtener el [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaz desde el [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaz y llame a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) para obtener una lista de visores personalizados.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)