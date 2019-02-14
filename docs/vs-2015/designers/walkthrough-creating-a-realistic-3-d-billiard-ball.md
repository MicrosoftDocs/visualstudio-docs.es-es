---
title: 'Tutorial: Crear una bola de billar 3D realista | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: af8eb0f3-bf6a-4d1c-ab47-dcd88ab04efa
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e63b1d767fca3514f6f765c56362d0e395496fc4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793310"
---
# <a name="walkthrough-creating-a-realistic-3-d-billiard-ball"></a>Tutorial: Crear una bola de billar 3D realista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial se muestra cómo crear una bola de billar 3D realista mediante el Diseñador de sombras y el Editor de imágenes de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. La apariencia 3D de la bola de billar se logra combinando varias técnicas de sombreador con los recursos apropiados de textura.  
  
 Este documento muestra estas actividades:  
  
-   Crear la apariencia básica de una bola de billar mediante la forma y textura.  
  
-   Agregar profundidad mediante el modelo de iluminación de Lambert.  
  
-   Mejorar el aspecto básico mediante resaltes especulares.  
  
-   Crear sensación de espacio reflejando el entorno.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes y los conocimientos siguientes para completar este tutorial:  
  
-   Una herramienta para ensamblar texturas en un mapa de cubo, como la herramienta de texturas de DirectX que se incluye en el SDK de DirectX SDK de junio de 2010.  
  
-   Familiarizarse con el Editor de imágenes en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
-   Familiarizarse con el Diseñador de sombras en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="creating-the-basic-appearance-with-shape-and-texture"></a>Crear el aspecto básico con la forma y la textura  
 En gráficos para PC, los elementos más básicos de apariencia son la forma y el color. En una simulación en el equipo, lo habitual es usar un modelo 3D para representar la forma de un objeto del mundo real. El detalle de color se aplica a la superficie del modelo usando un mapa de textura.  
  
 Normalmente, es posible que tenga que solicitar a un artista que cree un modelo 3D que pueda usar, pero como una bola de billar es una forma común (una esfera), el Diseñador de sombras ya tiene un modelo integrado apropiado.  
  
 La esfera es la forma predeterminada de vista previa del Diseñador de sombras; si actualmente está usando otra forma para obtener la vista previa del sombreador, vuelva a la esfera.  
  
#### <a name="to-preview-the-shader-by-using-a-sphere"></a>Para obtener una vista previa del sombreador mediante una esfera  
  
- En la barra de herramientas Diseñador de sombras, seleccione **Vista previa con esfera**.  
  
  En el paso siguiente, creará un programa del sombreador que aplique una textura al modelo, pero primero debe crear una textura que pueda usar. En este tutorial se muestra cómo crear la textura usando el Editor de imágenes que forma parte de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], pero puede usar cualquier editor de imágenes que sea capaz de guardar la textura en un formato adecuado.  
  
  Asegúrese de que se muestran la ventana **Propiedades** y el **Cuadro de herramientas**.  
  
#### <a name="to-create-a-billiard-ball-texture-by-using-the-image-editor"></a>Para crear una textura de bola de billar mediante el Editor de imágenes  
  
1. Cree una textura con la que trabajar. Para obtener información sobre cómo agregar una textura al proyecto, vea la sección Introducción de [Editor de imágenes](../designers/image-editor.md).  
  
2. Establezca el tamaño de la imagen de modo que su ancho sea el doble del alto; esto es necesario debido a la manera en que una textura se asigna a la superficie esférica de la bola de billar. Para cambiar el tamaño de la imagen, en la ventana **Propiedades**, especifique nuevos valores para las propiedades **Ancho** y **Alto**. Por ejemplo, establezca el ancho en 512 y el alto en 256.  
  
3. Dibuje una textura para la bola de billar, teniendo presente cómo una textura se asigna a una esfera.  
  
    La textura debe ser similar a esta:  
  
    ![Textura de la bola de billar](../designers/media/gfx-shader-demo-billiard-art-ball-texture.png "gfx_shader_demo_billiard_art_ball_texture")  
  
4. Opcionalmente, puede que quiera reducir los requisitos de almacenamiento de esta textura. Puede hacerlo reduciendo el ancho de la textura para que coincida con el alto. Esto comprime la textura a lo largo de su ancho, pero debido a la manera en que la textura se asigna a la esfera, se expandirá cuando se represente la bola de billar. Después de cambiar el tamaño, la textura debe ser similar a esta:  
  
    ![Textura de la bola de billar comprimida en un cuadrado](../designers/media/gfx-shader-demo-billiard-art-ball-texture-square.png "gfx_shader_demo_billiard_art_ball_texture_square")  
  
   Ahora puede crear un sombreador que aplique esta textura al modelo.  
  
