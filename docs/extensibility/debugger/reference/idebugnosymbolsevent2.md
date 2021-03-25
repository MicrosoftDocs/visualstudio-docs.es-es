---
description: Indica a la interfaz de usuario del depurador de Visual Studio que avise al usuario de que no se pudieron encontrar símbolos para el ejecutable iniciado.
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7a060436575d51710fcef9c444ac843aa56195d0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058409"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Indica [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] a la interfaz de usuario del depurador que avise al usuario de que no se pudieron encontrar símbolos para el ejecutable iniciado.

## <a name="syntax"></a>Sintaxis

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Implementado por los motores de depuración y consumido por la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaz de usuario del depurador.

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
