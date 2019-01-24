---
title: Escriba el visualizador y el visor personalizado | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5319721d57212f4fc853ca99c1544a51d4af878c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732130"
---
# <a name="type-visualizer-and-custom-viewer"></a>Visualizador de tipo y visor personalizado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un visualizador de tipo es un componente que se muestra un fragmento de datos en un formato muy específico. Este formato es completamente depende del implementador del visualizador, ya sea el usuario final o un proveedor de terceros de visualizadores.  
  
 Un visor personalizado es la parte de un evaluador de expresiones personalizado que muestra un fragmento de datos en un formato muy específico. Este formato es completamente depende del implementador del visor personalizado, lo que significa que el formato es responsabilidad del implementador del evaluador de expresiones (EE).  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Compatibilidad con los visualizadores de tipo en un evaluador de expresiones  
 Un EE puede admitir los visualizadores de tipo proporcionando un conjunto de interfaces que puede tener acceso a los visualizadores: las interfaces como [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) y [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Sin embargo, tenga en cuenta que el EE no es responsable de implementar el visualizador de tipo propio: EE permite simplemente visualizadores externos acceso a su información de tipo. Dichos visualizadores se podrían enviar junto con el EE e instalados en el lugar adecuado en Visual Studio, suministrado por otro proveedor de terceros o incluso por el usuario final.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Compatibilidad con visores personalizados de un evaluador de expresiones  
 Un EE también puede admitir los visores personalizados en el que el EE sí proporciona el código para ver el tipo de datos. Un visor personalizado implementa el [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfaz, que controla todas las tareas de mostrando los datos en el mismo formato que se desea; el Visor tiene control total sobre la visualización y aún puede permitir que los datos que se va a modificarse. Los visores personalizados proporcionados por el EE vienen con EE cuando se envía.  
  
## <a name="see-also"></a>Vea también  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)   
 [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

