---
title: Visualizador de tipos y Visor personalizado ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b8def9d28279f601ff488fca457982806629c0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712463"
---
# <a name="type-visualizer-and-custom-viewer"></a>Visualizador de tipos y visor personalizado
Un visualizador de tipos es un componente que muestra un fragmento de datos en un formato específico. El formato depende enteramente de quién implementa el visualizador, ya sea el usuario final o un proveedor externo de visualizadores.

 Un visor personalizado es la parte de un evaluador de expresiones personalizado que muestra un fragmento de datos en un formato específico. Este formato depende totalmente del implementador del visor personalizado, lo que significa que el formato depende del implementador del evaluador de expresiones (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Compatibilidad con visualizadores de tipos en un evaluador de expresiones
 Un EE admite visualizadores de tipos mediante la compatibilidad con un conjunto de interfaces accesibles para los visualizadores: interfaces como [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) e [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Sin embargo, eE no es responsable de implementar el visualizador de tipo en sí: el EE simplemente permite a los visualizadores externos el acceso a su información de tipo. Estos visualizadores pueden enviarse junto con el EE e instalar en el lugar adecuado en Visual Studio, proporcionado por otro proveedor de terceros o incluso por el usuario final.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Compatibilidad con visores personalizados en un evaluador de expresiones
 Un EE también puede admitir visores personalizados en los que el propio EE proporciona el código para ver el tipo de datos. Un visor personalizado implementa el [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfaz, que controla todas las tareas de mostrar los datos en el formato que se desee; el visor tiene control total sobre la pantalla e incluso puede permitir que los datos se modifiquen. Los visores personalizados suministrados por EE vienen con el EE cuando se envía el producto.

## <a name="see-also"></a>Vea también
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
- [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
