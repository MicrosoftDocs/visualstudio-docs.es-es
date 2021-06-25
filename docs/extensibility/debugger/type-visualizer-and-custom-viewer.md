---
title: Visualizador de tipos y Visor personalizado | Microsoft Docs
description: Obtenga información sobre los componentes del visualizador de tipos y los visores personalizados, que muestran los datos en un formato específico, y las diferencias entre ellos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c18bb49c740362d42a4a54bf52f6998629acb0c0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904427"
---
# <a name="type-visualizer-and-custom-viewer"></a>Visualizador de tipos y visor personalizado
Un visualizador de tipos es un componente que muestra un fragmento de datos en un formato específico. El formato es totalmente de quién implementa el visualizador, ya sea el usuario final o un proveedor de visualizadores de terceros.

 Un visor personalizado es la parte de un evaluador de expresiones personalizadas que muestra un fragmento de datos en un formato específico. Este formato es totalmente del implementador del visor personalizado, lo que significa que el formato es del implementador del evaluador de expresiones (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Compatibilidad con visualizadores de tipos en un evaluador de expresiones
 Una EE admite visualizadores de tipos al admitir un conjunto de interfaces accesibles para los visualizadores: interfaces como [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) e [IEEVisualizerDataProvider.](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) Sin embargo, el EE no es responsable de implementar el visualizador de tipos en sí: la EE simplemente permite que los visualizadores externos accedan a su información de tipo. Estos visualizadores pueden enviarse junto con el EE e instalarse en el lugar adecuado en Visual Studio, proporcionado por otro proveedor de terceros o incluso por el usuario final.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Compatibilidad con visores personalizados en un evaluador de expresiones
 Una EE también puede admitir visores personalizados en los que el propio EE proporciona el código para ver el tipo de datos. Un visor personalizado implementa la [interfaz IDebugCustomViewer,](../../extensibility/debugger/reference/idebugcustomviewer.md) que controla todas las tareas de mostrar los datos en el formato deseado; el visor tiene control total sobre la pantalla e incluso puede permitir que se modifiquen los datos. Los visores personalizados proporcionados por ee. UU. vienen con la EE cuando se envía el producto.

## <a name="see-also"></a>Consulta también
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
- [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
