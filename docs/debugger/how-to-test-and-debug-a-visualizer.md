---
title: "C&#243;mo: Comprobar y depurar un visualizador | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurar [Visual Studio], visualizadores"
  - "visualizadores, depurar"
  - "visualizadores, pruebas"
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Comprobar y depurar un visualizador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se ha escrito un visualizador, es necesario depurarlo y comprobarlo.  
  
 Una manera de comprobar un visualizador es instalarlo en Visual Studio y llamarlo desde una ventana del depurador. \(Vea [Cómo: Instalar un visualizador](../debugger/how-to-install-a-visualizer.md).\) Si lo hace, será necesario usar una segunda instancia de Visual Studio para asociar y depurar el visualizador, que se ejecuta en la primera instancia del depurador.  
  
 Una manera más fácil de depurar un visualizador es ejecutarlo desde un controlador de prueba.  Las API del visualizador facilitan la creación de este tipo de controlador, denominado *host de desarrollo del visualizador*.  
  
### Para crear un host de desarrollo del visualizador  
  
1.  En la clase del depurador, incluya un método estático que cree un objeto <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> y llame al método Show:  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     Los parámetros utilizados para construir el host son el objeto de datos que aparecerá en el visualizador \(`objectToVisualize`\) y el tipo de la clase del depurador.  
  
2.  Agregue la instrucción siguiente para llamar a `TestShowVisualizer`.  Si el visualizador se creó en una biblioteca de clases, es necesario crear un ejecutable que llame a la biblioteca de clases y coloque esta instrucción en el ejecutable:  
  
    ```  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     Para obtener un ejemplo más completo, vea [Tutorial: Escribir un visualizador en C\#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
## Vea también  
 [Tutorial: Escribir un visualizador en C\#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Cómo: Instalar un visualizador](../debugger/how-to-install-a-visualizer.md)   
 [Visualizadores](../debugger/create-custom-visualizers-of-data.md)