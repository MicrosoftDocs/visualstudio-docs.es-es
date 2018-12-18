---
title: Escriba el visualizador y el visor personalizado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5cf2cc9c8f89ed0ecc7935f9afa8e096f05a840
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276499"
---
# <a name="type-visualizer-and-custom-viewer"></a>Visualizador de tipo y visor personalizado
Un visualizador de tipo es un componente que se muestra un fragmento de datos en un formato específico. El formato es completamente hasta que implementa el visualizador, ya sea el usuario final o un proveedor de terceros de visualizadores.  
  
 Un visor personalizado es la parte de un evaluador de expresiones personalizado que muestra un fragmento de datos en un formato específico. Este formato es completamente depende del implementador del visor personalizado, lo que significa que el formato es responsabilidad del implementador del evaluador de expresiones (EE).  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Compatibilidad con los visualizadores de tipo en un evaluador de expresiones  
 Un EE es compatible con los visualizadores de tipo proporcionando un conjunto de interfaces que puede tener acceso a los visualizadores: las interfaces como [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) y [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Sin embargo, no es responsable de implementar el visualizador de tipo propio EE: EE permite simplemente visualizadores externos acceso a su información de tipo. Dichos visualizadores se podrían enviar junto con el EE e instalados en el lugar adecuado en Visual Studio, suministrado por otro proveedor de terceros o incluso por el usuario final.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Compatibilidad con visores personalizados de un evaluador de expresiones  
 Un EE también puede admitir los visores personalizados en el que el EE sí proporciona el código para ver el tipo de datos. Un visor personalizado implementa el [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfaz, que controla todas las tareas de mostrando los datos en el mismo formato que se desea disponer el Visor tiene control total sobre la visualización y puede incluso permitir que los datos se puede modificar. Los visores personalizados proporcionados por el EE vienen con EE cuando se envía.  
  
## <a name="see-also"></a>Vea también  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)   
 [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)