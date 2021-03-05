---
description: Determina si el administrador de depuración de sesión (SDM) puede desasociar el proceso.
title: 'IDebugProcess2:: CanDetach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92e876d5642cf8a4b7b60f5119839e64959f296e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151680"
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
Determina si el administrador de depuración de sesión (SDM) puede desasociar el proceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK.` devuelve `S_FALSE` si el depurador no se puede desasociar del proceso. De lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
