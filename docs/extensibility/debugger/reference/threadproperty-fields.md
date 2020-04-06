---
title: THREADPROPERTY_FIELDS de la Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b31c43187d1136f7a194c42749c430de6cd064a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713397"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Especifica qué información sobre un subproceso se va a recuperar.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_THREADPROPERTY_FIELDS { 
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
public enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Fields
 `TPF_ID`\
 Inicializar/utilizar `dwThreadId` el campo de la estructura [THREADPROPERTIES.](../../../extensibility/debugger/reference/threadproperties.md)

 `TPF_SUSPENDCOUNT`\
 Inicializar/utilizar `dwSuspendCount` el campo `THREADPROPERTIE`de la estructura S.

 `TPF_STATE`\
 Inicializar/utilizar `dwThreadState` el campo `THREADPROPERTIE`de la estructura S.

 `TPF_PRIORITY`\
 Inicializar/utilizar `bstrPriority` el campo `THREADPROPERTIE`de la estructura S.

 `TPF_NAME`\
 Inicializar/utilizar `bstrName` el campo `THREADPROPERTIE`de la estructura S.

 `TPF_LOCATION`\
 Inicializar/utilizar `bstrLocation` el campo `THREADPROPERTIE`de la estructura S.

 `TPF_ALLFIELDS`\
 Especifica todos los campos.

## <a name="remarks"></a>Observaciones
 Estos valores se pasan como argumento al método [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) para indicar qué campos de la estructura [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) se van a inicializar.

 Estos valores también `dwFields` se utilizan `THREADPROPERTIES` en el miembro de la estructura para indicar qué campos se utilizan y son válidos.

 Estas banderas se pueden `OR`combinar con un bit a bit .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
