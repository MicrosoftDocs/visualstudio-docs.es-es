---
title: Organizar objetos en contenedores de diseño en el Diseñador XAML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3ca6fc205585d832f4dadc5f4ce4709a71c7b6fe
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059206"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Organizar objetos en contenedores de diseño en el Diseñador XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Piense en qué parte de la página desea que aparezcan los objetos como imágenes, botones y vídeos. Tal vez desee que aparezcan en filas y columnas, en una sola línea vertical u horizontal, o en posiciones fijas.  
  
 Después de que haya considerado el aspecto que tendría la página, seleccione un panel de diseño. Todas las páginas tienen uno como punto de partida, ya que se necesita algo donde agregar los objetos. De manera predeterminada, es una **Cuadrícula**, pero se puede cambiar.  
  
 Los paneles de diseño le ayudarán a organizar los objetos en una página, pero no solo sirven para eso. Además, facilitan el diseño en diferentes tamaños y resoluciones de pantalla. Cuando los usuarios ejecutan la aplicación, todo lo que contiene el panel de diseño cambia de tamaño para coincidir con el espacio real en pantalla de sus dispositivos. Por supuesto, si no desea que el diseño actúe de ese modo, puede invalidar este comportamiento en todo o parte del diseño. Para controlarlo, puede utilizar propiedades de alto y ancho.  
  
 En esta página se describen los controles y los paneles de diseño y, además, se incluyen vínculos a vídeos cortos que le ayudarán a empezar a trabajar con ellos.  
  
> [!NOTE]
>  Algunos de los vídeos pueden hacer referencia a Blend o Expression Blend, que utilizan el mismo Diseñador XAML que Visual Studio y Blend para Visual Studio.  
  
## <a name="layout-panels"></a>Paneles de diseño  
 Para empezar su página, elija uno de estos paneles de diseño. La página puede tener más de uno. Por ejemplo, puede comenzar con un panel de diseño de **Cuadrícula** y, después, agregar un elemento **StackPanel** a un área de la **Cuadrícula**; así, podrá organizar los controles verticalmente en ese elemento.  
  
 Los siguientes paneles de diseño son los usados más habitualmente, pero hay otros. Puede encontrarlos todos en el panel **Activos**.  
  
- [Grid](#Grid)  
  
- [UniformGrid](#Uniform)  
  
- [Canvas](#Canvas)  
  
- [StackPanel](#Stack)  
  
- [WrapPanel](#Wrap)  
  
- [DockPanel](#Dock)  
  
### <a name="Grid"></a> Cuadrícula  
 Organice los objetos en filas y columnas.  
  
 ![](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png "98b234b2-ac3b-441f-9136-98375fee87b7")  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [con cuadrículas](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids)  
  
### <a name="Uniform"></a> UniformGrid  
 Organice los objetos en regiones de cuadrícula iguales o uniformes. Este panel es excelente para organizar una lista de imágenes.  
  
 ![](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png "928b9284-a7e8-4678-875a-656b80b78076")  
  
 (Disponible solo para proyectos de WPF)  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Working with a UniformGrid](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid)  
  
### <a name="Canvas"></a> Canvas  
 Organice los objetos como desee. Cuando los usuarios ejecuten la aplicación, estos elementos tendrán una posición fija en la pantalla.  
  
 ![](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png "e1ae27f0-3a57-454e-b580-877dcea8836d")  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [trabajar con el lienzo](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas)  
  
### <a name="Stack"></a> StackPanel  
 Organice los objetos en una sola línea horizontal o verticalmente.  
  
 ![](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png "a85a7b57-b0a8-495e-b985-f0291e41d093")  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Working with StackPanel and WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
### <a name="Wrap"></a> WrapPanel  
 Organice los objetos en secuencia de izquierda a derecha. Cuando el panel se queda sin espacio en el borde de la derecha, *ajusta* el contenido a la línea siguiente, y así sucesivamente de izquierda a derecha y de arriba abajo. También puede hacer que la orientación de un panel de ajuste (WrapPanel) sea vertical para que los objetos fluyan de arriba abajo y de izquierda a derecha.  
  
 (Disponible solo para proyectos de WPF)  
  
 ![](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png "b1c415fb-9a32-4a18-aa0b-308fca994ac9")  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Working with StackPanel and WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
### <a name="Dock"></a> DockPanel  
 Organice los objetos para que permanezcan, o se *acoplen*, en uno de los bordes del panel.  
  
 (Disponible solo para proyectos de WPF)  
  
 ![](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png "72d46b58-9a49-4dd5-8af7-6843c0440226")  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [WPF - DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)  
  
## <a name="layout-controls"></a>Controles de diseño  
 También puede agregar los objetos a controles de diseño. No tienen tantas características como un panel de diseño, pero pueden resultar útiles en determinados escenarios.  
  
 Los siguientes controles de diseño son los usados más habitualmente, pero hay otros. Puede encontrarlos todos en el panel **Activos**.  
  
- [Border](#Border)  
  
- [Popup](#Popup)  
  
- [ScrollViewer](#Scroll)  
  
- [UniformGrid](#Uniform)  
  
- [Viewbox](#View)  
  
### <a name="Border"></a> Border  
 Cree un borde, un fondo o ambos alrededor de un objeto. Solo puede agregar un objeto a un elemento **Border**. Si quiere aplicar un borde o un fondo a más de un objeto, agregue un panel de diseño al elemento **Border**. A continuación, agregue objetos a ese panel o control.  
  
 ![](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png "e761238b-99fd-43c5-bbc4-57538b8289ff")  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Working with Borders](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders)  
  
### <a name="Popup"></a> Popup  
 Muestre información u opciones a los usuarios en una ventana. Solo puede agregar un objeto a un elemento **Popup**. De manera predeterminada, un elemento **Popup** contiene una **Cuadrícula**, pero se puede cambiar esta configuración.  
  
### <a name="Scroll"></a> ScrollViewer  
 Permita que los usuarios se desplacen hacia abajo en una página o parte de una página. Puede agregar un solo objeto a un control **ScrollViewer** así que resulta muy adecuado agregar un panel de diseño como una **Cuadrícula** o **StackPanel**.  
  
 ![](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png "06b326d4-f23d-41a6-b26b-e1aff37572a7")  
  
### <a name="View"></a> Viewbox  
 Escale objetos igual que haría con un control de zoom. Solo puede agregar un objeto a un elemento **Viewbox**. Si quiere aplicar ese efecto a más de un objeto, agregue un panel de diseño al control **ViewBox** y, después, agregue los controles a dicho panel de diseño.  
  
 (Disponible solo para proyectos de WPF)  
  
 ![](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png "f5b13c66-d918-4141-8a16-bd8f8628687a")  
  
## <a name="see-also"></a>Vea también  
 [Working with elements in XAML Designer](../designers/working-with-elements-in-xaml-designer.md)   
 [Crear una UI usando el Diseñador XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
