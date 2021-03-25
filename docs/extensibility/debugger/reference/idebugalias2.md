---
description: Representa un alias numérico para una variable y permite que un evaluador de expresiones (EE) obtenga el dominio de aplicación para el alias.
title: IDebugAlias2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6ca97fbe23e9b0c84c39e591c0fd9cfb997fca5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059046"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Representa un alias numérico para una variable y permite que un evaluador de expresiones (EE) obtenga el dominio de aplicación para el alias.

## <a name="syntax"></a>Sintaxis

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se implementa mediante el motor DE depuración administrada (DE).

## <a name="methods"></a>Métodos
 Además de los métodos de la interfaz [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) , esta interfaz implementa el método siguiente:

|Método|Descripción|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Recupera el identificador del dominio de aplicación.|

## <a name="remarks"></a>Observaciones
 Un alias es un número decimal en forma de cadena seguido del carácter #, por ejemplo, 1001 #.

## <a name="requirements"></a>Requisitos
 Encabezado: EE. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
