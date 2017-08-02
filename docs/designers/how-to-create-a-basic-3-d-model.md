---
title: "C&#243;mo: Crear un modelo 3D b&#225;sico | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
caps.latest.revision: 18
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 18
---
# C&#243;mo: Crear un modelo 3D b&#225;sico
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este documento se muestra cómo utilizar el editor del modelo para crear un modelo 3D básico.  
  
 En este documento se muestran estas actividades:  
  
-   Agregar objetos a una escena  
  
-   La selección hace anteriores y los bordes  
  
-   Convertir selecciones  
  
-   Mediante las herramientas de **Subdivida la cara** y de **Muestra el nombre**  
  
-   Mediante el comando de **Triangular**  
  
## Crear un modelo 3D básico  
 Puede utilizar el editor modelo para crear y modificar modelos 3D y escenas para el juego o la aplicación.  Los pasos siguientes muestran cómo utilizar el editor del modelo para crear un modelo 3D simplificado de una casa.  Un modelo simplificado se puede utilizar como activos finales de una imagen de sustitución que todavía se están creando, como malla para la detección de un conflicto, o un modelo de bajo\- detalle que se utilizará cuando el objeto que representa es muy por beneficiarse de una representación más detallada.  
  
 Cuando termine, el modelo debe tener este aspecto:  
  
 ![El modelo completado de la casa simplificada](~/docs/designers/media/gfx_model_demo_house_final.png "gfx\_model\_demo\_house\_final")  
  
 Antes de empezar, asegúrese de que la ventana y **Cuadro de herramientas** de **Propiedades** se muestren.  
  
#### Para crear un modelo 3D simplificado de una casa  
  
1.  Cree un modelo 3D para ejecutar.  Para obtener información sobre cómo agregar un modelo al proyecto, vea la sección Introducción en [Editor de modelos](../designers/model-editor.md).  
  
2.  Agregue un cubo a la escena.  En la ventana de **Cuadro de herramientas** , en **Formas**, **Cubo** seleccione y luego lo mueve a la superficie de diseño.  
  
3.  Cambie a la cara\- selección.  En la barra de herramientas del editor, elija **Seleccionar cara**.  
  
4.  Subdivida la parte superior del cubo.  En modo de selección de nombre, elija el cubo una vez para fin de la selección, y elija la parte superior del cubo para seleccionar la cara superior.  En la barra de herramientas del editor, elija **Subdivida la cara**.  Esto agrega nuevos vértices a la parte superior del cubo que división él en cuatro particiones igualmente ordenadas.  
  
     ![La parte superior del cubo se ha subdividido](~/docs/designers/media/gfx_model_demo_house_subdiv.png "gfx\_model\_demo\_house\_subdiv")  
  
5.  Si dos lados adyacentes de cubo\- para el ejemplo, el principio y los lados derechos del cubo.  En modo de selección de nombre, elija el cubo una vez para activarlo para la selección y elegir un lado del cubo.  Presione y mantenga presionada la tecla CONTROL, elija otro lado del cubo que sea adyacente al lado que seleccionó primero y, en la barra de herramientas del editor, elija **Muestra el nombre**.  
  
     ![Los lados del cubo se han extruido.](~/docs/designers/media/gfx_model_demo_house_extrude.png "gfx\_model\_demo\_house\_extrude")  
  
6.  Extiende una de las extrusiones.  Elija uno de hace nuevo que acaba de extruido y, a continuación, en la barra de herramientas del editor, elija la herramienta de **Traducir** y mueve el manipulador de traducción en la misma dirección que la extrusión.  
  
     ![Un lado del cubo se ha extruido aún más.](~/docs/designers/media/gfx_model_demo_house_extend.png "gfx\_model\_demo\_house\_extend")  
  
7.  Triangulate el modelo.  En la barra de herramientas del editor, elija **opciones avanzadas**, **Herramientas**, **Triangular**.  
  
8.  Cree el mosaico de inicio.  Cambie al modo de la perímetro\- selección eligiendo **Seleccionar borde** en la barra de herramientas del editor, y elija el cubo para activarla.  Presione y mantenga presionada la tecla CONTROL como selecciona los bordes que se muestran aquí:  
  
     ![Los bordes que formarán el pico del tejado](~/docs/designers/media/gfx_model_demo_house_edges.png "gfx\_model\_demo\_house\_edges")  
  
     Cuando los bordes seleccionados, en la barra de herramientas del editor, elija la herramienta de **Traducir** y después mueva el manipulador de traducción arriba para crear el diseño de inicio.  
  
 Se completa el modelo simplificado de inicio.  A continuación se muestra el modelo final de nuevo, con sombreado plano aplicado:  
  
 ![El modelo completado de la casa simplificada](~/docs/designers/media/gfx_model_demo_house_final.png "gfx\_model\_demo\_house\_final")  
  
 Como paso siguiente, puede aplicar un sombreador de este modelo 3D.  Para obtener más información, vea [Cómo: Aplicar un sombreador a un modelo 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## Vea también  
 [Cómo: Modelar un terreno en 3D](../designers/how-to-model-3-d-terrain.md)   
 [Editor de modelos](../designers/model-editor.md)   
 [Diseñador de sombras](../designers/shader-designer.md)