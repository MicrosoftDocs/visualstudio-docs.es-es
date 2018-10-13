---
title: 'Cómo: Crear una textura básica | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 143bf4f094a603c20e12b52adb452b193fb57a33
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292804"
---
# <a name="how-to-create-a-basic-texture"></a>Cómo: Crear una textura básica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este documento se muestra cómo usar el Editor de imágenes para crear una textura básica.  
  
 Este documento muestra estas actividades:  
  
-   Establecer el tamaño de la textura  
  
-   Establecer el color de primer plano y el color de fondo  
  
-   Usar el canal alfa (transparencia)  
  
-   Usar las herramientas **Rellenar** y **Elipse**  
  
-   Establecer propiedades de herramientas  
  
## <a name="creating-a-basic-texture"></a>Crear una textura básica  
 Puede usar el Editor de imágenes para crear y modificar imágenes y texturas para su juego o aplicación.  
  
 Los siguientes pasos muestran cómo crear una textura que representa un destino de "diana". Cuando termine, la textura debe ser similar a la siguiente imagen. Para mostrar mejor la transparencia de la textura, se configuró el Editor de imágenes para usar un modelo de color verde de cuadros para mostrarla.  
  
 ![Destino de "diana" con transparencia mostrado en verde](../designers/media/digit-bullseye-texture-in-editor.png "Digit-Bullseye-Texture-In-Editor")  
  
 Antes de empezar, asegúrese de que se muestra la ventana **Propiedades**. Se usa la ventana **Propiedades** para establecer el tamaño de la imagen, cambiar las propiedades de las herramientas y especificar colores mientras trabaja.  
  
#### <a name="to-create-a-bullseye-target-texture"></a>Para crear una textura de destino de "diana"  
  
1.  Cree una textura con la que trabajar. Para obtener información sobre cómo agregar una textura al proyecto, vea la sección Introducción de [Editor de imágenes](../designers/image-editor.md).  
  
2.  Establezca el tamaño de imagen en 512 x 512 píxeles. En la ventana **Propiedades**, establezca los valores de las propiedades **Ancho** y **Alto** en `512`.  
  
3.  En la barra de herramientas del Editor de imágenes, elija la herramienta **Relleno**. La ventana **Propiedades** muestra ahora las propiedades de la herramienta **Relleno** junto con las propiedades de la imagen.  
  
4.  Establezca el color de primer plano en negro totalmente transparente. En la ventana **Propiedades**, en el grupo de propiedades **Colores**, seleccione **Primer plano**. Establezca los valores de las propiedades **R**, **G**, **B** y **A** junto al selector de colores en `0`.  
  
5.  En la barra de herramientas del Editor de imágenes, seleccione la herramienta **Relleno** y, después, mantenga presionada la tecla Mayús y elija cualquier punto de la imagen. Al usar la tecla Mayús, el valor alfa del color de relleno reemplaza el color de la imagen. De lo contrario, se usa el valor alfa para mezclar el color de relleno junto con el color de la imagen.  
  
    > [!IMPORTANT]
    >  Este paso, junto con la selección de color en el paso anterior, garantiza que la imagen base está preparada para la textura de destino de "diana" que se va a dibujar. Cuando la imagen se rellena con negro transparente, y dado que el borde del destino es negro, no habrá ningún artefacto de suavizado alrededor del destino.  
  
6.  En la barra de herramientas del Editor de imágenes, elija la herramienta **Elipse**.  
  
7.  Establezca el color de primer plano en negro totalmente opaco. Establezca los valores de las propiedades **R**, **G** y **B** en `0` y el valor de la propiedad **A** en `255`.  
  
8.  Establezca el color de fondo en blanco totalmente opaco. En la ventana **Propiedades**, en el grupo de propiedades **Colores**, seleccione **Fondo**. Establezca los valores de las propiedades **R**, **G**, **B** y **A** en `255`.  
  
9. Establezca el ancho del contorno de la elipse. En la ventana **Propiedades**, en el grupo de propiedades **Apariencia**, establezca el valor de la propiedad **Ancho** en `8`.  
  
10. Asegúrese de que esté habilitado el suavizado de contorno. En la ventana **Propiedades**, en el grupo de propiedades **Apariencia**, asegúrese de que esté habilitada la propiedad **Suavizado de contorno**.  
  
11. Con la herramienta **Elipse**, dibuje un círculo desde la coordenada de píxel `(3, 3)` a la coordenada de píxel `(508, 508)`. Para dibujar el círculo más fácilmente, puede presionar y mantener presionada la tecla Mayús mientras dibuja.  
  
    > [!NOTE]
    >  Las coordenadas de píxel de la ubicación actual del puntero se muestran en la barra de estado de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
12. Cambie el color de fondo. Establezca **R** en `44`, **G** en `165`, **B** en `211` y **A** en `255`.  
  
13. Dibuje otro círculo desde la coordenada de píxel `(64, 64)` a la coordenada de píxel `(448, 448)`.  
  
14. Cambie el color de fondo a blanco totalmente opaco. Establezca **R**, **G**, **B** y **A** en `255`.  
  
15. Dibuje otro círculo desde la coordenada de píxel `(128, 128)` a la coordenada de píxel `(384, 384)`.  
  
16. Cambie el color de fondo. Establezca **R** en `255`, **G** y **B** en `64` y **A** en `255`.  
  
17. Dibuje otro círculo desde la coordenada de píxel `(192, 192)` a la coordenada de píxel `(320, 320)`.  
  
 La textura de destino de "diana" está completa. Aquí está la imagen final, mostrada con transparencia.  
  
 ![La textura de destino de "diana" completa](../designers/media/gfx-image-demo-bullseye.png "gfx_image_demo_bullseye")  
  
 Como paso siguiente, puede generar niveles de MIP para esta textura. Para obtener información, vea [Cómo: Crear y modificar niveles de MIP](../designers/how-to-create-and-modify-mip-levels.md).  
  
## <a name="see-also"></a>Vea también  
 [Image Editor](../designers/image-editor.md)



