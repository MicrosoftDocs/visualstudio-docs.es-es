---
title: IDebugProgram2::GetDebugProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e18aa5611e7440322e08828060714b4fad954b89
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870441"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Obtiene las propiedades del programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetDebugProperty( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty( 
   out IDebugProperty2 ppProperty
);
```

#### <a name="parameters"></a>Parámetros
 `ppProperty`

 [out] Devuelve un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa las propiedades del programa.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Las propiedades que devuelve este método son específicas del programa. Si el programa necesita devolver más de una propiedad, el [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto devuelto por este método es un contenedor de propiedades adicionales y una llamada a la [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) método devuelve un lista de todas las propiedades.

 Un programa puede exponer cualquier número y tipo de propiedades adicionales que se pueden describir mediante el `IDebugProperty2` interfaz. Un IDE puede mostrar las propiedades adicionales del programa mediante una interfaz de usuario del explorador de propiedades genéricas.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)