---
description: Permite consultar información sobre el equipo de destino.
title: IDebugWindowsComputerPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fd2d499fad2e05a8f295e2c087289fcb9477f90f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083484"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
Permite consultar información sobre el equipo de destino.

## <a name="syntax"></a>Sintaxis

```
IDebugWindowsComputerPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz la implementan los objetos de puerto del administrador de depuración de sesión.

## <a name="methods"></a>Métodos
 En la tabla siguiente se muestran los métodos de `IDebugWindowsComputerPort2` .

|Método|Descripción|
|------------|-----------------|
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Recupera información sobre el equipo en el que se ejecuta el depurador.|

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
