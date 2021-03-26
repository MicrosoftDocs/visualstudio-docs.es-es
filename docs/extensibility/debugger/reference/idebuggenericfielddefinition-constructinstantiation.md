---
description: Construye una instancia de campo dada una matriz de argumentos de tipo.
title: 'IDebugGenericFieldDefinition:: ConstructInstantiation | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4565077357678725a6601ac14c48cfce21ec9101
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063440"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
Construye una instancia de campo dada una matriz de argumentos de tipo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT ConstructInstantiation(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   IDebugField** ppConstructedField
);
```

```csharp
int ConstructInstantiation(
   uint            cArgs,
   IDebugField[]   ppArgs,
   out IDebugField ppConstructedField
);
```

## <a name="parameters"></a>Parámetros
`cArgs`\
de Número de argumentos de la `ppArgs` matriz.

`ppArgs`\
de Matriz que contiene los argumentos de tipo. Los argumentos de tipo deben ser tipos cerrados (genéricos no genéricos o con instancias completas).

`ppConstructedField`\
enuncia Devuelve la interfaz [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa el nuevo campo.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 No se comprueban las restricciones.

## <a name="see-also"></a>Consulte también
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
