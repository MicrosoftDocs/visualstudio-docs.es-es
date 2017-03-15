---
title: "Visualizador de tipo y el visor personalizado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], de visor personalizado"
  - "depurar [SDK de depuración], Visualizador de tipo"
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Visualizador de tipo y el visor personalizado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un visualizador de tipo es un componente que muestra un fragmento de datos en un formato muy específico.  Este formato depende totalmente del implementador del visualizador, si el usuario final o un tercero proveedor de visualizadores.  
  
 Un visor personalizado es la parte de un evaluador de expresiones personalizado que muestra un fragmento de datos en un formato muy específico.  Este formato depende totalmente del implementador de visor personalizado, lo que significa que el formato depende del implementador del evaluador de expresiones \(EE\).  
  
## Compatibilidad con los visualizadores escrito en una expresión Evaluador  
 Aa puede admitir los visualizadores de tipo proporcionando un conjunto de interfaces accesibles a los visualizadores: interfaces como [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) y [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md).  Observe, sin embargo, que aa no es responsable de implementar el visualizador propio de tipo: aa permite simplemente el acceso externo de los visualizadores a su información de tipo.  Tales visualizadores se pueden enviar junto con aa e instalar en el lugar adecuado en Visual Studio, proporcionado por otro proveedor de terceros o incluso el usuario final.  
  
## Compatibilidad con los visores personalizados en un evaluador de expresiones  
 Aa también puede admitir los visores personalizados en los que las fuentes de aa propio el código para ver el tipo de datos.  Un visor personalizado implementa la interfaz de [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) , en la que controla todos los deberes de mostrar los datos se desea cualquier formato; el visor tiene el control completo sobre la presentación y puede incluso se puedan modificar los datos.  Cualquier visor personalizado proporcionado por aa viene con aa cuando se envía el producto.  
  
## Vea también  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)   
 [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)