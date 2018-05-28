---
title: Trabajar con elementos en el Diseñador XAML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 676c8767691610349cc2eee4c09970318feda9f5
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="working-with-elements-in-xaml-designer"></a>Trabajar con elementos en el Diseñador XAML
Puede agregar elementos (controles, diseños y formas) a la aplicación en XAML, en el código o mediante el Diseñador XAML. En este tema se describe cómo trabajar con elementos en el Diseñador XAML en Visual Studio o Blend para Visual Studio.

## <a name="adding-an-element-to-a-layout"></a>Agregar un elemento a un diseño
 El *diseño* es el proceso de ajustar el tamaño de los elementos y colocarlos en una interfaz de usuario. Para colocar elementos visuales, debe colocarlos en un [Panel](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.panel.aspx) de diseño. `Panel` tiene una propiedad secundaria, que es una colección de tipos [FrameworkElement](http://msdn.microsoft.com/library/windows/apps/br208706.aspx). Se pueden usar distintos elementos secundarios de `Panel`, como [Canvas](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.canvas.aspx), [StackPanel](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.aspx) y [Grid](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx), para que actúen como contenedores de diseño y para colocar y organizar los elementos en una página.

 De forma predeterminada, un panel `Grid` sirve como contenedor de diseño de nivel superior dentro de una página o formulario. Puede agregar paneles de diseño, controles u otros elementos en el diseño de página de nivel superior.

#### <a name="to-add-an-element-to-a-layout"></a>Para agregar un elemento a un diseño

-   En el Diseñador XAML, realice una de las siguientes acciones:

    -   Haga doble clic en un elemento en el **Cuadro de herramientas** (o seleccione un elemento en el Cuadro de herramientas y presione Entrar).

    -   Arrastre un elemento del **Cuadro de herramientas** a la mesa de trabajo.

    -   En el **Cuadro de herramientas**, seleccione una de las herramientas de dibujo (como [Elipse](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.ellipse.aspx) o [Rectángulo](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.aspx)) y después dibuje un elemento en el panel activo.

## <a name="changing-the-layering-order-of-elements"></a>Cambiar el orden de distribución en capas de los elementos
 Cuando hay dos elementos en la mesa de trabajo del Diseñador XAML, un elemento aparecerá delante del otro según el orden de distribución en capas. En la parte inferior de la lista de elementos de la ventana Esquema del documento se encuentra el elemento que se sitúa en primer plano (excepto cuando se establece la propiedad **ZIndex** de un elemento). Cuando se inserta un elemento en una página, un formulario o un contenedor de diseño, el elemento se coloca automáticamente delante de los demás elementos en el elemento de contenedor activo. Para cambiar el orden de los elementos, puede usar los comandos de **Ordenar** o arrastrar los elementos en el árbol de objetos de la ventana Esquema del documento.

#### <a name="to-change-the-layering-order"></a>Para cambiar el orden de distribución en capas

-   Realice una de las siguientes acciones:

    -   En la ventana **Esquema del documento**, arrastre los elementos hacia arriba o hacia abajo para crear el orden de distribución en capas deseado.

    -   En la ventana Esquema del documento o en la mesa de trabajo, haga clic con el botón derecho en el elemento cuyo orden de distribución en capas quiere cambiar, elija **Orden** y, después, haga clic en una de las opciones siguientes:

        -   **Traer al frente** para traer el elemento al primer plano del orden.

        -   **Traer adelante** para traer el elemento un nivel hacia adelante en el orden.

        -   **Enviar atrás** para enviar el elemento un nivel hacia atrás en el orden.

        -   **Enviar al fondo** para enviar el elemento a la última posición del orden.

     Cambie la propiedad **ZIndex** en la sección **Diseño** en la ventana Propiedades. En el caso de los elementos superpuestos, la propiedad **ZIndex** tiene prioridad sobre el orden de los elementos que se muestran en la ventana Esquema del documento. Cuando los elementos se superponen, aparece un elemento con un valor **ZIndex** más alto delante.

## <a name="changing-the-alignment-of-an-element"></a>Cambiar la alineación de un elemento
 Puede alinear los elementos en la mesa de trabajo usando comandos de menú o arrastrando los elementos a las guías de alineación.

 Una *guía de alineación* es una indicación visual que ayuda a alinear un elemento con respecto a otros elementos de la aplicación.

#### <a name="to-align-two-or-more-elements-by-using-menu-commands"></a>Para alinear dos o más elementos usando comandos de menú

1.  Seleccione los elementos que desee alinear. Puede seleccionar varios elementos manteniendo presionada la tecla Ctrl mientras los selecciona.

2.  Seleccione una de las propiedades siguientes en **HorizontalAlignment** en la sección **Diseño** de la ventana Propiedades: **Izquierda**, **Centro**, **Derecha** o **Ajustar**.

3.  Seleccione una de las propiedades siguientes en **VerticalAlignment** en la sección **Diseño** de la ventana Propiedades: **Superior**, **Centro**, **Inferior** o **Ajustar**.

#### <a name="to-align-two-or-more-elements-by-using-snaplines"></a>Para alinear dos o más elementos usando guías de alineación

-   En el Diseñador XAML, en un diseño que contenga al menos dos elementos, arrastre o cambie el tamaño de uno de los elementos de modo que el borde se alinee con otro elemento.

     Cuando los bordes estén alineados, aparecerá un *límite de alineación* para indicar la alineación. El límite de alineación es una línea roja discontinua. Los límites de alineación aparecen solamente cuando está habilitado el **ajuste a las guías de alineación** . Para ver una ilustración de la mesa de trabajo que muestra los límites de alineación, vea [Crear una IU con el Diseñador XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="changing-an-elements-margins"></a>Cambiar los márgenes de un elemento
 Los márgenes del Diseñador XAML determinan cuánto espacio vacío hay alrededor de un elemento en la mesa de trabajo. Por ejemplo, los márgenes especifican la cantidad de espacio entre los bordes exteriores de un elemento y los límites de un panel `Grid` que contiene el elemento. Los márgenes también especifican la cantidad de espacio entre los elementos que están contenidos en un `StackPanel`.

#### <a name="to-change-an-elements-margins-in-the-properties-window"></a>Para cambiar los márgenes de un elemento en la ventana Propiedades

1.  Seleccione el elemento cuyos márgenes desea cambiar.

2.  En **Diseño**, en la ventana Propiedades, cambie el valor (en píxeles o unidades independientes del dispositivo, que tienen un tamaño aproximado de 1/96 de pulgada) de cualquiera de las propiedades de **Margen** (**Superior**, **Izquierdo**, **Derecho** o **Inferior**).

#### <a name="to-change-an-elements-margins-in-the-artboard"></a>Para cambiar los márgenes de un elemento en la mesa de trabajo

-   Para cambiar los márgenes de un elemento con respecto a su contenedor de diseño, haga clic en los *adornos de margen* que aparecen alrededor del elemento en la mesa de trabajo cuando el elemento está seleccionado y se encuentra dentro de un contenedor de diseño. Para obtener una ilustración que muestra los adornos de margen, vea [Crear una IU con el Diseñador XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

     Si el control Adorner de margen está abierto, ya sea vertical u horizontalmente, el margen no está establecido. Si el control Adorner de margen está cerrado, ese margen está establecido.

     Cuando se abre un adorno del margen y el margen opuesto no se establece, este último quedará establecido según el valor correcto de acuerdo con la ubicación del elemento en la mesa de trabajo. Para los márgenes opuestos, como **Izquierdo** y **Derecho**, siempre se establece al menos una propiedad.

    > [!IMPORTANT]
    >  Los elementos incluidos dentro de algunos contenedores de diseño, como <xref:Windows.UI.Xaml.Controls.Canvas>, no tienen controles Adorner de margen. Los elementos incluidos dentro de un <xref:Windows.UI.Xaml.Controls.StackPanel> tienen controles Adorner de margen para los márgenes izquierdo y derecho o para los márgenes superior e inferior, según la orientación del `StackPanel`.

## <a name="grouping-and-ungrouping-elements"></a>Agrupar y desagrupar elementos
 La acción de agrupar dos o más elementos en el Diseñador XAML crea un nuevo contenedor de diseño y coloca los elementos dentro de ese contenedor. La colocación de dos o más elementos juntos en un contenedor de diseño permite seleccionar, mover y transformar fácilmente el grupo como si sus elementos fuesen un único elemento. La agrupación permite además identificar elementos que están relacionados entre sí de alguna manera, como los botones que constituyen un elemento de navegación. Cuando se desagrupan los elementos, simplemente se elimina el contenedor de diseño que los contiene.

#### <a name="to-group-elements-into-a-new-layout-container"></a>Para agrupar elementos en un nuevo contenedor de diseño

1.  Seleccione los elementos que desee agrupar. (Para seleccionar varios elementos, mantenga presionada la tecla Ctrl mientras hace clic en ellos).

2.  Haga clic con el botón derecho en los elementos seleccionados, seleccione **Agrupar en** y, después, haga clic en el tipo de contenedor de diseño en el que quiera incluir el grupo.

    > [!TIP]
    >  Si selecciona <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> o <xref:Windows.UI.Xaml.Controls.ScrollViewer> para agrupar los elementos, estos se colocan en un nuevo panel <xref:Windows.UI.Xaml.Controls.Grid> dentro de <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> o <xref:Windows.UI.Xaml.Controls.ScrollViewer>. Si desagrupa los elementos de uno de estos contenedores de diseño, solo se elimina <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> o <xref:Windows.UI.Xaml.Controls.ScrollViewer>, y se conserva el panel <xref:Windows.UI.Xaml.Controls.Grid>. Para eliminar el panel `Grid`, desagrupe los elementos de nuevo.

#### <a name="to-ungroup-elements-and-delete-the-layout"></a>Para desagrupar elementos y eliminar el diseño

-   Haga clic con el botón derecho en el grupo que quiere desagrupar y haga clic en **Desagrupar**.

 También puede agrupar o desagrupar elementos haciendo clic con el botón derecho en los elementos seleccionados en la ventana Esquema del documento y haciendo clic en **Agrupar en** o **Desagrupar**.

## <a name="resetting-the-element-layout"></a>Restablecer el diseño de un elemento
 Puede restaurar los valores predeterminados de las propiedades de diseño específicas de un elemento mediante el comando Restablecer diseño. Con este comando, puede restablecer el margen, la alineación, el ancho, el alto y el tamaño de un elemento, ya sea de forma individual o colectiva.

#### <a name="to-reset-the-element-layout"></a>Para restablecer el diseño de un elemento

-   En la ventana Esquema del documento o en la mesa de trabajo, haga clic con el botón derecho en el elemento, elija **Diseño**, **Restablecer**  *NombreDeLaPropiedad*, donde *NombreDeLaPropiedad* es la propiedad que quiere restablecer (o seleccione **Diseño**, **Restablecer todo** para restablecer todas las propiedades de diseño del elemento).

## <a name="see-also"></a>Vea también

- [Crear una UI usando el Diseñador XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
