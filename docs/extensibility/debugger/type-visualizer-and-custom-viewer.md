---
title: Escriba visualizador y el visor personalizado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80798887beee6116b3a93b5d8ec86b14269b5475
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="type-visualizer-and-custom-viewer"></a>Visualizador de tipo y el visor personalizado
Un visualizador de tipo es un componente que se muestra un fragmento de datos en un formato muy específico. Este formato es completamente depende del implementador del visualizador, ya sea el usuario final o un proveedor de terceros de visualizadores.  
  
 Un visor personalizado es la parte de un evaluador de expresiones personalizado que muestra un fragmento de datos en un formato muy específico. Este formato es completamente depende del implementador del visor personalizado, lo que significa que el formato es responsabilidad del implementador del evaluador de expresiones (EE).  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Compatibilidad con los visualizadores de tipo en un evaluador de expresiones  
 Un EE puede admitir los visualizadores de tipo ya admite un conjunto de interfaces que puede tener acceso a los visualizadores: las interfaces como [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) y [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Sin embargo, tenga en cuenta que no es responsable de implementar el visualizador de tipo propio EE: EE simplemente permite visualizadores externos el acceso a su información de tipo. Tales visualizadores podrían se envía junto con lo EE e instalar en el lugar adecuado en Visual Studio, suministrado por otro proveedor de terceros o incluso por el usuario final.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Compatibilidad con los visores personalizados en un evaluador de expresiones  
 También puede disponer de un EE visores personalizados en el que los EE propio proporciona el código para ver el tipo de datos. Un visor personalizado implementa el [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfaz, que controla todas las tareas de mostrar los datos en el mismo formato que se desea; el Visor tiene control total sobre la visualización e incluso puede permitir que los datos que se va a modificarse. Los visores personalizados proporcionados por el EE vienen con EE cuando se envió el producto.  
  
## <a name="see-also"></a>Vea también  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)   
 [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)