---
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
ms.openlocfilehash: 1287af4b1afb328e3b843bae0ae93284fe8386c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915503"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
Extiende los tipos de campos que están disponibles para admitir los genéricos de código administrado.

## <a name="syntax"></a>Sintaxis

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
