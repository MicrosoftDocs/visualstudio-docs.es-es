---
title: "Trabajar con elementos en el Dise&#241;ador XAML | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Trabajar con elementos en el Dise&#241;ador XAML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede agregar elementos \(controles, diseños y formas\) a la aplicación en XAML, en el código o mediante el Diseñador XAML.  En este tema se describe cómo trabajar con elementos en el Diseñador XAML en Visual Studio o Blend para Visual Studio.  
  
## Agregar un elemento a un diseño  
 El *diseño* es el proceso de ajustar el tamaño de los elementos y colocarlos en una interfaz de usuario.  Para colocar elementos visuales, debe ponerlos en un [Panel](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.panel.aspx) de diseño.  Un `Panel` tiene una propiedad secundaria que es una colección de tipos [FrameworkElement](http://msdn.microsoft.com/library/windows/apps/br208706.aspx).  Puede usar varios elementos secundarios `Panel`, como [Canvas](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.canvas.aspx), [StackPanel](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.aspx) y [Grid](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) para emplearlos como contenedores de diseño y para colocar y organizar los elementos en una página.  
  
 De forma predeterminada, un panel `Grid` sirve como contenedor de diseño de nivel superior dentro de una página o formulario.  Puede agregar paneles de diseño, controles u otros elementos en el diseño de página de nivel superior.  
  
#### Para agregar un elemento a un diseño  
  
-   En el Diseñador XAML, realice una de las siguientes acciones:  
  
    -   Haga doble clic en un elemento en el **Cuadro de herramientas** \(o seleccione un elemento en el Cuadro de herramientas y presione ENTRAR\).  
  
    -   Arrastre un elemento del **Cuadro de herramientas** a la mesa de trabajo.  
  
    -   En el **Cuadro de herramientas**, seleccione una de las herramientas de dibujo \(por ejemplo, [Elipse](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.ellipse.aspx) o [Rectángulo](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.aspx)\) y, a continuación, dibuje un elemento en el panel activo.  
  
## Cambiar el orden de distribución en capas de los elementos  
 Cuando hay dos elementos en la mesa de trabajo del Diseñador XAML, un elemento aparecerá delante del otro según el orden de distribución en capas.  En la parte inferior de la lista de elementos de la ventana Esquema del documento se encuentra el elemento que se sitúa en primer plano \(excepto cuando se establece la propiedad **ZIndex** de un elemento\).  Cuando se inserta un elemento en una página, un formulario o un contenedor de diseño, el elemento se coloca automáticamente delante de los demás elementos en el elemento de contenedor activo.  Para cambiar el orden de los elementos, puede usar los comandos **Order** o arrastrar los elementos del árbol de objetos de la ventana Esquema del documento.  
  
#### Para cambiar el orden de distribución en capas  
  
-   Realice una de las siguientes acciones:  
  
    -   En la ventana **Esquema del documento**, arrastre los elementos hacia arriba o hacia abajo para crear el orden de distribución en capas deseado.  
  
    -   En la ventana Esquema del documento o en la mesa de trabajo, haga clic con el botón derecho en el elemento cuyo orden de distribución en capas desea cambiar, elija **Orden** y, a continuación, haga clic en una de las siguientes opciones:  
  
        -   **Traer al frente** para traer el elemento al primer plano del orden.  
  
        -   **Traer adelante** para traer el elemento un nivel hacia adelante en el orden.  
  
        -   **Enviar atrás** para enviar el elemento un nivel hacia atrás en el orden.  
  
        -   **Enviar al fondo** para enviar el elemento a la parte trasera del orden.  
  
     Cambie la propiedad **ZIndex** en la sección **Diseño** en la ventana Propiedades.  En el caso de los elementos superpuestos, la propiedad **ZIndex** tiene prioridad sobre el orden de los elementos que se muestra en la ventana Esquema del documento.  Un elemento con un valor **ZIndex** inferior aparece delante cuando los elementos se superponen.  
  
## Cambiar la alineación de un elemento  
 Puede alinear los elementos en la mesa de trabajo usando comandos de menú o arrastrando los elementos a las guías de alineación.  
  
 Una *guía de alineación* es una indicación visual que le ayuda a alinear un elemento con respecto a otros elementos de la aplicación.  
  
#### Para alinear dos o más elementos usando comandos de menú  
  
1.  Seleccione los elementos que desee alinear.  Puede seleccionar varios elementos manteniendo presionada la tecla Ctrl mientras los selecciona.  
  
2.  Seleccione una de las siguientes propiedades en **HorizontalAlignment** en la sección **Diseño** de la ventana Propiedades: **Izquierda**, **Centro**, **Derecha** o **Ajustar**.  
  
3.  Seleccione una de las siguientes propiedades en **VerticalAlignment** en la sección **Diseño** de la ventana Propiedades: **Superior**, **Centro**, **Inferior** o **Ajustar**.  
  
#### Para alinear dos o más elementos usando guías de alineación  
  
-   En el Diseñador XAML, en un diseño que contenga al menos dos elementos, arrastre o cambie el tamaño de uno de los elementos de modo que el borde se alinee con otro elemento.  
  
     Cuando los bordes estén alineados, aparecerá un *límite de alineación* para indicar la alineación.  El límite de alineación es una línea roja discontinua.  Los límites de alineación aparecen solamente cuando está habilitado el **ajuste a las guías de alineación**.  Para ver una ilustración de la mesa de trabajo que muestra los límites de alineación, consulte [Tutorial: Crear una UI usando el Diseñador XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
## Cambiar los márgenes de un elemento  
 Los márgenes del Diseñador XAML determinan cuánto espacio vacío hay alrededor de un elemento en la mesa de trabajo.  Por ejemplo, los márgenes especifican la cantidad de espacio entre los bordes exteriores de un elemento y los límites de un panel `Grid` que contiene el elemento.  Los márgenes también especifican la cantidad de espacio entre los elementos que están contenidos en un `StackPanel`.  
  
#### Para cambiar los márgenes de un elemento en la ventana Propiedades  
  
1.  Seleccione el elemento cuyos márgenes desea cambiar.  
  
2.  En **Diseño**, en la ventana Propiedades, cambie el valor \(en píxeles o unidades independientes del dispositivo, que tienen un tamaño aproximado de 1\/96 pulgada\) de cualquiera de las propiedades **Margen** \(**Superior**, **Izquierdo**, **Derecho** o **Inferior**\).  
  
#### Para cambiar los márgenes de un elemento en la mesa de trabajo  
  
-   Para cambiar los márgenes de un elemento con respecto a su contenedor de diseño, haga clic en los controles *Adorner de margen* que aparecen alrededor del elemento en la mesa de trabajo cuando dicho elemento esté seleccionado y se encuentre dentro de un contenedor de diseño.  Para ver una ilustración que muestra los controles Adorner de margen, consulte [Tutorial: Crear una UI usando el Diseñador XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
     Si el control Adorner de margen está abierto, ya sea vertical u horizontalmente, el margen no está establecido.  Si el control Adorner de margen está cerrado, ese margen está establecido.  
  
     Cuando se abre el control Adorner de margen y el margen opuesto no está establecido, el margen opuesto se establece en el valor correcto de acuerdo con la ubicación del elemento en la mesa de trabajo.  En el caso de los márgenes opuestos, como los márgenes **Izquierdo** y **Derecho**, siempre se establece al menos una propiedad.  
  
    > [!IMPORTANT]
    >  Los elementos incluidos dentro de algunos contenedores de diseño, como <xref:Windows.UI.Xaml.Controls.Canvas>, no tienen controles Adorner de margen.  Los elementos incluidos dentro de un <xref:Windows.UI.Xaml.Controls.StackPanel> tienen controles Adorner de margen para los márgenes izquierdo y derecho o para los márgenes superior e inferior, según la orientación del `StackPanel`.  
  
## Agrupar y desagrupar elementos  
 La acción de agrupar dos o más elementos en el Diseñador XAML crea un nuevo contenedor de diseño y coloca los elementos dentro de ese contenedor.  La colocación de dos o más elementos juntos en un contenedor de diseño permite seleccionar, mover y transformar fácilmente el grupo como si sus elementos fuesen un único elemento.  La agrupación permite además identificar elementos que están relacionados entre sí de alguna manera, como los botones que constituyen un elemento de navegación.  Cuando se desagrupan los elementos, simplemente se elimina el contenedor de diseño que los contiene.  
  
#### Para agrupar elementos en un nuevo contenedor de diseño  
  
1.  Seleccione los elementos que desee agrupar.  \(Para seleccionar varios elementos, mantenga presionada la tecla Ctrl mientras hace clic en ellos\).  
  
2.  Haga clic con el botón derecho en los elementos seleccionados, seleccione **Agrupar en** y, a continuación, haga clic en el tipo de contenedor de diseño en el que desea que se encuentre el grupo.  
  
    > [!TIP]
    >  Si selecciona <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> o <xref:Windows.UI.Xaml.Controls.ScrollViewer> para agrupar los elementos, estos se colocan en un nuevo panel <xref:Windows.UI.Xaml.Controls.Grid> dentro de <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> o <xref:Windows.UI.Xaml.Controls.ScrollViewer>.  Si desagrupa los elementos de uno de estos contenedores de diseño, solo se elimina <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> o <xref:Windows.UI.Xaml.Controls.ScrollViewer>, y se conserva el panel <xref:Windows.UI.Xaml.Controls.Grid>.  Para eliminar el panel `Grid`, desagrupe los elementos de nuevo.  
  
#### Para desagrupar elementos y eliminar el diseño  
  
-   Haga clic con el botón derecho en el grupo que desea desagrupar y haga clic en **Desagrupar**.  
  
 También puede agrupar o desagrupar elementos haciendo clic con el botón derecho en los elementos seleccionados en la ventana Esquema del documento y haciendo clic en **Agrupar en** o **Desagrupar**.  
  
## Restablecer el diseño de un elemento  
 Puede restaurar los valores predeterminados de las propiedades de diseño específicas de un elemento mediante el comando Restablecer diseño.  Con este comando, puede restablecer el margen, la alineación, el ancho, el alto y el tamaño de un elemento, ya sea de forma individual o colectiva.  
  
#### Para restablecer el diseño de un elemento  
  
-   En la ventana Esquema del documento o en la mesa de trabajo, haga clic con el botón derecho en el elemento, elija **Diseño**, **Restablecer** *PropertyName*, donde *PropertyName* es la propiedad que desea restablecer \(o elija **Diseño**, **Restablecer todo** para restablecer todas las propiedades de diseño del elemento\).  
  
## Vea también  
 [Tutorial: Crear una UI usando el Diseñador XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)