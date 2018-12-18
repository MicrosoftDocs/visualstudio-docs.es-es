---
title: 'Cómo: Crear un sombreador de gradiente basado en geometría'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cfdf75c058d1786febda71b05d424b1032254754
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2018
ms.locfileid: "37923912"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Cómo: Crear un sombreador de gradiente basado en geometría

En este artículo se muestra cómo usar el Diseñador de sombras y el lenguaje DGSL (Directed Graph Shader Language) para crear un sombreador de degradado basado en geometría. Este sombreador escala un valor de color RGB constante según el alto de cada punto de un objeto en el espacio global.

## <a name="create-a-geometry-based-gradient-shader"></a>Crear un sombreador de degradado basado en geometría

Puede implementar un sombreador basado en geometría mediante la incorporación de la posición del píxel en el sombreador. En los lenguajes de sombreado, un píxel contiene más información que solo el color y la ubicación en una pantalla 2D. Un píxel, conocido como un *fragmento* en algunos sistemas, es una colección de valores que describen la superficie que corresponde a un píxel. El sombreador que se describe en este documento usa el alto de cada píxel de un objeto 3D en el espacio global para afectar al color de salida final del fragmento.

Antes de empezar, asegúrese de que se muestran la ventana **Propiedades** y el **Cuadro de herramientas**.

1.  Cree un sombreador DGSL con el que trabajar. Para obtener información sobre cómo agregar un sombreador DGSL al proyecto, vea la sección Introducción de [Diseñador de sombras](../designers/shader-designer.md).

2.  Desconecte el nodo **Color de punto** del nodo **Color final**. Elija el terminal **RGB** del nodo **Color de punto** y, después, elija **Romper vínculos**. Esto hace sitio para el nodo que se agrega en el paso siguiente.

3.  Agregue un nodo **Multiplicar** al gráfico. En el **Cuadro de herramientas**, en **Matemáticas**, seleccione **Multiplicar** y muévalo a la superficie de diseño.

4.  Agregue un nodo **Vector de máscara** al gráfico. En el **Cuadro de herramientas**, en **Utilidad**, seleccione **Vector de máscara** y muévalo a la superficie de diseño.

5.  Especifique los valores de máscara para el nodo **Vector de máscara**. En el modo **Seleccionar**, seleccione el nodo **Vector de máscara** y, después, en la ventana **Propiedades**, establezca la propiedad **Verde / Y** en **True** y las propiedades **Rojo / X**, **Azul / Z** y **Alfa / W** en **False**. En este ejemplo, las propiedades **Rojo / X**, **Verde / Y** y **Azul / Z** se corresponden a los componentes X, Y y Z del nodo **Posición global** y **Alfa / W** no se usa. Dado que solo **Verde / Y** está establecido en **True**, solo el componente Y del vector de entrada permanece después de que se enmascare.

6.  Agregue un nodo **Posición global** al gráfico. En el **Cuadro de herramientas**, en **Constantes**, seleccione **Posición global** y muévala a la superficie de diseño.

7.  Enmascare la posición de espacio global del fragmento. En el modo **Seleccionar**, mueva el terminal **Salida** del nodo **Posición global** al terminal **Vector** del nodo **Vector de máscara**. Esta conexión enmascara la posición del fragmento para ignorar los componentes X y Z.

8.  Multiplique la constante de color RGB por la posición del espacio de global enmascarada. Mueva el terminal **RGB** del nodo **Color de punto** al terminal **Y** del nodo **Multiplicar** y, después, mueva el terminal **Salida** del nodo **Vector de máscara** al terminal **X** del nodo **Multiplicar**. Esta conexión escala el valor de color según el alto de píxel en el espacio global.

9. Conecte el valor de color escalado al color final. Mueva el terminal **Salida** del nodo **Multiplicar** al terminal **RGB** del nodo **Color final**.

La ilustración siguiente muestra el gráfico de sombreador completo y una vista previa del sombreador aplicado a una esfera.

> [!NOTE]
> En esta ilustración, se especificó un color naranja para mostrar mejor el efecto del sombreador pero como la forma de vista previa no tiene ninguna posición en el espacio global, no se puede ver una vista previa completa del sombreador en el Diseñador de sombras. El sombreador se debe previsualizar en una escena real para demostrar el efecto completo.

 ![Gráfico de sombreador y vista previa de su efecto](../designers/media/digit-gradient-effect-graph.png)

 Es posible que algunas formas proporcionen mejores vistas previas para algunos sombreadores. Para más información sobre cómo obtener una vista previa de los sombreadores en el Diseñador de sombras, vea **Vista previa de sombreadores** en [Diseñador de sombras](../designers/shader-designer.md)

 En la siguiente ilustración se muestra el sombreador descrito en este documento aplicado a una escena 3D que se demuestra en [Cómo: Modelar un terreno en 3D](../designers/how-to-model-3-d-terrain.md). La intensidad del color aumenta con el alto del punto en la posición global.

 ![Efecto de degradado aplicado a un modelo de terreno 3D](../designers/media/digit-gradient-effect-result.png)

 Para obtener más información sobre cómo aplicar un sombreador a un modelo 3D, vea [Cómo: Aplicar un sombreador a un modelo 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Vea también

- [Cómo: aplicar un sombreador a un modelo en 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Cómo: exportar un sombreador](../designers/how-to-export-a-shader.md)
- [Cómo: modelar un terreno en 3D](../designers/how-to-model-3-d-terrain.md)
- [Cómo: crear un sombreador de textura de escala de grises](../designers/how-to-create-a-grayscale-texture-shader.md)
- [Diseñador de sombras](../designers/shader-designer.md)
- [Nodos del Diseñador de sombras](../designers/shader-designer-nodes.md)