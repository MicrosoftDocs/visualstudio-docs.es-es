---
description: Extiende los tipos de campos que están disponibles para admitir los genéricos de código administrado.
title: IDebugExtendedField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5da66ddab0f485587ac5779187384a749459419e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152109"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
Extiende los tipos de campos que están disponibles para admitir los genéricos de código administrado.

## <a name="syntax"></a>Syntax

```
IDebugExtendedField : IDebugField
```

## <a name="methods"></a>Métodos
 Además de los métodos de la interfaz [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , esta interfaz implementa los siguientes métodos:

|Método|Descripción|
|------------|-----------------|
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Recupera el tipo de campo extendido especificado.|
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Determina si el campo representa un tipo cerrado.|

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
