---
title: 'Cómo: Crear un sombreador Phong básico'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c7c69da8-142b-4d3b-9be9-4be0d5970b25
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cc27aa96b0e893ada745533d070b3b7aa29264e2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937816"
---
# <a name="how-to-create-a-basic-phong-shader"></a>Cómo: Crear un sombreador Phong básico

En este artículo se muestra cómo usar el Diseñador de sombras y el lenguaje DGSL (Directed Graph Shader Language) para crear un sombreador de iluminación que implementa el modelo de iluminación Phong clásico.

## <a name="the-phong-lighting-model"></a>El modelo de iluminación Phong

El modelo de iluminación Phong extiende el modelo de iluminación de Lambert para incluir reflejos especulares, que simulan las propiedades brillantes de una superficie. El componente especular proporciona iluminación adicional de las mismas fuentes de iluminación direccionales que se usan en el modelo de iluminación de Lambert, pero su contribución al color final se procesa de manera diferente. El resaltado especular afecta a cada superficie en la escena de manera diferente, en función de la relación entre la dirección de la vista, la dirección de las fuentes de luz y la orientación de la superficie. Es un producto del color especular, la potencia especular y la orientación de la superficie, y del color, la intensidad y la dirección de las fuentes de luz. Las superficies que reflejan la fuente de luz directamente en el visor reciben la contribución especular máxima y las superficies que reflejan la fuente de luz lejos del visor no reciben ninguna contribución. En el modelo de iluminación Phong, uno o más componentes especulares se combinan para determinar el color y la intensidad del resaltado especular para cada punto en el objeto y, después, se agregan al resultado del modelo de iluminación Lambert para producir el color final del píxel.

Para obtener más información sobre el modelo de iluminación Lambert, vea [Cómo: Crear un sombreador Lambert básico](../designers/how-to-create-a-basic-lambert-shader.md).

Antes de empezar, asegúrese de que se muestran la ventana **Propiedades** y el **Cuadro de herramientas**.

1. Cree un sombreador Lambert, como se describe en [Cómo: Crear un sombreador Lambert básico](../designers/how-to-create-a-basic-lambert-shader.md).

2. Desconecte el nodo **Lambert** del nodo **Color final**. Elija el terminal **RGB** del nodo **Lambert** y, después, elija **Romper vínculos**. Esto hace sitio para el nodo que se agrega en el paso siguiente.

3. Agregue un nodo **Agregar** al gráfico. En el **Cuadro de herramientas**, en **Matemáticas**, seleccione **Agregar** y muévalo a la superficie de diseño.

4. Agregue un nodo **Especular** al gráfico. En el **Cuadro de herramientas**, en **Utilidad**, seleccione **Especular** y muévalo a la superficie de diseño.

5. Agregue la contribución especular. Mueva el terminal **Salida** del nodo **Especular** al terminal **X** del nodo **Agregar** y, después, mueva el terminal **Salida** del nodo **Lambert** al terminal **Y** del nodo **Agregar**. Estas conexiones combinan las contribuciones de color difuso y especular totales para el píxel.

6. Conecte el valor de color calculado al color final. Mueva el terminal **Salida** del nodo **Agregar** al terminal **RGB** del nodo **Color final**.

   La ilustración siguiente muestra el gráfico de sombreador completo y una vista previa del sombreador aplicado a un modelo de tetera.

> [!NOTE]
> Para demostrar mejor el efecto del sombreador en esta ilustración, se especificó un color naranja mediante el parámetro **MaterialDiffuse** del sombreador y un acabado de aspecto metálico mediante los parámetros **MaterialSpecular** y **MaterialSpecularPower**. Para obtener información sobre los parámetros de materiales, vea la sección Vista previa de sombreadores en [Diseñador de sombras](../designers/shader-designer.md).

 ![Gráfico de sombreador y vista previa de su efecto](../designers/media/digit-lighting-graph.png)

 Es posible que algunas formas proporcionen mejores vistas previas para algunos sombreadores. Para más información sobre cómo obtener una vista previa de los sombreadores en el Diseñador de sombras, vea la sección Vista previa de sombreadores en [Diseñador de sombras](../designers/shader-designer.md)

 La siguiente ilustración muestra el sombreador descrito en este documento aplicado a un modelo 3D. La propiedad **MaterialSpecular** se establece en (1,00, 0,50, 0,20, 0,00) y su propiedad **MaterialSpecularPower** se establece en 16.

> [!NOTE]
> La propiedad **MaterialSpecular** determina el acabado aparente del material de la superficie. Una superficie muy brillante como el cristal o el plástico suele tener un color especular que es un tono brillante de blanco. Una superficie metálica suele tener un color especular próximo al color difuso. Una superficie con acabado satinado suele tener un color especular que es un tono oscuro de gris.
>
> La propiedad **MaterialSpecularPower** determina la intensidad de los reflejos especulares. Las potencias especulares altas simulan reflejos más opacos y localizados. Las potencias especulares muy bajas simulan reflejos intensos y circulares que pueden saturar en exceso y ocultar el color de toda la superficie.

 ![Iluminación Phong aplicada a un modelo](../designers/media/digit-lighting-model.png)

 Para obtener más información sobre cómo aplicar un sombreador a un modelo 3D, vea [Cómo: Aplicar un sombreador a un modelo 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Vea también

- [Cómo: aplicar un sombreador a un modelo en 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Cómo: exportar un sombreador](../designers/how-to-export-a-shader.md)
- [Cómo: crear un sombreador Lambert básico](../designers/how-to-create-a-basic-lambert-shader.md)
- [Diseñador de sombras](../designers/shader-designer.md)
- [Nodos del Diseñador de sombras](../designers/shader-designer-nodes.md)