#### <a name="to-create-a-basic-texture-shader"></a>Para crear un sombreador de textura básico  
  
1. Cree un sombreador DGSL con el que trabajar. Para obtener información sobre cómo agregar un sombreador DGSL al proyecto, vea la sección Introducción de [Diseñador de sombras](../designers/shader-designer.md).  
  
    De manera predeterminada, un gráfico de sombreador tiene el siguiente aspecto:  
  
    ![El gráfico de sombreador predeterminado](../designers/media/gfx-shader-demo-billiard-step-0.png "gfx_shader_demo_billiard_step_0")  
  
2. Modifique el sombreador predeterminado para que se aplique el valor de un ejemplo de textura al píxel actual. El gráfico de sombreador debe tener este aspecto:  
  
    ![Un gráfico de sombreador que aplica textura a un objeto](../designers/media/gfx-shader-demo-billiard-step-1.png "gfx_shader_demo_billiard_step_1")  
  
3. Aplique la textura que ha creado en el procedimiento anterior configurando las propiedades de textura. Establezca el valor de la propiedad **Textura** del nodo **Ejemplo de textura** en **Textura1** y, después, especifique el archivo de textura usando la propiedad **Nombre de archivo** del grupo de propiedades **Textura1** en la misma ventana de propiedades.  
  
   Para obtener más información sobre cómo aplicar una textura en su sombreador, vea [Cómo: Crear un sombreador de textura básico](../designers/how-to-create-a-basic-texture-shader.md).  
  
   Ahora, la bola de billar debe tener un aspecto similar a este:  
  
   ![Un primer plano de la bola de billar con textura](../designers/media/gfx-shader-demo.png "gfx_shader_demo_")  
  
## <a name="creating-depth-with-the-lambert-lighting-model"></a>Crear profundidad con el modelo de iluminación Lambert  
 Hasta ahora, ha creado una bola de billar fácilmente reconocible. En cambio, parece plano y sin interés, más como un dibujo de una bola de billar que una réplica convincente. La apariencia plana es resultado del sombreador simplista, que se comporta como si cada píxel de la superficie de la bola de billar recibiese la misma cantidad de luz.  
  
 En el mundo real, la luz aparece más brillante en superficies que miran directamente a una fuente de luz y aparece menos brillante en superficies que están en un ángulo oblicuo respecto a la fuente de luz. Esto se debe a que la energía de los rayos de luz se distribuye por la superficie más pequeña cuando esta se orienta directamente a la fuente de luz. Mientras la superficie se aparta de la fuente de luz, la misma cantidad de energía se distribuye a través de un área de la superficie cada vez mayor. Una superficie que se aparta de una fuente de luz no recibe energía lumínica en absoluto, lo que da como resultado un aspecto completamente oscuro. Esta varianza en cuanto al brillo en la superficie de un objeto es una indicación visual importante que ayuda a definir la forma de un objeto; sin ella, el objeto aparece plano.  
  
 En los gráficos para PC, los *modelos de iluminación* (aproximaciones simplificadas de interacciones de iluminación complejas del mundo real) se usan para replicar el aspecto de iluminación real. El modelo de iluminación de Lambert varía la cantidad de luz reflejada difusamente por la superficie de un objeto según lo descrito en el párrafo anterior. Puede agregar el modelo de iluminación de Lambert al sombreador para dar a la bola de billar un aspecto 3D más convincente.  
  
#### <a name="to-add-lambert-lighting-to-your-shader"></a>Para agregar iluminación Lambert al sombreador  
  
- Modifique el sombreador para modular el valor del ejemplo de textura mediante el valor de iluminación de Lambert. El gráfico de sombreador debe tener este aspecto:  
  
   ![El gráfico del sombreador con la iluminación de la ley de Lambert agregada](../designers/media/gfx-shader-demo-billiard-step-2.png "gfx_shader_demo_billiard_step_2")  
  
- Opcionalmente, puede ajustar la manera en que se comporta la iluminación configurando la propiedad **MaterialDiffuse** del gráfico del sombreador. Para tener acceso a las propiedades del gráfico de sombreador, seleccione un área vacía de la superficie de diseño y después busque la propiedad a la que quiere obtener acceso en la ventana **Propiedades**.  
  
  Para obtener más información sobre cómo aplicar iluminación Lambert en su sombreador, vea [Cómo: Crear un sombreador Lambert básico](../designers/how-to-create-a-basic-lambert-shader.md).  
  
  Con la iluminación Lambert aplicada, la bola de billar debería ser similar a esta:  
  
  ![Un primer plano de la bola de billar iluminada y texturizada](../designers/media/gfx-shader-demo-billiard-ball-2.png "gfx_shader_demo_billiard_ball_2")  
  
