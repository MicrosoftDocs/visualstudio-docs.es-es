---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3efe97518b0952c1207eac97fe9151f36c686f43
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846561"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Especifica la información de un subproceso que se va a recuperar.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
typedef DWORD THREADPROPERTY_FIELDS;
```

```csharp
public enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Campos
 `TPF_ID`\
 Inicialice/use el `dwThreadId` campo de la estructura [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) .

 `TPF_SUSPENDCOUNT`\
 Inicialice/use el `dwSuspendCount` campo de la `THREADPROPERTIE` estructura S.

 `TPF_STATE`\
 Inicialice/use el `dwThreadState` campo de la `THREADPROPERTIE` estructura S.

 `TPF_PRIORITY`\
 Inicialice/use el `bstrPriority` campo de la `THREADPROPERTIE` estructura S.

 `TPF_NAME`\
 Inicialice/use el `bstrName` campo de la `THREADPROPERTIE` estructura S.

 `TPF_LOCATION`\
 Inicialice/use el `bstrLocation` campo de la `THREADPROPERTIE` estructura S.

 `TPF_ALLFIELDS`\
 Especifica todos los campos.

## <a name="remarks"></a>Notas
 Estos valores se pasan como argumento al método [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) para indicar qué campos de la estructura [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) se van a inicializar.

 Estos valores también se usan en `dwFields` el miembro de la `THREADPROPERTIES` estructura para indicar qué campos se usan y son válidos.

 Estas marcas se pueden combinar con una operación bit a bit `OR` .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
