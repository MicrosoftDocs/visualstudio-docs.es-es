---
description: Extiende el IDebugTypeFieldBuilder para poder crear tipos de matriz.
title: IDebugTypeFieldBuilder2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48bdc4f1bb2668b83da3b042df194e73045e45fc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083523"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Extiende el **IDebugTypeFieldBuilder** para poder crear tipos de matriz.

## <a name="syntax"></a>Sintaxis

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Notas para llamadores
 Esta interfaz se puede obtener del proveedor de símbolos.

## <a name="methods"></a>Métodos
 Además de los métodos de la interfaz [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) , esta interfaz implementa el método siguiente:

|Método|Descripción|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Crea una matriz del tipo y el tamaño especificados.|

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
