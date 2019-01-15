---
title: Organizar objetos en contenedores de diseño en el Diseñador XAML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: d5c56dc477b3c788f8d5ebfee4809067c77e08e8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829314"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Organizar objetos en contenedores de diseño en el Diseñador XAML

En este artículo se describen los paneles y controles de diseño del Diseñador XAML.

Piense en qué parte de la página quiere que aparezcan los objetos como imágenes, botones y vídeos. Tal vez desee que aparezcan en filas y columnas, en una sola línea vertical u horizontal, o en posiciones fijas.

Después de que haya considerado el aspecto que tendría la página, seleccione un panel de diseño. Todas las páginas tienen uno como punto de partida, ya que se necesita algo donde agregar los objetos. De manera predeterminada, es una **Cuadrícula**, pero puede cambiar esta configuración.

Los paneles de diseño le ayudarán a organizar los objetos en una página, pero no solo sirven para eso. Además, facilitan el diseño en diferentes tamaños y resoluciones de pantalla. Cuando los usuarios ejecutan la aplicación, todo lo que contiene el panel de diseño cambia de tamaño para coincidir con el espacio real en pantalla de sus dispositivos. Por supuesto, si no quiere que el diseño actúe de ese modo, puede invalidar este comportamiento en todo o parte del diseño. Para controlarlo, puede utilizar propiedades de alto y ancho.

## <a name="layout-panels"></a>Paneles de diseño

Para empezar su página, elija uno de estos paneles de diseño. La página puede tener más de uno. Por ejemplo, puede comenzar con un panel de diseño de **Cuadrícula** y, después, agregar un elemento **StackPanel** a un área de la **Cuadrícula**; así, podrá organizar los controles verticalmente en ese elemento.

Los siguientes paneles de diseño son los usados más habitualmente, pero hay otros. Puede encontrarlos todos en el panel **Activos**.

- [Grid](#Grid)

- [UniformGrid](#UniformGrid)

- [Canvas](#Canvas)

- [StackPanel](#stackpanel)

- [WrapPanel](#wrappanel)

- [DockPanel](#dockpanel)

### <a name="grid"></a>Cuadrícula

Organice los objetos en filas y columnas.

![Panel de diseño de cuadrícula](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png)

### <a name="uniformgrid"></a>UniformGrid

Organice los objetos en regiones de cuadrícula iguales o uniformes. Este panel es excelente para organizar una lista de imágenes.

![Panel de diseño UniformGrid](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png)

(Disponible solo para proyectos de WPF).

### <a name="canvas"></a>Canvas

Organice los objetos como desee. Cuando los usuarios ejecuten la aplicación, estos elementos tendrán una posición fija en la pantalla.

![Panel de diseño de lienzo](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png)

### <a name="stackpanel"></a>StackPanel

Organice los objetos en una sola línea horizontal o verticalmente.

![Panel de diseño StackPanel](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png)

### <a name="wrappanel"></a>WrapPanel

Organice los objetos en secuencia de izquierda a derecha. Cuando el panel se queda sin espacio en el borde de la derecha, *ajusta* el contenido a la línea siguiente, y así sucesivamente de izquierda a derecha y de arriba abajo. También puede hacer que la orientación de un panel de ajuste (WrapPanel) sea vertical para que los objetos fluyan de arriba abajo y de izquierda a derecha.

(Disponible solo para proyectos de WPF).

![Panel de diseño WrapPanel](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png)

### <a name="dockpanel"></a>DockPanel

Organice los objetos para que permanezcan, o se *acoplen*, en uno de los bordes del panel.

(Disponible solo para proyectos de WPF).

![Panel de diseño DockPanel](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png)

**Vea un vídeo corto:** ![Botón de reproducción](../designers/media/bldadminconsoleinitialconfigicon.PNG) [WPF - DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)

## <a name="layout-controls"></a>Controles de diseño

También puede agregar los objetos a controles de diseño. No tienen tantas características como un panel de diseño, pero pueden resultar útiles en determinados escenarios.

Los siguientes controles de diseño son los más populares, pero hay otros. Puede encontrarlos todos en el panel **Activos**.

- [Border](#Border)

- [Popup](#Popup)

- [ScrollViewer](#scrollviewer)

- [Viewbox](#viewbox)

### <a name="border"></a>Borde

Cree un borde, un fondo o ambos alrededor de un objeto. Solo puede agregar un objeto a un elemento **Border**. Si quiere aplicar un borde o un fondo a más de un objeto, agregue un panel de diseño al elemento **Border**. A continuación, agregue objetos a ese panel o control.

![Control de diseño de borde](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png)

### <a name="popup"></a>Popup

Muestre información u opciones a los usuarios en una ventana. Solo puede agregar un objeto a un elemento **Popup**. De manera predeterminada, un elemento **Popup** contiene una **Cuadrícula**, pero se puede cambiar esta configuración.

### <a name="scrollviewer"></a>ScrollViewer

Permita que los usuarios se desplacen hacia abajo en una página o parte de una página. Puede agregar un solo objeto a un control **ScrollViewer** así que resulta muy adecuado agregar un panel de diseño como una **Cuadrícula** o **StackPanel**.

![Control de diseño ScrollViewer](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png)

### <a name="viewbox"></a>Viewbox

Escale objetos igual que haría con un control de zoom. Solo puede agregar un objeto a un elemento **Viewbox**. Si quiere aplicar ese efecto a más de un objeto, agregue un panel de diseño al control **ViewBox** y, después, agregue los controles a dicho panel de diseño.

(Disponible solo para proyectos de WPF).

![Control de diseño ViewBox](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png)

## <a name="see-also"></a>Vea también

- [Trabajo con elementos en el Diseñador XAML](../designers/working-with-elements-in-xaml-designer.md)
- [Creación de una IU con el Diseñador XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)