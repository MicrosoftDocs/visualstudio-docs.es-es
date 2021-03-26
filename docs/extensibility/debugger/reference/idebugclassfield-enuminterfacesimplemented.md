---
description: Crea un enumerador para las interfaces implementadas por esta clase.
title: 'IDebugClassField:: EnumInterfacesImplemented | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1763cbcd0a1c61150a054752c94a42f10127251a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088619"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Crea un enumerador para las interfaces implementadas por esta clase.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumInterfacesImplemented( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumInterfacesImplemented(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parámetros
`ppEnum`\
enuncia Devuelve un objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de interfaces implementadas. Devuelve un valor NULL si no hay ninguna interfaz.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, Devuelve S_OK o devuelve S_FALSE si no hay interfaces implementadas en esta clase. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Cada elemento de la enumeración es un objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que describe una interfaz. Tenga en cuenta que el código no administrado no [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] usa las interfaces como una entidad discreta, por lo que este método siempre devuelve un valor null para el código no administrado [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] .

## <a name="see-also"></a>Consulte también
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
