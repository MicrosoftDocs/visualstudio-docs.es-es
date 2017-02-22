---
title: "C&#243;mo: Crear un sombreador de color b&#225;sico | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
caps.latest.revision: 24
caps.handback.revision: 24
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# C&#243;mo: Crear un sombreador de color b&#225;sico
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este documento se muestra cómo usar el Diseñador de sombras y el lenguaje DGSL \(Directed Graph Shader Language\) para crear un sombreador de color plano.  Este sombreador establece el color final en un valor de color RGB constante.  
  
 En este documento se muestran estas actividades:  
  
-   Quitar nodos de un gráfico  
  
-   Agregar nodos a un gráfico  
  
-   Establecer las propiedades del nodo  
  
-   Conectar nodos  
  
## Crear un sombreador de color plano  
 Puede implementar un sombreador de color plano escribiendo el valor de color de una constante de color RGB en el color del resultado final.  
  
 Antes de empezar, asegúrese de que se muestran la ventana **Propiedades** y el **Cuadro de herramientas**.  
  
#### Para crear un sombreador de color plano  
  
1.  Cree un sombreador DGSL con el que trabajar.  Para obtener información sobre cómo agregar un sombreador DGSL al proyecto, vea la sección Introducción de [Diseñador de sombras](../designers/shader-designer.md).  
  
2.  Elimine el nodo **Color de punto**.  Use la herramienta **Seleccionar** para seleccionar el nodo **punto Color** y, a continuación, en la barra de menús, elija **Editar**, **Eliminar**.  
  
3.  Agregue un nodo de **Constante de color** al gráfico.  En el **Cuadro de herramientas**, en **Constantes**, seleccione **Constante de color** y muévala a la superficie de diseño.  
  
4.  Especifique un valor de color para el nodo **Constante de color**.  Utilice la herramienta **Seleccionar** para seleccionar el nodo **Constante de color** y, en la ventana **Propiedades**, en la propiedad **Resultados**, especifique un valor de color.  Para el naranja, especifique un valor \(1,0, 0,5, 0,2, 1,0\).  
  
5.  Conectar la constante de color al color final.  Para crear las conexiones, mueva el terminal **RGB** del nodo **Constante de color** al terminal **RGB** del nodo **Color final** y, después, mueva el terminal **Alpha** del nodo **Constante de color** al terminal **Alpha** del nodo **Color final**.  Estas conexiones establecen color final en la constante de color definida en el paso anterior.  
  
 La siguiente ilustración muestra el gráfico de sombreador completo y una vista previa del sombreador aplicado a un cubo.  
  
> [!NOTE]
>  En la ilustración, el color naranja se especificó para ilustrar mejor el efecto del sombreador.  
  
 ![Gráfico de sombreador y su resultado en un modelo 3D](../designers/media/digit-flat-color-effect.png "Digit\-Flat\-Color\-Effect")  
  
 Algunas formas podrían dar mejores vistas previas para algunos los sombreadores.  Para obtener más información sobre cómo obtener una vista previa de los sombreadores en el Diseñador de sombras, vea [Diseñador de sombras](../designers/shader-designer.md).  
  
## Vea también  
 [Cómo: Aplicar un sombreador a un modelo 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Cómo: Exportar un sombreador](../designers/how-to-export-a-shader.md)   
 [Diseñador de sombras](../designers/shader-designer.md)   
 [Nodos del Diseñador de sombras](../designers/shader-designer-nodes.md)