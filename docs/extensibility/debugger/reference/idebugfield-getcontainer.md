---
title: IDebugField::GetContainer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetContainer
helpviewer_keywords:
- IDebugField::GetContainer method
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 283e23a70b95e3882569dbb18dda7ba365b8b765
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62919488"
---
# <a name="idebugfieldgetcontainer"></a>IDebugField::GetContainer
Este método obtiene el contenedor de un campo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetContainer( 
   IDebugContainerField** ppContainerField
);
```

```csharp
int GetContainer(
   out IDebugContainerField ppContainerField
);
```

#### <a name="parameters"></a>Parámetros
 `ppContainerField`

 [out] Devuelve el contenedor, tal como está representada por la [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaz.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Si este campo no tiene un contenedor, el valor devuelto `ppContainerField` será un valor null.

## <a name="see-also"></a>Vea también
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)