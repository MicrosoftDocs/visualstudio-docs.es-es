---
title: 'Cómo: Crear una textura básica'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b356d8596581b1c289d9b9aa13a3d5b362e39e58
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769101"
---
# <a name="how-to-create-a-basic-texture"></a>Cómo: Crear una textura básica

En este artículo se muestra cómo usar el Editor de imágenes para crear una textura básica, incluidas estas actividades:

- Establecer el tamaño de la textura

- Establecer el color de primer plano y el color de fondo

- Usar el canal alfa (transparencia)

- Usar las herramientas **Rellenar** y **Elipse**

- Establecer propiedades de herramientas

## <a name="create-a-basic-texture"></a>Crear una textura básica

Puede usar el Editor de imágenes para crear y modificar imágenes y texturas para su juego o aplicación.

En los pasos siguientes se muestra cómo crear una textura que represente un destino de "diana". Cuando haya terminado, la textura debe tener una apariencia similar a la de la imagen siguiente. Para mostrar mejor la transparencia de la textura, se configuró el Editor de imágenes para usar un modelo de color verde de cuadros para mostrarla.

![Destino de "Bullseye" con transparencia mostrado en verde](../designers/media/digit-bullseye-texture-in-editor.png)

Antes de empezar, asegúrese de que se muestra la ventana **Propiedades**. Se usa la ventana **Propiedades** para establecer el tamaño de la imagen, cambiar las propiedades de las herramientas y especificar colores mientras trabaja.

### <a name="create-a-bullseye-target-texture"></a>Crear una textura de destino de "diana"

1. Cree una textura con la que va a trabajar. Para información sobre cómo agregar una textura al proyecto, consulte [Editor de imágenes](../designers/image-editor.md#get-started).

2. Establezca el tamaño de imagen en 512 x 512 píxeles. En la ventana **Propiedades**, establezca los valores de las propiedades **Ancho** y **Alto** en `512`.

3. En la barra de herramientas del Editor de imágenes, elija la herramienta **Relleno**. La ventana **Propiedades** muestra ahora las propiedades de la herramienta **Relleno** junto con las propiedades de la imagen.

4. Establezca el color de primer plano en negro totalmente transparente. En la ventana **Propiedades**, en el grupo de propiedades **Colores**, seleccione **Primer plano**. Establezca los valores de las propiedades **R**, **G**, **B** y **A** junto al selector de colores en `0`.

5. En la barra de herramientas del Editor de imágenes, seleccione la herramienta **Relleno** y, después, mantenga presionada la tecla **Mayús** y elija cualquier punto de la imagen. Al usar la tecla **Mayús**, el valor alfa del color de relleno reemplaza el color de la imagen. De lo contrario, se usa el valor alfa para mezclar el color de relleno junto con el color de la imagen.

    > [!IMPORTANT]
    > Este paso, junto con la selección de color en el paso anterior, garantiza que la imagen base está preparada para la textura de destino de "diana" que se va a dibujar. Cuando la imagen se rellena con negro transparente, y dado que el borde del destino es negro, no habrá ningún artefacto de suavizado alrededor del destino.

6. En la barra de herramientas del Editor de imágenes, elija la herramienta **Elipse**.

7. Establezca el color de primer plano en negro totalmente opaco. Establezca los valores de las propiedades **R**, **G** y **B** en `0` y el valor de la propiedad **A** en `255`.

8. Establezca el color de fondo en blanco totalmente opaco. En la ventana **Propiedades**, en el grupo de propiedades **Colores**, seleccione **Fondo**. Establezca los valores de las propiedades **R**, **G**, **B** y **A** en `255`.

9. Establezca el ancho del contorno de la elipse. En la ventana **Propiedades**, en el grupo de propiedades **Apariencia**, establezca el valor de la propiedad **Ancho** en `8`.

10. Asegúrese de que esté habilitado el suavizado de contorno. En la ventana **Propiedades**, en el grupo de propiedades **Apariencia**, asegúrese de que esté habilitada la propiedad **Suavizado de contorno**.

11. Con la herramienta **Elipse**, dibuje un círculo desde la coordenada de píxel `(3, 3)` a la coordenada de píxel `(508, 508)`. Para dibujar el círculo más fácilmente, puede presionar y mantener presionada la tecla **Mayús** mientras dibuja.

    > [!NOTE]
    > Las coordenadas de píxel de la ubicación actual del puntero se muestran en la barra de estado de Visual Studio.

12. Cambie el color de fondo. Establezca **R** en `44`, **G** en `165`, **B** en `211` y **A** en `255`.

13. Dibuje otro círculo desde la coordenada de píxel `(64, 64)` a la coordenada de píxel `(448, 448)`.

14. Cambie el color de fondo a blanco totalmente opaco. Establezca **R**, **G**, **B** y **A** en `255`.

15. Dibuje otro círculo desde la coordenada de píxel `(128, 128)` a la coordenada de píxel `(384, 384)`.

16. Cambie el color de fondo. Establezca **R** en `255`, **G** y **B** en `64` y **A** en `255`.

17. Dibuje otro círculo desde la coordenada de píxel `(192, 192)` a la coordenada de píxel `(320, 320)`.

La textura de destino de "diana" está completa. Aquí está la imagen final, mostrada con transparencia.

![La textura de destino "bullseye" completa](../designers/media/gfx_image_demo_bullseye.png)

Como paso siguiente, puede generar niveles de MIP para esta textura. Para obtener información, vea [Cómo: Crear y modificar niveles de MIP](../designers/how-to-create-and-modify-mip-levels.md).

## <a name="see-also"></a>Vea también

- [Editor de imágenes](../designers/image-editor.md)
