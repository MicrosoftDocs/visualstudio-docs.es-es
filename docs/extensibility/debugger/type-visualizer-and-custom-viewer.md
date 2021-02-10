---
title: Visualizador de tipos y visor personalizado | Microsoft Docs
description: Obtenga información sobre los componentes del visualizador de tipos y los visores personalizados, que muestran los datos en un formato específico y las diferencias entre ellos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3fe647d8a5a4bf3485b1d7b9f7b9699997bf3da6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965439"
---
# <a name="type-visualizer-and-custom-viewer"></a>Visualizador de tipos y visor personalizado
Un visualizador de tipos es un componente que muestra un fragmento de datos en un formato específico. El formato es completamente el que implementa el visualizador, ya sea el usuario final o un proveedor de visualizadores de terceros.

 Un visor personalizado es la parte de un evaluador de expresiones personalizado que muestra un fragmento de datos en un formato específico. Este formato es totalmente el que el implementador del visor personalizado, lo que significa que el formato es el que corresponde al implementador del evaluador de expresiones (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Compatibilidad con los visualizadores de tipos en un evaluador de expresiones
 Un de EE admite visualizadores de tipos mediante la compatibilidad con un conjunto de interfaces accesibles para los visualizadores: interfaces como [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) y [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Sin embargo, el EE no es responsable de implementar el propio visualizador de tipos: EE simplemente permite que los visualizadores externos tengan acceso a su información de tipo. Estos visualizadores pueden enviarse junto con el EE e instalarse en el lugar adecuado de Visual Studio, proporcionado por otro proveedor de terceros o incluso por el usuario final.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Compatibilidad con visores personalizados en un evaluador de expresiones
 EE también puede admitir visores personalizados en los que el propio EE proporciona el código para ver el tipo de datos. Un visor personalizado implementa la interfaz [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) , que controla todas las tareas de mostrar los datos en el formato que se desee; el visor tiene control total sobre la pantalla e incluso puede permitir que se modifiquen los datos. Los visores personalizados proporcionados por EE vienen a la hora de enviar el producto.

## <a name="see-also"></a>Vea también
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
- [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
