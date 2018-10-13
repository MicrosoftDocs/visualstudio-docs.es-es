---
title: IDebugEngine3 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b316816c3e49d57cd4aa2d0229a00ad1e28173d0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222552"
---
# <a name="idebugengine3"></a>IDebugEngine3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Representa un único motor de depuración (DE) que controla la depuración de uno o varios módulos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa mediante una DE personalizado (si lo admite símbolos) para habilitar el estado de JustMyCode. Esta interfaz debe implementarse mediante la DE si es compatible con los símbolos y JustMyCode.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El Administrador de depuración (SDM) para pasar de las opciones de usuario para las ubicaciones desde las que se va a cargar los símbolos de sesión llama a esta interfaz. También se llama para establecer el GUID del motor de cuando se crea una instancia (este GUID se basa en las métricas desde el momento del registro del motor). El SDM también llama a esta interfaz para establecer el estado de JustMyCode y establecer todas las excepciones que se conoce el depurador a un estado específico.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos heredados de [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), el `IDebugEngine3` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Establece la ruta de acceso o rutas de acceso que va a usar para buscar la DE los símbolos de depuración.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Carga los símbolos para todos los módulos que aún no ha tenido sus símbolos cargados.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Indica a la DE la información de JustMyCode.|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Establece el GUID DE alguna de las métricas.|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Establecer todas las excepciones pendientes actualmente en un estado especificado.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

