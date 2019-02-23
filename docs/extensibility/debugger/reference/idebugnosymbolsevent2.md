---
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0850f043d763077ef9a33ad35e82ad924574b6d8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56721321"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Las señales del [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] la interfaz de usuario para advertir al usuario que no se encontró para el ejecutable iniciado los símbolos del depurador.

## <a name="syntax"></a>Sintaxis

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Implementado por los motores de depuración y utilizado por el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] la interfaz de usuario del depurador.

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll