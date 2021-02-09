---
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0922d6e6e7d7e4ccc162652427e3f8c584580dd4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929672"
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
