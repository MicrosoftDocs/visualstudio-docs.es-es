---
title: Procedimiento Probar y depurar un visualizador | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0353234e5a266ca1a344ce7bc304f27d8c3af95
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906289"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Procedimiento Prueba y depuración de un visualizador
Cuando se ha escrito un visualizador, es necesario depurarlo y comprobarlo.

Una manera de comprobar un visualizador es instalarlo en Visual Studio y llamarlo desde una ventana del depurador. Vea [Cómo: Instalación de un visualizador](../debugger/how-to-install-a-visualizer.md). Si lo hace, será necesario usar una segunda instancia de Visual Studio para asociar y depurar el visualizador, que se ejecuta en la primera instancia del depurador.

Una manera más fácil de depurar un visualizador es ejecutarlo desde un controlador de prueba. Las API del visualizador facilitan la creación de este tipo de controlador, denominado *host de desarrollo del visualizador*.

### <a name="to-create-a-visualizer-development-host"></a>Para crear un host de desarrollo del visualizador

1. En la clase del depurador, incluya un método estático que cree un objeto <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> y llame al método Show:

    ```csharp
    public static void TestShowVisualizer(object objectToVisualize)
    {
        VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
        myHost.ShowVisualizer();
    }
    ```

    Los parámetros utilizados para construir el host son el objeto de datos que aparecerá en el visualizador (`objectToVisualize`) y el tipo de la clase del depurador.

2. Agregue la instrucción siguiente para llamar a `TestShowVisualizer`. Si el visualizador se creó en una biblioteca de clases, es necesario crear un ejecutable que llame a la biblioteca de clases y coloque esta instrucción en el ejecutable:

    ```csharp
    DebuggerSide.TestShowVisualizer(myString);
    ```

    Para obtener un ejemplo más completo, vea [Tutorial: Escribir un visualizador en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).

## <a name="see-also"></a>Vea también
- [Tutorial: Escritura de un visualizador en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Cómo: instalar un visualizador](../debugger/how-to-install-a-visualizer.md)
- [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)
