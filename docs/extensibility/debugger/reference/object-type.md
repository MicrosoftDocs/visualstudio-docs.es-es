---
title: OBJECT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ffb85a14e42dd57c345481285eb1f776b3866d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714123"
---
# <a name="object_type"></a>Object_Type
Especifica el tipo de un objeto del evaluador de expresiones.

## <a name="syntax"></a>Sintaxis

```cpp
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

```csharp
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

## <a name="fields"></a>Campos
 `OBJECT_TYPE_BOOLEAN`\
 Indica que el objeto es un valor booleano.

 `OBJECT_TYPE_CHAR`\
 Indica que el objeto es un carácter.

 `OBJECT_TYPE_I1`\
 Indica que el objeto es un entero de un byte con signo.

 `OBJECT_TYPE_U1`\
 Indica que el objeto es un entero sin signo de un byte.

 `OBJECT_TYPE_I2`\
 Indica que el objeto es un entero de dos bytes con signo.

 `OBJECT_TYPE_U2`\
 Indica que el objeto es un entero sin signo de dos bytes.

 `OBJECT_TYPE_I4`\
 Indica que el objeto es un entero de cuatro bytes con signo.

 `OBJECT_TYPE_U4`\
 Indica que el objeto es un entero sin signo de cuatro bytes.

 `OBJECT_TYPE_I8`\
 Indica que el objeto es un entero de ocho bytes con signo.

 `OBJECT_TYPE_U8`\
 Indica que el objeto es un entero sin signo de ocho bytes.

 `OBJECT_TYPE_R4`\
 Indica que el objeto es un número de punto flotante de cuatro bytes.

 `OBJECT_TYPE_R8`\
 Indica que el objeto es un número de punto flotante de ocho bytes.

 `OBJECT_TYPE_OBJECT`\
 Indica que el objeto es un objeto.

 `OBJECT_TYPE_NULL`\
 Indica que el objeto es NULL.

 `OBJECT_TYPE_CLASS`\
 Indica que el objeto es una clase.

## <a name="remarks"></a>Observaciones
 Se pasa como argumento a los métodos [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) y [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) .

## <a name="requirements"></a>Requisitos
 Encabezado: EE. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)
