---
title: IDebugEngine3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a985acc5a949ead841239d56c8b067967531fb1e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927059"
---
# <a name="idebugengine3"></a>IDebugEngine3
Representa un único motor de depuración (DE) que controla la depuración de uno o más módulos.

## <a name="syntax"></a>Sintaxis

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se implementa mediante un personalizado DE (si admite símbolos) para habilitar el estado de JustMyCode. La interfaz debe ser implementada por el DE si admite símbolos y JustMyCode.

## <a name="notes-for-callers"></a>Notas para llamadores
 El administrador de depuración de la sesión (SDM) llama a esta interfaz para pasar las opciones de usuario para las ubicaciones desde las que se cargan los símbolos. También se llama a para establecer el GUID del motor cuando se crea una instancia (este GUID se basa en las métricas desde el momento del registro del motor). El SDM también llama a esta interfaz para establecer el estado JustMyCode y establecer todas las excepciones conocidas por el depurador en un estado especificado.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos heredados de [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), la `IDebugEngine3` interfaz expone los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Establece la ruta de acceso o las rutas de acceso que utilizará para buscar símbolos de depuración.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Carga los símbolos para todos los módulos a los que todavía no se han cargado los símbolos.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Indica a la información DE JustMyCode.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Establece el DE GUID a partir de las métricas.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Establece todas las excepciones pendientes actualmente en un estado especificado.|

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
