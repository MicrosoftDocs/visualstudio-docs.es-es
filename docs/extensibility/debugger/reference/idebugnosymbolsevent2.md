---
title: IDebugNoSymbolsEvent2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9483c5a434ddfddb3f877111deabea9be6520b05
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726709"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Indica a [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] la interfaz de usuario del depurador que advierta al usuario de que no se podían encontrar símbolos para el ejecutable iniciado.

## <a name="syntax"></a>Sintaxis

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Implementado por motores de depuración [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] y consumido por la interfaz de usuario del depurador.

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
