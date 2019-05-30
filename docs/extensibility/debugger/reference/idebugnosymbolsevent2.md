---
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dadd4547d5b0f691b454a98ba714abea9bf6f058
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323715"
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