---
title: "C&#243;mo: Modelar un terreno en 3D | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
caps.latest.revision: 17
caps.handback.revision: 17
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# C&#243;mo: Modelar un terreno en 3D
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este documento se muestra cómo utilizar el editor del modelo para crear un modelo 3D de terreno.  
  
 En este documento se muestran estas actividades:  
  
-   Agregar objetos a una escena  
  
-   La selección hace anteriores y los puntos  
  
-   Convertir selecciones  
  
-   Mediante la herramienta de **Subdivida la cara**  
  
-   Enmarcar un objeto en la superficie de diseño  
  
## Crear un modelo de pista 3D  
 Puede crear un terreno 3D subdividiendo un plano para crear caras adicionales y, a continuación, manipulando los vértices para crear características de terreno interesantes.  
  
 Cuando termine, el modelo debe tener este aspecto:  
  
 ![Escena 3D que muestra un modelo de terreno](../designers/media/digit-terrain-model.png "Digit\-Terrain\-Model")  
  
 Antes de empezar, asegúrese de que la ventana y **Cuadro de herramientas** de **Propiedades** se muestren.  
  
#### Para crear un modelo de pista 3D  
  
1.  Cree un modelo 3D para ejecutar.  Para obtener información sobre cómo agregar un modelo al proyecto, vea la sección Introducción en [Editor de modelos](../designers/model-editor.md).  
  
2.  Agregue un plano a la escena.  En el **Cuadro de herramientas**, en **Formas**, seleccione **Plano** y muévalo a la superficie de diseño.  
  
    > [!TIP]
    >  Para crear el objeto plano más fácil trabajar con, puede cuadro él en la superficie de diseño.  En el modo de **activada** , seleccione el objeto plano y, en la barra de herramientas del editor, elija el botón de **Objeto de marco** .  
  
3.  Modo de selección de cara enter.  En la barra de herramientas del editor, elija **Seleccionar cara**.  
  
4.  Subdivida el plano.  En modo de selección de nombre, elija el plano una vez para activarlo para la selección y, a continuación de nuevo para seleccionar el sólo cara.  En la barra de herramientas del editor, elija **Subdivida la cara**.  Esto agrega nuevos vértices al plano que división él en cuatro particiones igualmente ordenadas.  
  
5.  Cree más subdivisiones.  Con las nuevas caras todavía seleccionadas, elija **Subdivida la cara** dos veces más.  Esto crea un total de 64 caras.  Al crear más subdivisiones, puede proporcionar más detalles del terreno.  
  
6.  Entre en el modo de selección del punto.  En la barra de herramientas del editor, elija **Seleccionar punto**.  
  
7.  Modifique un punto para crear una característica de terreno.  En modo de selección de punto, seleccione uno de los puntos y, en la barra de herramientas del editor, elija la herramienta de **Traducir** .  Un cuadro que representa el punto aparece en la superficie de diseño.  Use la flecha verde para mover el cuadro y modificar el alto del punto.  Repita este paso para los distintos puntos para crear características de terreno interesantes.  
  
    > [!TIP]
    >  Puede seleccionar varios puntos a la vez para modificarlos de forma uniforme.  
  
 Se completa el modelo de terreno.  A continuación se muestra el modelo final de nuevo, con el sombreado de Phong aplicado:  
  
 ![Escena 3D que muestra un modelo de terreno](../designers/media/digit-terrain-model.png "Digit\-Terrain\-Model")  
  
 Puede utilizar este modelo de terreno para demostrar el efecto del sombreador de degradado que se describe en [Cómo: Crear un sombreador de gradiente basado en geometría](../designers/how-to-create-a-geometry-based-gradient-shader.md).  
  
## Vea también  
 [Editor de modelos](../designers/model-editor.md)