## <a name="enhancing-the-basic-appearance-with-specular-highlights"></a>Mejorar el aspecto básico con resaltes especulares  
 El modelo de iluminación de Lambert proporciona la sensación de forma y dimensión ausente en el sombreador de solo textura. En cambio, la bola de billar todavía tiene un aspecto algo opaco.  
  
 Una bola de billar real suele tener un acabado brillante que refleja una parte de la luz que cae sobre ella. Parte de esta luz reflejada da lugar a los reflejos especulares, que simulan las propiedades reflectoras de una superficie. Dependiendo de las propiedades de acabado, los resaltes se pueden ubicar o ampliar, intensificar o hacer más sutiles. Estas reflexiones especulares se modelan mediante la relación entre una fuente de luz, la orientación de la superficie y la posición de la cámara, es decir, el reflejo es más intenso cuando la orientación de la superficie refleja la fuente de luz directamente a la cámara, y es menos intenso cuando la reflexión es menos directa.  
  
 El modelo de iluminación de Phong se basa en el modelo de iluminación de Lambert para incluir reflejos especulares como se describe en el párrafo anterior. Puede agregar el modelo de iluminación de Phong al sombreador para dar a la bola de billar un acabado simulado con el que conseguirá una apariencia más interesante.  
  
#### <a name="to-add-specular-highlights-to-your-shader"></a>Para agregar reflejos especulares al sombreador  
  
1. Modifique el sombreador para incluir la contribución especular mediante la combinación de adición. El gráfico de sombreador debe tener este aspecto:  
  
    ![El gráfico del sombreador con luz especular agregada](../designers/media/gfx-shader-demo-billiard-step-3.png "gfx_shader_demo_billiard_step_3")  
  
2. Opcionalmente, puede ajustar la manera en que el resaltado especular se comporta configurando las propiedades especulares (**MaterialSpecular** y **MaterialSpecularPower**) del gráfico del sombreador. Para tener acceso a las propiedades del gráfico de presentación, seleccione un área vacía de la superficie de diseño y, en la ventana de **Propiedades**, busque la propiedad a la que quiere obtener acceso.  
  
   Para obtener más información sobre cómo aplicar resaltes especulares en su sombreador, vea [Cómo: Crear un sombreador Phong básico](../designers/how-to-create-a-basic-phong-shader.md).  
  
   Con los reflejos especulares aplicados, la bola de billar debería ser similar a esta:  
  
   ![Un primer plano de la bola de billar con reflexión especular agregada](../designers/media/gfx-shader-demo-billiard-ball-3.png "gfx_shader_demo_billiard_ball_3")  
  
## <a name="creating-a-sense-of-space-by-reflecting-the-environment"></a>Crear un sentido de espacio reflejando el entorno  
 Con los reflejos especulares aplicados, la bola de billar tiene una apariencia bastante convincente. Tiene la forma correcta, el trabajo correcto de dibujo y el acabado adecuado. En cambio, existe otra técnica que hará que el aspecto de la bola de billar se integre mejor en su entorno.  
  
 Si examina una bola de billar real de cerca, puede ver que su superficie brillante no refleja simplemente resaltes especulares sino que también refleja débilmente una imagen de su entorno. Puede simular esta reflexión usando una imagen del entorno como textura y combinándola con la propia textura del modelo para determinar el color final de cada píxel. Dependiendo del tipo de acabado que quiera, puede combinar más o menos de la textura de reflexión junto con el resto del sombreador. Por ejemplo, un sombreador que simula una superficie muy brillante como un espejo podría usar solo la textura de reflexión, pero un sombreador que simula una reflexión más sutil, como la de una bola de billar, podría combinar solo una pequeña parte del valor de la textura de reflexión junto con el resto del cálculo del sombreador.  
  
 Por supuesto, no puede simplemente aplicar la imagen reflejada al modelo de la misma manera que aplica el mapa de texturas del modelo. Si lo hiciera, la reflexión universal se desplazaría con la bola de billar como si la reflexión estuviera pegada a ella. Dado que una reflexión puede proceder de cualquier dirección, necesita una manera de proporcionar un valor de asignaciones de reflexión para cualquier ángulo y una manera de mantener la asignación de la reflexión orientada según el entorno. Para satisfacer estos requisitos, puede usar una clase especial de mapa de textura, denominada *mapa de cubo*, que proporciona seis texturas organizadas para formar los lados de un cubo. Desde este cubo, puede identificar cualquier dirección para buscar un valor de textura. Si las texturas en cada lado del cubo contienen imágenes del entorno, puede simular cualquier reflexión muestreando la ubicación adecuada en la superficie del cubo. Si se mantiene el cubo alineado con el mundo, se obtendrá una reflexión precisa del entorno. Para determinar dónde se debe muestrear el cubo, simplemente calcule la reflexión del vector de la cámara según sale de la superficie del objeto, y úsela como coordenadas de textura 3D. El uso de mapas de cubo de esta manera es una técnica común que se conoce como *asignación de entorno*.  
  
 La asignación de entorno proporciona una aproximación eficaz de reflexiones reales como se describe en los párrafos anteriores. Puede mezclar reflexiones asignadas al entorno en el sombreador para dar a la bola de billar un acabado simulado que haga que la bola de billar parezca más integrada en la escena.  
  
 El primer paso es crear una textura de mapa de cubo. En muchos tipos de aplicaciones, el contenido del mapa de cubo no tiene que ser perfecto para ser efectivo, especialmente cuando la reflexión es sutil o no ocupa un espacio visible en la pantalla. Por ejemplo, muchos juegos usan mapas de cubo precalculados para la asignación de entornos y simplemente usan el más cercano a cada objeto brillante, aunque esto significa que la reflexión no es correcta. Incluso una aproximación suele ser suficiente para obtener un efecto convincente.  
  
