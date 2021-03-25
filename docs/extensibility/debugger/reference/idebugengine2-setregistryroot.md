---
description: Establece la raíz del registro para el motor de depuración (DE).
title: 'IDebugEngine2:: SetRegistryRoot | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f754c12fc19d6ba5ed506ef3b51ee704b4160783
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084940"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
Establece la raíz del registro para el motor de depuración (DE).

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetRegistryRoot( 
   LPCOLESTR pszRegistryRoot
);
```

```csharp
int SetRegistryRoot( 
   string pszRegistryRoot
);
```

## <a name="parameters"></a>Parámetros
`pszRegistryRoot`\
de Raíz del registro que se va a usar.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método permite [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] especificar una raíz del registro alternativa que el de debe usar para obtener la configuración del registro; por ejemplo, "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp".

## <a name="see-also"></a>Consulte también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
