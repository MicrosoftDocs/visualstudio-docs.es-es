---
title: Prueba y depuración de un visualizador | Microsoft Docs
description: Pruebe y depure un visualizador ejecutándolo desde un controlador de prueba (host de desarrollo del visualizador), o bien instalándolo en Visual Studio y llamándolo desde una ventana del depurador.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fa97453d08650b78a02eda873a01afe9e376caec
ms.sourcegitcommit: 4cd3eb514e9fa48e586279e38fe7c2e111ebb304
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2021
ms.locfileid: "113298249"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Procedimiento Prueba y depuración de un visualizador
Cuando se ha escrito un visualizador, es necesario depurarlo y comprobarlo.

Una manera de comprobar un visualizador es instalarlo en Visual Studio y llamarlo desde una ventana del depurador. Vea [Cómo: Instalación de un visualizador](../debugger/how-to-install-a-visualizer.md). Si lo hace, será necesario usar una segunda instancia de Visual Studio para asociar y depurar el visualizador, que se ejecuta en la primera instancia del depurador.

Una manera más fácil de depurar un visualizador es ejecutarlo desde un controlador de prueba. Las API del visualizador facilitan la creación de este tipo de controlador, denominado *host de desarrollo del visualizador*.

>[!NOTE]
> Actualmente, el controlador de prueba solo se admite al llamar al visualizador desde una aplicación de .NET Framework.

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

    Para obtener un ejemplo más completo, consulte [Tutorial: Escritura de un visualizador en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).

## <a name="see-also"></a>Vea también
- [Tutorial: Escritura de un visualizador en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Cómo: instalar un visualizador](../debugger/how-to-install-a-visualizer.md)
- [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)
