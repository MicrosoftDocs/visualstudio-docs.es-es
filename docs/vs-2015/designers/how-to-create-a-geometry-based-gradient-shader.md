---
title: Procedimiento Crear un sombreador de degradado basado en geometría | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8735931e761f7d511615b5be7e93e0198a6b1a45
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60071725"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Procedimiento Crear un sombreador de gradiente basado en geometría
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este documento se muestra cómo usar el Diseñador de sombras y el lenguaje DGSL (Directed Graph Shader Language) para crear un sombreador de degradado basado en geometría. Este sombreador escala un valor de color RGB constante según el alto de cada punto de un objeto en el espacio global.  
  
 Este documento muestra estas actividades:  
  
- Agregar nodos a un gráfico de sombreador  
  
- Establecer las propiedades del nodo  
  
- Desconectar nodos  
  
- Conectar nodos  
  
## <a name="creating-a-geometry-based-gradient-shader"></a>Crear un sombreador de degradado basado en geometría  
 Puede implementar un sombreador basado en geometría mediante la incorporación de la posición del píxel en el sombreador. En los lenguajes de sombreado, un píxel contiene más información que solo el color y la ubicación en una pantalla 2D. Un píxel, conocido como un *fragmento* en algunos sistemas, es una colección de valores que describen la superficie que corresponde a un píxel. El sombreador que se describe en este documento usa el alto de cada píxel de un objeto 3D en el espacio global para afectar al color de salida final del fragmento.  
  
 Antes de empezar, asegúrese de que se muestran la ventana **Propiedades** y el **Cuadro de herramientas**.  
  
#### <a name="to-create-a-geometry-based-gradient-shader"></a>Para crear un sombreador de degradado basado en geometría  
  
1. Cree un sombreador DGSL con el que trabajar. Para obtener información sobre cómo agregar un sombreador DGSL al proyecto, vea la sección Introducción de [Diseñador de sombras](../designers/shader-designer.md).  
  
2. Desconecte el nodo **Color de punto** del nodo **Color final**. Elija el terminal **RGB** del nodo **Color de punto** y, después, elija **Romper vínculos**. Esto hace sitio para el nodo que se agrega en el paso siguiente.  
  
3. Agregue un nodo **Multiplicar** al gráfico. En el **Cuadro de herramientas**, en **Matemáticas**, seleccione **Multiplicar** y muévalo a la superficie de diseño.  
  
4. Agregue un nodo **Vector de máscara** al gráfico. En el **Cuadro de herramientas**, en **Utilidad**, seleccione **Vector de máscara** y muévalo a la superficie de diseño.  
  
5. Especifique los valores de máscara para el nodo **Vector de máscara**. En el modo **Seleccionar**, seleccione el nodo **Vector de máscara** y, después, en la ventana **Propiedades**, establezca la propiedad **Verde / Y** en **True** y las propiedades **Rojo / X**, **Azul / Z** y **Alfa / W** en **False**. En este ejemplo, las propiedades **Rojo / X**, **Verde / Y** y **Azul / Z** se corresponden a los componentes X, Y y Z del nodo **Posición global** y **Alfa / W** no se usa. Dado que solo **Verde / Y** está establecido en **True**, solo el componente Y del vector de entrada permanece después de que se enmascare.  
  
6. Agregue un nodo **Posición global** al gráfico. En el **Cuadro de herramientas**, en **Constantes**, seleccione **Posición global** y muévala a la superficie de diseño.  
  
7. Enmascare la posición de espacio global del fragmento. En el modo **Seleccionar**, mueva el terminal **Salida** del nodo **Posición global** al terminal **Vector** del nodo **Vector de máscara**. Esta conexión enmascara la posición del fragmento para ignorar los componentes X y Z.  
  
8. Multiplique la constante de color RGB por la posición del espacio de global enmascarada. Mueva el terminal **RGB** del nodo **Color de punto** al terminal **Y** del nodo **Multiplicar** y, después, mueva el terminal **Salida** del nodo **Vector de máscara** al terminal **X** del nodo **Multiplicar**. Esta conexión escala el valor de color según el alto de píxel en el espacio global.  
  
9. Conecte el valor de color escalado al color final. Mueva el terminal **Salida** del nodo **Multiplicar** al terminal **RGB** del nodo **Color final**.  
  
   La ilustración siguiente muestra el gráfico de sombreador completo y una vista previa del sombreador aplicado a una esfera.  
  
> [!NOTE]
>  En esta ilustración, se especificó un color naranja para mostrar mejor el efecto del sombreador pero como la forma de vista previa no tiene ninguna posición en el espacio global, no se puede ver una vista previa completa del sombreador en el Diseñador de sombras. El sombreador se debe previsualizar en una escena real para demostrar el efecto completo.  
  
 ![Gráfico de sombreador y vista previa de su efecto](../designers/media/digit-gradient-effect-graph.png "Digit-Gradient-Effect-Graph")  
  
 Es posible que algunas formas proporcionen mejores vistas previas para algunos sombreadores. Para más información sobre cómo obtener una vista previa de los sombreadores en el Diseñador de sombras, vea **Vista previa de sombreadores** en [Diseñador de sombras](../designers/shader-designer.md)  
  
 La siguiente ilustración muestra el sombreador que se describe en este documento aplicado a una escena 3D que se muestra en [Cómo: Modelar un terreno en 3D](../designers/how-to-model-3-d-terrain.md). La intensidad del color aumenta con el alto del punto en la posición global.  
  
 ![Efecto de degradado aplicado a un modelo de terreno 3D](../designers/media/digit-gradient-effect-result.png "Digit-Gradient-Effect-Result")  
  
 Para obtener más información acerca de cómo aplicar un sombreador a un modelo 3D, vea [Cómo: Aplicar un sombreador a un modelo 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Aplicar a un sombreador a un modelo 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Cómo: Exportar un sombreador](../designers/how-to-export-a-shader.md)   
 [Cómo: Modelo terreno en 3D](../designers/how-to-model-3-d-terrain.md)   
 [Cómo: Crear a un sombreador de textura de escala de grises](../designers/how-to-create-a-grayscale-texture-shader.md)   
 [Diseñador de sombras](../designers/shader-designer.md)   
 [Nodos del Diseñador de sombras](../designers/shader-designer-nodes.md)
