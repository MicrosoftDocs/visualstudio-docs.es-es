---
description: Representa la definición de un campo para un tipo genérico de código administrado.
title: IDebugGenericFieldDefinition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0c9b2a4b9dbdbf5d1b5faefb8dfbf498f873ec01
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063362"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
Representa la definición de un campo para un tipo genérico de código administrado.

## <a name="syntax"></a>Sintaxis

```
IDebugGenericFieldDefinition : IUnknown
```

## <a name="methods"></a>Métodos
 Esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Construye una instancia de campo dada una matriz de argumentos de tipo.|
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Recupera los parámetros de tipo dados el número de parámetros.|
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Recupera el número de parámetros de tipo asociados al campo genérico.|

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
