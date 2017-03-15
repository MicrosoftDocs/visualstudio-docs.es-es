---
title: "C&#243;mo: Crear una textura b&#225;sica | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
caps.latest.revision: 15
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 15
---
# C&#243;mo: Crear una textura b&#225;sica
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este documento se muestra cómo usar el Editor de imágenes para crear una textura básica.  
  
 En este documento se muestran estas actividades:  
  
-   Establecer el tamaño de textura  
  
-   Establecer los colores de primer plano y de fondo  
  
-   Utilizando el canal alfa \(transparencia\)  
  
-   Mediante las herramientas de **Relleno** y de **Elipse**  
  
-   Establecer las propiedades de la herramienta  
  
## Crear una textura básica  
 Puede utilizar el editor de imágenes para crear y modificar imágenes y después texturas para el juego o la aplicación.  
  
 Los pasos siguientes muestran cómo crear una textura que representa un destino de “diana”. Cuando termine, textura debe parecerse a la siguiente imagen.  Para mostrar mejor la transparencia de textura, se ha configurado el editor de Imágenes utilizar un verde, modelo de cuadros para mostrarlo.  
  
 ![Destino de "Bullseye" con transparencia mostrado en verde](../designers/media/digit-bullseye-texture-in-editor.png "Digit\-Bullseye\-Texture\-In\-Editor")  
  
 Antes de empezar, asegúrese de que la ventana de **Propiedades** está visible.  Utilice la ventana de **Propiedades** para establecer el tamaño de la imagen, cambia las propiedades de la herramienta, y especificar colores mientras trabaja.  
  
#### Para crear una textura de destino de “diana”  
  
1.  Cree una textura con la que trabajar.  Para obtener información sobre cómo agregar una textura al proyecto, vea la sección Introducción de [Editor de imágenes](../designers/image-editor.md).  
  
2.  Establezca el tamaño de la imagen en píxeles 512x512.  En la ventana de **Propiedades** , establezca los valores de las propiedades de **Ancho** y de **Altura** a `512`.  
  
3.  En la barra de herramientas del editor de imágenes, elija la herramienta de **Relleno** .  La ventana de **Propiedades** ahora muestra las propiedades de la herramienta de **Relleno** así como las propiedades de la imagen.  
  
4.  Establezca el color de primer plano de blanco lleno\- transparente.  En la ventana de **Propiedades** , en el grupo de propiedades de **Colores** , seleccione **Primer plano**.  Establezca los valores de **R**, de **G**, de **B**, y las propiedades de **T** junto al selector de colores en `0`.  
  
5.  En la barra de herramientas del editor de imágenes, elija la herramienta de **Relleno** , y después presione y mantenga presionada la tecla MAYÚS y elija cualquier punto de la imagen.  Usando la tecla MAYÚS hace el valor alfa del color de relleno para reemplazar el color de la imagen; si no, el valor alfa se utiliza para combinar el color de relleno así como color de la imagen.  
  
    > [!IMPORTANT]
    >  Este paso, así como la selección de color en el paso anterior, garantiza que la imagen base está preparada para la textura de destino de “diana” que se va a dibujar.  Cuando la imagen se rellena con transparente negro\- y porque es el borde de destino negro \(que no se ningún artefacto de alias alrededor del destino.  
  
6.  En la barra de herramientas del editor de imágenes, elija la herramienta de **Elipse** .  
  
7.  Establezca el color de primer plano de blanco lleno\- opaco.  Establezca los valores de **R**, de **G**, y las propiedades de **B** para `0` y el valor de la propiedad de **T** a `255`.  
  
8.  Establezca el color de fondo en blanco lleno\- opaco.  En la ventana de **Propiedades** , en el grupo de propiedades de **Colores** , seleccione **En segundo plano**.  Establezca los valores de **R**, de **G**, de **B**, y las propiedades de **T** a `255`.  
  
9. Establezca el ancho del contorno de la elipse.  En la ventana de **Propiedades** , en el grupo de propiedades de **Apariencia** , establezca el valor de la propiedad de **Ancho** a `8`.  
  
10. Asegúrese de que el suavizado de contorno esté habilitado.  En la ventana de **Propiedades** , en el grupo de propiedades de **Apariencia** , asegúrese de que la propiedad de **Suavizado** está establecida.  
  
11. Mediante la herramienta de **Elipse** , extraiga un círculo de coordenada de píxeles `(3, 3)` a la coordenada de píxeles `(508, 508)`.  Para dibujar un círculo más fácilmente, presione y mantener presionada la tecla MAYÚS mientras dibuja.  
  
    > [!NOTE]
    >  Las coordenadas de píxel de la ubicación actual del puntero se muestran en la barra de estado de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
12. Cambie el color de fondo.  Establezca **R** a `44`, **G** a `165`, **B** `211`y, **T** a `255`.  
  
13. Extraiga otro círculo de coordenada de píxeles `(64, 64)` a la coordenada de píxeles `(448, 448)`.  
  
14. Cambie el color de fondo de nuevo en blanco lleno\- opaco.  Establezca **R**, **G**, **B**, y **T** a `255`.  
  
15. Extraiga otro círculo de coordenada de píxeles `(128, 128)` a la coordenada de píxeles `(384, 384)`.  
  
16. Cambie el color de fondo.  Establezca **R** a `255`, **G** y **B** `64`y, **T** a `255`.  
  
17. Extraiga otro círculo de coordenada de píxeles `(192, 192)` a la coordenada de píxeles `(320, 320)`.  
  
 Se completa la textura de destino de “diana”.  A continuación se muestra la imagen final, que se muestra con la transparencia.  
  
 ![La textura de destino "bullseye" completa](../designers/media/gfx_image_demo_bullseye.png "gfx\_image\_demo\_bullseye")  
  
 Como paso siguiente, puede generar los niveles MIP para esta textura.  Para obtener más información, vea [Cómo: Crear y modificar niveles de MIP](../designers/how-to-create-and-modify-mip-levels.md).  
  
## Vea también  
 [Editor de imágenes](../designers/image-editor.md)