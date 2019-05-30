---
title: IDebugAlias2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abd220cd8c67318981fda79d3be8a0014ab61de1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321725"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Representa un alias para una variable numérico y permite que un evaluador de expresiones (EE) para obtener el dominio de aplicación para el alias.

## <a name="syntax"></a>Sintaxis

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se implementa mediante el motor de depuración administrado (DE).

## <a name="methods"></a>Métodos
 Además de los métodos en el [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interfaz, esta interfaz implementa el método siguiente:

|Método|Descripción|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Recupera el identificador del dominio de aplicación.|

## <a name="remarks"></a>Comentarios
 Un alias es un número decimal en forma de cadena seguido por el carácter #, por ejemplo, 1001#.

## <a name="requirements"></a>Requisitos
 Encabezado: Ee.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll