---
description: Este método hace que un programa esté disponible para los motores de depuración (DEs) y el administrador de depuración de la sesión.
title: IDebugProgramPublisher2::P ublishProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba1ac74813ea0c3ae5b7eadb26d540b7bfe20707
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065234"
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
Este método hace que un programa esté disponible para los motores de depuración (DEs) y el administrador de depuración de la sesión.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT PublishProgram(
   CONST_GUID_ARRAY Engines,
   LPCOLESTR        szFriendlyName,
   IUnknown*        pDebuggeeInterface
);
```

```csharp
int PublishProgram(
   CONST_GUID_ARRAY Engines,
   string           szFriendlyName,
   object           pDebuggeeInterface
);
```

## <a name="parameters"></a>Parámetros
`Engines`\
de Una matriz de GUID para DEs que se puede iniciar o adjuntar a este programa.

`szFriendlyName`\
de Nombre descriptivo para el programa (aparece en los menús o cuadros de diálogo que se presentan al usuario).

`pDebuggeeInterface`\
[in] `IUnknown` interfaz para el programa (este valor se usa como una cookie para identificar el programa de forma exclusiva; este mismo valor se usa para "anular la publicación" del programa)

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Para que un programa deje de estar disponible para la depuración, llame a [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).

## <a name="see-also"></a>Consulte también
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)