#### <a name="to-create-textures-for-an-environment-map-by-using-the-image-editor"></a>Para crear texturas para un mapa de entorno mediante el Editor de imágenes  
  
1. Cree una textura con la que trabajar. Para obtener información sobre cómo agregar una textura al proyecto, vea la sección Introducción de [Editor de imágenes](../designers/image-editor.md).  
  
2. Establezca el tamaño de imagen de modo que el ancho sea igual al alto y sea una potencia de dos en tamaño; esto es necesario debido a la manera en que un mapa del cubo se indexa. Para cambiar el tamaño de la imagen, en la ventana **Propiedades**, especifique nuevos valores para las propiedades **Ancho** y **Alto**. Por ejemplo, establezca el valor de las propiedades **Ancho** y **Alto** en 256.  
  
3. Use un color sólido para rellenar la textura. Esta textura será la parte inferior del mapa de cubo, que corresponde a la superficie de la mesa de billar. Recuerde el color que usó cuenta para la textura siguiente. Recuerde el color que ha usado para la textura siguiente.  
  
4. Cree una segunda textura con el mismo tamaño que la primera. Esta textura se repetirá en los cuatro lados del mapa de cubo, que corresponden a la superficie y los lados de una mesa de billar, y al área de alrededor de la mesa de billar. Asegúrese de dibujar la superficie de la tabla de billar en esta textura usando el mismo color que la textura inferior. La textura debe ser similar a esta:  
  
    ![La textura de los lados del mapa del cubo](../designers/media/gfx-shader-demo-billiard-art-env-texture-side.png "gfx_shader_demo_billiard_art_env_texture_side")  
  
    Recuerde que un mapa de reflexión no tiene que ser fotorrealista para ser eficaz; por ejemplo, el mapa del cubo usado para crear las imágenes de este caso solo contiene cuatro bolsillos en lugar de seis.  
  
5. Cree una tercera textura con el mismo tamaño que las otras. Esta textura será la parte superior del mapa de cubo, que corresponde al techo de la mesa de billar. Para hacer que esta parte de la reflexión sea más interesante, puede dibujar una luz desde arriba para reforzar los reflejos especulares que ha agregado al sombreador en el procedimiento anterior. La textura debe ser similar a esta:  
  
    ![La textura de la parte superior del mapa del cubo](../designers/media/gfx-shader-demo-billiard-art-env-texture-top2.png "gfx_shader_demo_billiard_art_env_texture_top2")  
  
   Ahora que ha creado las texturas individuales de los lados del mapa de cubo, puede usar una herramienta para a ensamblarlos en un mapa de cubo que se puede almacenar en una sola textura de .dds. Puede usar cualquier programa que quiera para crear el mapa de cubo, siempre que pueda guardar el mapa de cubo en el formato de textura .dds. Este tutorial muestra cómo crear la textura usando la herramienta de texturas de DirectX que forma parte del SDK de DirectX de junio de 2010.  
  
#### <a name="to-assemble-a-cube-map-by-using-the-directx-texture-tool"></a>Para ensamblar un mapa de cubo mediante la herramienta de texturas de DirectX  
  
