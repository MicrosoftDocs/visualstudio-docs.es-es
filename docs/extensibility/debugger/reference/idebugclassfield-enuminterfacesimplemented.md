---
title: IDebugClassField::EnumInterfacesImplementado ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91d9cac6b695ba2a0d34da776fa79ba62ba2e015
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734485"
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
[fuera] Devuelve un [objeto IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de interfaces implementadas. Devuelve un valor nulo si no hay interfaces.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK o devuelve S_FALSE si no hay interfaces implementadas en esta clase. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Cada elemento de la enumeración es un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto que describe una interfaz. Tenga en [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] cuenta que el código no administrado no usa interfaces como [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] una entidad discreta, por lo que este método siempre devuelve un valor nulo para el código no administrado.

## <a name="see-also"></a>Vea también
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
