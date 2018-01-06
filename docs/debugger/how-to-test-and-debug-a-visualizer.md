---
title: "Cómo: probar y depurar un visualizador | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 75102abacbf93c90b6c24d2884224dd9dd1e1bae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Cómo: Comprobar y depurar un visualizador
Cuando se ha escrito un visualizador, es necesario depurarlo y comprobarlo.  
  
 Una manera de comprobar un visualizador es instalarlo en Visual Studio y llamarlo desde una ventana del depurador. (Consulte [Cómo: instalar un visualizador](../debugger/how-to-install-a-visualizer.md).) Si lo hace, será necesario usar una segunda instancia de Visual Studio para asociar y depurar el visualizador, que se ejecuta en la primera instancia del depurador.  
  
 Una manera más fácil de depurar un visualizador es ejecutarlo desde un controlador de prueba. Las API del visualizador facilitan la creación de controlador que se denomina la *host de desarrollo del visualizador*.  
  
### <a name="to-create-a-visualizer-development-host"></a>Para crear un host de desarrollo del visualizador  
  
1.  En la clase del depurador, incluya un método estático que cree un objeto <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> y llame al método Show:  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     Los parámetros utilizados para construir el host son el objeto de datos que aparecerá en el visualizador (`objectToVisualize`) y el tipo de la clase del depurador.  
  
2.  Agregue la instrucción siguiente para llamar a `TestShowVisualizer`. Si el visualizador se creó en una biblioteca de clases, es necesario crear un ejecutable que llame a la biblioteca de clases y coloque esta instrucción en el ejecutable:  
  
    ```  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     Para obtener un ejemplo más completo, vea [Tutorial: escribir un visualizador en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Escribir un visualizador en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Cómo: instalar un visualizador](../debugger/how-to-install-a-visualizer.md)   
 [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)