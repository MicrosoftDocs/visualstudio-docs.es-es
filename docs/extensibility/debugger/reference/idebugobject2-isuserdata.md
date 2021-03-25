---
description: Determina si el objeto representa datos de usuario.
title: 'IDebugObject2:: IsUserData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 485583c0d6ef8ac42b78612e68995462ef900795
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053729"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Determina si el objeto representa datos de usuario.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsUserData(
   BOOL* pfUser
);
```

```csharp
int IsUserData(
   out int pfUser
);
```

## <a name="parameters"></a>Parámetros
`pfUser`\
enuncia Devuelve un valor distinto de cero ( `TRUE` ) si el objeto representa datos de usuario; cero ( `FALSE` ) si no lo es.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Los datos de usuario son cualquier objeto que forme parte de un módulo designado como JustMyCode (una opción configurable por el usuario que marque un módulo como código de usuario y, por tanto, sea visible en un seguimiento de la pila).

## <a name="see-also"></a>Consulte también
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
