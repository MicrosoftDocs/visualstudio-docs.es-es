---
title: IDebugEngine3 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 291f5ca6f945abe9e0322839eb80c38b60674ce4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine3"></a>IDebugEngine3
Representa un motor de depuración (Alemania) que controla la depuración de uno o varios módulos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa mediante un Alemania personalizado (si lo admite los símbolos) para habilitar el estado de JustMyCode. Esta interfaz se debe implementar en la DE si es compatible con símbolos y JustMyCode.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El Administrador de sesión de depuración (SDM) para pasar de opciones de usuario para las ubicaciones desde las que se va a cargar los símbolos llama a esta interfaz. También se llama para establecer el GUID del motor de cuando se crea una instancia (este GUID se basa en las métricas desde el momento del registro de motor). El SDM también llama a esta interfaz para establecer el estado de JustMyCode y establecer todas las excepciones que se conoce por el depurador a un estado específico.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos heredados de [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), el `IDebugEngine3` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Establece la ruta o rutas de acceso que la DE usará para buscar símbolos de depuración.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Carga los símbolos para todos los módulos que aún no ha tenido sus símbolos cargados.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Indica a la DE la información de JustMyCode.|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Establece el GUID DE las métricas.|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Establecer todas las excepciones pendientes actualmente a un estado específico.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)