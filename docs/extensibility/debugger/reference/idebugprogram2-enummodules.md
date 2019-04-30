---
title: IDebugProgram2::EnumModules | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumModules
helpviewer_keywords:
- IDebugProgram2::EnumModules
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8de1f98cb6953ba713796e1dbd74de849a0aaf7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917310"
---
# <a name="idebugprogram2enummodules"></a>IDebugProgram2::EnumModules
Recupera una lista de los módulos que este programa se ha cargado y se está ejecutando.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumModules( 
   IEnumDebugModules2** ppEnum
);
```

```csharp
int EnumModules( 
   out IEnumDebugModules2 ppEnum
);
```

#### <a name="parameters"></a>Parámetros
 `ppEnum`

 [out] Devuelve un [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) objeto que contiene una lista de los módulos.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Un módulo es un archivo DLL o un ensamblado y normalmente se incluye en el **módulos** ventana de depuración.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)