1. En la herramienta de texturas de DirectX, en el menú principal, seleccione **Archivo**, **Nueva textura**. Aparece el cuadro de diálogo **Nueva textura**.  
  
2. En el grupo **Tipo de textura**, seleccione **Textura del mapa de cubo**.  
  
3. En el grupo **Dimensiones**, especifique el valor correcto para **Ancho** y **Alto** y, después, seleccione **Aceptar**. Aparece un nuevo documento de texturas. De manera predeterminada, la textura mostrada en primer lugar en el documento de texturas se corresponde con la cara del cubo **Positivo X**.  
  
4. Cargue la textura que ha creado para el lado del cubo de textura sobre la cara del cubo. En el menú principal, seleccione **Archivo**, **Abrir en esta cara del mapa de cubo**, seleccione la textura que ha creado para el lado del cubo y, después, seleccione **Abrir**.  
  
5. Repita el paso 4 para las caras del cubo **Negativo X**, **Positivo Z** y **Negativo Z**. Para ello, debe ver la cara que quiere cargar. Para ver una cara diferente del mapa de cubo, en el menú principal, seleccione **Ver**, **Cara del mapa de cubo** y, después, seleccione la cara que quiere ver.  
  
6. Para la cara del cubo **Positivo Y**, cargue la textura que ha creado para la parte superior del cubo de textura.  
  
7. Para la cara del cubo **Negativo Y**, cargue la textura que ha creado para la parte inferior del cubo de textura.  
  
8. Guarde la textura.  
  
   Puede imaginarse el diseño del mapa de cubo así:  
  
   ![Diseño del entorno del mapa del cubo](../designers/media/gfx-shader-demo-billiard-art-env-texture-top.png "gfx_shader_demo_billiard_art_env_texture_top")  
  
   La imagen en la parte superior es la cara del cubo Positivo Y (+Y); en el centro, de izquierda a derecha, están las caras del cubo -X, +Z, +X y -Z; en la parte inferior está la cara del cubo -Y.  
  
   Ahora puede modificar el sombreador para combinar el ejemplo de mapa de cubo en el resto del sombreador.  
  
#### <a name="to-add-environment-mapping-to-your-shader"></a>Para agregar asignación de entorno al sombreador  
  
1. Modifique el sombreador para incluir la contribución de asignación de entorno mediante la combinación de adición. El gráfico de sombreador debe tener este aspecto:  
  
    ![Un primer plano de ambos tipos de nodos de sombreador reflectantes](../designers/media/gfx-shader-demo-billiard-step-4b.png "gfx_shader_demo_billiard_step_4b")  
  
    Observe que puede usar un nodo de **Multiplicar-sumar** para simplificar el gráfico de presentación.  
  
    A continuación se muestra una vista más detallada de los nodos del sombreador que implementan la asignación de entorno:  
  
    ![El gráfico del sombreador con la asignación de entorno agregada](../designers/media/gfx-shader-demo-billiard-step-4a.png "gfx_shader_demo_billiard_step_4a")  
  
2. Aplique la textura que ha creado en el procedimiento anterior configurando las propiedades de textura del mapa de cubo. Establezca el valor de la propiedad **Textura** del nodo **Muestra de mapa de cubo** en **Textura2** y, después, especifique el archivo de textura usando la propiedad **Nombre de archivo** del grupo de propiedades **Textura2**.  
  
3. Opcionalmente, puede ajustar la reflexión de la bola de billar configurando la propiedad **Resultado** del nodo **Constante**. Para tener acceso a las propiedades del nodo, selecciónelas y después en la ventana **Propiedades**, busque la propiedad a la que quiere obtener acceso.  
  
   Con la asignación de entorno aplicada, la bola de billar debería ser similar a esta:  
  
   ![Un primer plano de la bola de billar asignada al entorno](../designers/media/gfx-shader-demo-billiard-ball-4.png "gfx_shader_demo_billiard_ball_4")  
  
   En esta imagen final, observe que los efectos que ha agregado se unen para crear una bola de billar muy convincente. La forma, textura e iluminación crean la apariencia básica de un objeto 3D, y los reflejos y los brillos especulares hacen que la bola de billar resulte más interesante y se integre mejor en su entorno.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Exportar un sombreador](../designers/how-to-export-a-shader.md)   
 [Cómo: Aplicar a un sombreador a un modelo 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Diseñador de sombras](../designers/shader-designer.md)   
 [Editor de imágenes](../designers/image-editor.md)   
 [Nodos del Diseñador de sombras](../designers/shader-designer-nodes.md)
