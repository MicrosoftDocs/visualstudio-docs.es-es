---
description: Especifica el tipo de mensaje y el motivo.
title: MESSAGETYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b85933896dfff38c2d346fd18144710e2e6fc127
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091531"
---
# <a name="messagetype"></a>MESSAGETYPE
Especifica el tipo de mensaje y el motivo.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
typedef DWORD MESSAGETYPE;
```

```csharp
public enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
```

## <a name="fields"></a>Campos
 `MT_OUTPUTSTRING`\
 Indica que el mensaje se debe enviar a la ventana de salida. Esto es mutuamente excluyente de `MT_MESSAGEBOX` .

 `MT_MESSAGEBOX`\
 Indica que el mensaje debe mostrarse en un cuadro de mensaje. Esto es mutuamente excluyente de `MT_OUTPUTSTRING` .

 `MT_TYPE_MASK`\
 Valor de máscara para aislar el destino del mensaje.

 `MT_REASON_EXCEPTION`\
 Indica que se está mostrando un cuadro de mensaje como resultado de una excepción. Esto es mutuamente excluyente de `MT_REASON_TRACEPOINT` .

 `MT_REASON_TRACEPOINT`\
 Indica que se está mostrando un cuadro de mensaje como resultado de alcanzar un punto de seguimiento. Esto es mutuamente excluyente `MT_REASON_EXCEPTION` .

 `MT_REASON_MASK`\
 Un valor de máscara para aislar el motivo del mensaje que se muestra.

## <a name="remarks"></a>Observaciones
 Estos valores se devuelven desde los métodos [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) y [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) .

 Uno de los valores de razón se puede combinar con uno de los valores de destino de salida mediante una operación bit a bit `OR` .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
