---
title: IDebugProgram3::ExecuteOnThread ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 201c08352bc5b616298349c52197529ef3f1a7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722660"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Ejecuta el programa depurador. El subproceso se devuelve para proporcionar al depurador información sobre qué subproceso está viendo el usuario al ejecutar el programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT ExecuteOnThread(
   [in] IDebugThread2* pThread)
```

```csharp
int ExecuteOnThread(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parámetros
`pThread`\
[en] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Hay tres maneras diferentes en las que un depurador puede reanudar la ejecución después de detenerse:

- Ejecutar: Cancele cualquier paso anterior y ejecútelo hasta el siguiente punto de interrupción, etc.

- Paso: Cancele cualquier paso antiguo y ejecútelo hasta que se complete el nuevo paso.

- Continuar: vuelva a ejecutar y deje activo cualquier paso antiguo.

  El subproceso `ExecuteOnThread` al que se pasa es útil al decidir qué paso cancelar. Si no conoce el subproceso, ejecutar execute cancela todos los pasos. Con el conocimiento del subproceso, solo necesita cancelar el paso en el subproceso activo.

## <a name="see-also"></a>Vea también
- [Ejecutar](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
