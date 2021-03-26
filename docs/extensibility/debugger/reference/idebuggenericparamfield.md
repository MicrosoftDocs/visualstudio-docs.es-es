---
description: Representa un parámetro para un tipo genérico de código administrado.
title: IDebugGenericParamField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2dc01aaf3485e89ac32b4a4fd86c7491a1f96853
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091934"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
Representa un parámetro para un tipo genérico de código administrado.

## <a name="syntax"></a>Sintaxis

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Se utiliza para la compatibilidad de genéricos.

## <a name="methods"></a>Métodos
 Además de los métodos de la interfaz [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , esta interfaz implementa los siguientes métodos:

|Método|Descripción|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Devuelve el número de restricciones que están asociadas a este parámetro genérico.|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Recupera las restricciones que están asociadas a este parámetro genérico.|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Recupera las marcas para este parámetro genérico.|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Recupera el índice de este parámetro genérico.|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Recupera el nombre de este parámetro genérico.|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Recupera el tipo o el propietario del método de este parámetro genérico.|

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
