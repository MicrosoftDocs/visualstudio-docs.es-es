---
description: Representa un campo dinámico para un objeto IDebugBinder.
title: IDebugDynamicFieldCOMPlus | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus interface
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27fc3fb25b738db20d480a7a4542884dcb76123a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154035"
---
# <a name="idebugdynamicfieldcomplus"></a>IDebugDynamicFieldCOMPlus
Representa un campo dinámico para un objeto [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .

## <a name="syntax"></a>Syntax

```
IDebugDynamicFieldCOMPlus : IDebugDynamicField
```

## <a name="methods"></a>Métodos
 Además de los métodos de la interfaz [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) , esta interfaz implementa los siguientes métodos:

|Método|Descripción|
|------------|-----------------|
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|Recupera un tipo a partir de su tipo primitivo.|
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|Recupera un tipo a partir de su token.|

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
