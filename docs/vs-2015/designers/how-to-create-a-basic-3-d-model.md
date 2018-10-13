---
title: 'Cómo: Crear un modelo 3D básico | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e61c86e553672ac619f71a27f8a651b417700c8f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224788"
---
# <a name="how-to-create-a-basic-3-d-model"></a>Cómo: Crear un modelo 3D básico
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este documento se muestra cómo usar el Editor de modelos para crear un modelo 3D básico.  
  
 Este documento muestra estas actividades:  
  
-   Agregar objetos a una escena  
  
-   Selección de caras y bordes  
  
-   Traducir selecciones  
  
-   Uso de las herramientas **Subdividir cara** y **Extruir cara**  
  
-   Uso del comando **Triangular**  
  
## <a name="creating-a-basic-3-d-model"></a>Creación de un modelo 3D básico  
 Puede usar el Editor de modelos para crear y modificar modelos 3D y escenas para su juego o aplicación. Los pasos siguientes muestran cómo usar el Editor de modelos para crear un modelo 3D simplificado de una casa. Un modelo simplificado puede usarse como sustituto de activos de arte finales que se siguen creando, como una malla para la detección de colisiones o como un modelo de nivel bajo de detalle que se usará cuando el objeto que representa se encuentra demasiado lejos para beneficiarse de una representación más detallada.  
  
 Cuando termine, el modelo debe tener este aspecto:  
  
 ![El modelo completado de la casa simplificada](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")  
  
 Antes de empezar, asegúrese de que se muestran la ventana **Propiedades** y el **Cuadro de herramientas**.  
  
#### <a name="to-create-a-simplified-3-d-model-of-a-house"></a>Para crear un modelo 3D simplificado de una casa  
  
1.  Cree un modelo 3D con el que trabajar. Para obtener información sobre cómo agregar un modelo al proyecto, vea la sección Introducción de [Editor de modelos](../designers/model-editor.md).  
  
2.  Agregue un cubo a la escena. En la ventana **Herramientas**, en **Formas**, seleccione **Cubo** y después muévalo a la superficie de diseño.  
  
3.  Cambie a selección de cara. En la barra de herramientas del Editor de modelos, elija **Seleccionar cara**.  
  
4.  Subdivida la parte superior del cubo. En el modo de selección de cara, elija el cubo una vez para activarlo para la selección y, después, elija la parte superior del cubo para seleccionar la cara superior. En la barra de herramientas del Editor de modelos, haga clic en **Subdividir cara**. Esto agrega vértices nuevos a la parte superior del cubo que lo dividen en cuatro particiones de igual tamaño.  
  
     ![La parte superior del cubo se ha subdividido](../designers/media/gfx-model-demo-house-subdiv.png "gfx_model_demo_house_subdiv")  
  
5.  Extruya dos lados adyacentes del cubo, por ejemplo, la parte frontal y derecha del cubo. En el modo de selección de cara, elija el cubo una vez para activarlo para la selección y, después, elija un lado del cubo. Presione y mantenga presionada la tecla Control, elija otro lado del cubo que sea adyacente al primero que seleccionó y, después, en la barra de herramientas del Editor de modelos, haga clic en **Extruir cara**.  
  
     ![Los lados del cubo se han extruido.](../designers/media/gfx-model-demo-house-extrude.png "gfx_model_demo_house_extrude")  
  
6.  Extienda una de las extrusiones. Seleccione una de las caras que acaba de extruir y, después, en la barra de herramientas del Editor de modelos, elija la herramienta **Trasladar** y mueva el manipulador de traslación en la misma dirección que la extrusión.  
  
     ![Un lado del cubo se ha extruido aún más.](../designers/media/gfx-model-demo-house-extend.png "gfx_model_demo_house_extend")  
  
7.  Triangule el modelo. En la barra de herramientas del Editor de modelos, elija **Avanzadas**, **Herramientas**, **Triangular**.  
  
8.  Cree el techo de la casa. Cambie al modo de selección de borde eligiendo **Seleccionar borde** en la barra de herramientas del Editor de modelos y, después, seleccione el cubo para activarlo. Mantenga presionada la tecla Control mientras selecciona los bordes que se muestran aquí:  
  
     ![Los bordes que formarán el pico del tejado](../designers/media/gfx-model-demo-house-edges.png "gfx_model_demo_house_edges")  
  
     Con los bordes seleccionados, en la barra de herramientas del Editor de modelos elija la herramienta **Trasladar** y, después, mueva el manipulador de traslación hacia arriba para crear el techo de la casa.  
  
 El modelo de la casa simplificada está completado. Este es el modelo final de nuevo, con sombreado plano aplicado:  
  
 ![El modelo completado de la casa simplificada](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")  
  
 Como paso siguiente, puede aplicar un sombreador a este modelo 3D. Para más información, vea [Cómo: aplicar un sombreador a un modelo 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Modelar un terreno en 3D](../designers/how-to-model-3-d-terrain.md)   
 [Editor de modelos](../designers/model-editor.md)   
 [Diseñador de sombras](../designers/shader-designer.md)



