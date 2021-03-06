---
description: Obtiene las propiedades del programa.
title: 'IDebugProgram2:: Getdebugproperty (| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60e551829a1f424a9bb7f89642f1d692db8d8032
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075983"
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

## <a name="parameters"></a>Parámetros
`ppProperty`\
enuncia Devuelve un objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa las propiedades del programa.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Las propiedades devueltas por este método son específicas del programa. Si el programa necesita devolver más de una propiedad, el objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) devuelto por este método es un contenedor de propiedades adicionales y al llamar al método [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) se devuelve una lista de todas las propiedades.

 Un programa puede exponer cualquier número y tipo de propiedades adicionales que se pueden describir a través de la `IDebugProperty2` interfaz. Un IDE puede mostrar las propiedades del programa adicional a través de una interfaz de usuario del explorador de propiedades genérica.

## <a name="see-also"></a>Consulte también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
