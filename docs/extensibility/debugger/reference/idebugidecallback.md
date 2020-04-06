---
title: IDebugIDECallback ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 585ff354cef9686097325ea4dea25cd08c4cbb1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727827"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Permite que un evaluador de expresiones (EE) muestre un mensaje en la ventana de salida del depurador.

## <a name="syntax"></a>Sintaxis

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta devolución de llamada la implementa el motor de depuración administrado.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Puede ser consumido por un evaluador de expresiones para enviar la salida a la ventana de salida del depurador.

## <a name="methods"></a>Métodos
 Esta interfaz implementa el siguiente método:

|Método|Descripción|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Envía la cadena de mensaje especificada a la ventana de salida del depurador.|

## <a name="requirements"></a>Requisitos
 Encabezado: Ee.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
