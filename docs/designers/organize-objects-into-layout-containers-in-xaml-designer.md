---
title: "Organizar objetos en contenedores de dise&#241;o en el Dise&#241;ador XAML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Organizar objetos en contenedores de dise&#241;o en el Dise&#241;ador XAML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Piense en qué parte de la página desea que aparezcan los objetos como imágenes, botones y vídeos.  Tal vez desee que aparezcan en filas y columnas, en una sola línea vertical u horizontal, o en posiciones fijas.  
  
 Después de que haya considerado el aspecto que tendría la página, seleccione un panel de diseño.  Todas las páginas tienen uno como punto de partida, ya que se necesita algo donde agregar los objetos.  De forma predeterminada, es una **Cuadrícula**, pero puede cambiar esta configuración.  
  
 Los paneles de diseño le ayudarán a organizar los objetos en una página, pero no solo sirven para eso.  Además, facilitan el diseño en diferentes tamaños y resoluciones de pantalla.  Cuando los usuarios ejecutan la aplicación, todo lo que contiene el panel de diseño cambia de tamaño para coincidir con el espacio real en pantalla de sus dispositivos.  Por supuesto, si no desea que el diseño actúe de ese modo, puede invalidar este comportamiento en todo o parte del diseño.  Para controlarlo, puede utilizar propiedades de alto y ancho.  
  
 En esta página se describen los controles y los paneles de diseño y, además, se incluyen vínculos a vídeos cortos que le ayudarán a empezar a trabajar con ellos.  
  
> [!NOTE]
>  Algunos de los vídeos pueden hacer referencia a Blend o Expression Blend, que utilizan el mismo Diseñador XAML que Visual Studio y Blend para Visual Studio.  
  
## Paneles de diseño  
 Para empezar su página, elija uno de estos paneles de diseño.  La página puede tener más de uno.  Por ejemplo, puede comenzar con un panel de diseño de **Cuadrícula** y, a continuación, agregar un elemento **StackPanel** a un área de la **Cuadrícula**; así, podrá organizar los controles verticalmente en ese elemento.  
  
 Los siguientes paneles de diseño son los usados más habitualmente, pero hay otros.  Puede encontrarlos todos en el panel **Activos**.  
  
-   [Cuadrícula](#Grid)  
  
-   [UniformGrid](#Uniform)  
  
-   [Canvas](#Canvas)  
  
-   [StackPanel](#Stack)  
  
-   [WrapPanel](#Wrap)  
  
-   [DockPanel](#Dock)  
  
###  <a name="Grid"></a> Cuadrícula  
 Organice los objetos en filas y columnas.  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Using Grids](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids)  
  
###  <a name="Uniform"></a> UniformGrid  
 Organice los objetos en regiones de cuadrícula iguales o uniformes.  Este panel es excelente para organizar una lista de imágenes.  
  
 \(Disponible solo para proyectos de WPF\)  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Working with a UniformGrid](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid)  
  
###  <a name="Canvas"></a> Canvas  
 Organice los objetos como desee.  Cuando los usuarios ejecuten la aplicación, estos elementos tendrán una posición fija en la pantalla.  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Working with the canvas](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas)  
  
###  <a name="Stack"></a> StackPanel  
 Organice los objetos en una sola línea horizontal o verticalmente.  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Working with StackPanel and WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Wrap"></a> WrapPanel  
 Organice los objetos en secuencia de izquierda a derecha.  Cuando el panel se queda sin espacio en el borde de la derecha, *ajusta* el contenido a la línea siguiente, y así sucesivamente de izquierda a derecha y de arriba abajo.  También puede hacer que la orientación de un panel de ajuste \(WrapPanel\) sea vertical para que los objetos fluyan de arriba abajo y de izquierda a derecha.  
  
 \(Disponible solo para proyectos de WPF\)  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Working with StackPanel and WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Dock"></a> DockPanel  
 Organice los objetos para que permanezcan, o se *acoplen*, en uno de los bordes del panel.  
  
 \(Disponible solo para proyectos de WPF\)  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [WPF \- DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)  
  
## Controles de diseño  
 También puede agregar los objetos a controles de diseño.  No tienen tantas características como un panel de diseño, pero pueden resultar útiles en determinados escenarios.  
  
 Los siguientes controles de diseño son los usados más habitualmente, pero hay otros.  Puede encontrarlos todos en el panel **Activos**.  
  
-   [Borde](#Border)  
  
-   [Popup](#Popup)  
  
-   [ScrollViewer](#Scroll)  
  
-   [UniformGrid](#Uniform)  
  
-   [Viewbox](#View)  
  
###  <a name="Border"></a> Borde  
 Cree un borde, un fondo o ambos alrededor de un objeto.  Solo puede agregar un objeto a un **Borde**.  Si desea aplicar un borde o un fondo a más de un objeto, agregue un panel de diseño al **Borde**.  A continuación, agregue objetos a ese panel o control.  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Working with Borders](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders)  
  
###  <a name="Popup"></a> Popup  
 Muestre información u opciones a los usuarios en una ventana.  Solo puede agregar un objeto a un **Popup**.  De forma predeterminada, un **Popup** contiene una **Cuadrícula**, pero se puede cambiar esta configuración.  
  
###  <a name="Scroll"></a> ScrollViewer  
 Permita que los usuarios se desplacen hacia abajo en una página o parte de una página.  Puede agregar un solo objeto a un control **ScrollViewer** así que resulta muy adecuado agregar un panel de diseño como una **Cuadrícula** o **StackPanel**.  
  
###  <a name="View"></a> Viewbox  
 Escale objetos igual que haría con un control de zoom.  Solo puede agregar un objeto a un **Viewbox**.  Si desea aplicar ese efecto a más de un objeto, agregue un panel de diseño al control **ViewBox** y después agregue los controles a dicho panel de diseño.  
  
 \(Disponible solo para proyectos de WPF\)  
  
## Vea también  
 [Trabajar con elementos en el Diseñador XAML](../designers/working-with-elements-in-xaml-designer.md)   
 [Tutorial: Crear una UI usando el Diseñador XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)