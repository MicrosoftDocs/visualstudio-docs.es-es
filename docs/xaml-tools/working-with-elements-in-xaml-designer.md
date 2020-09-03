---
title: Trabajar con elementos en el Diseñador XAML
ms.date: 05/14/2018
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 3f544501a7d8a792af9ddd89c682324a21002c4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "82921098"
---
# <a name="work-with-elements-in-xaml-designer"></a>Trabajar con elementos en el Diseñador XAML

Para agregar elementos (controles, distribuciones y formas) a una aplicación, puedes usar XAML, código o XAML Designer. En este tema se describe cómo trabajar con elementos en el Diseñador XAML en Visual Studio o Blend para Visual Studio.

## <a name="add-an-element-to-a-layout"></a>Adición de un elemento a un diseño

El *diseño* es el proceso de ajustar el tamaño de los elementos y colocarlos en una interfaz de usuario. Para colocar elementos visuales, debe colocarlos en un [Panel](xref:Windows.UI.Xaml.Controls.Panel) de diseño. `Panel` tiene una propiedad secundaria, que es una colección de tipos [FrameworkElement](xref:Windows.UI.Xaml.FrameworkElement). Se pueden usar distintos elementos secundarios de `Panel`, como [Canvas](xref:Windows.UI.Xaml.Controls.Canvas), [StackPanel](xref:Windows.UI.Xaml.Controls.StackPanel) y [Grid](xref:Windows.UI.Xaml.Controls.Grid), para que actúen como contenedores de diseño y para colocar y organizar los elementos en una página.

De forma predeterminada, un panel `Grid` sirve como contenedor de diseño de nivel superior dentro de una página o formulario. Puedes agregar paneles de diseño, controles u otros elementos en el diseño de página de nivel superior.

Para agregar un elemento a un diseño en el Diseñador XAML, realice una de estas acciones:

- Haga doble clic en un elemento del **Cuadro de herramientas** (o seleccione un elemento del Cuadro de herramientas y presione **Entrar**).

- Arrastre un elemento del **Cuadro de herramientas** a la mesa de trabajo.

- En el **Cuadro de herramientas**, seleccione una de las herramientas de dibujo (como [Elipse](xref:Windows.UI.Xaml.Shapes.Ellipse) o [Rectángulo](xref:Windows.UI.Xaml.Shapes.Rectangle)) y después dibuje un elemento en el panel activo.

## <a name="change-the-layering-order-of-elements"></a>Cambio del orden de distribución en capas de los elementos

Cuando haya dos elementos en la mesa de trabajo en XAML Designer, aparecerá un elemento delante del otro en el orden de distribución en capas. En la parte inferior de la lista de elementos de la ventana Esquema del documento se encuentra el elemento que se sitúa en primer plano (excepto cuando se establece la propiedad **ZIndex** de un elemento). Cuando se inserta un elemento en una página, un formulario o un contenedor de diseño, el elemento se coloca automáticamente delante de los demás elementos en el elemento de contenedor activo. Para cambiar el orden de los elementos, puede usar los comandos de **Ordenar** o arrastrar los elementos en el árbol de objetos de la ventana Esquema del documento.

Para cambiar el orden de distribución en capas, realice una de estas acciones:

- En la ventana **Esquema del documento**, arrastre los elementos hacia arriba o hacia abajo para crear el orden de distribución en capas deseado.

- En la ventana Esquema del documento o en la mesa de trabajo, haga clic con el botón derecho en el elemento cuyo orden de distribución en capas quiere cambiar, elija **Orden** y, después, haga clic en una de las opciones siguientes:

  - **Traer al frente** para traer el elemento al primer plano del orden.

  - **Traer adelante** para traer el elemento un nivel hacia adelante en el orden.

  - **Enviar atrás** para enviar el elemento un nivel hacia atrás en el orden.

  - **Enviar al fondo** para enviar el elemento a la última posición del orden.

- Cambie la propiedad **ZIndex** en la sección **Diseño** en la ventana Propiedades. En el caso de los elementos superpuestos, la propiedad **ZIndex** tiene prioridad sobre el orden de los elementos que se muestran en la ventana Esquema del documento. Cuando los elementos se superponen, aparece un elemento con un valor **ZIndex** más alto delante.

## <a name="change-the-alignment-of-an-element"></a>Cambio de la alineación de un elemento

Puede alinear los elementos en la mesa de trabajo usando comandos de menú o arrastrando los elementos a las guías de alineación.

Una *guía de alineación* es una indicación visual que ayuda a alinear un elemento con respecto a otros elementos de la aplicación.

Para alinear dos o más elementos mediante los comandos de menú:

1. Selecciona los elementos que desees alinear. Puede seleccionar varios elementos si mantiene presionada la tecla **Ctrl** mientras los selecciona.

2. Seleccione una de las propiedades siguientes en **HorizontalAlignment** en la sección **Diseño** de la ventana Propiedades: **Izquierda**, **Centro**, **Derecha** o **Ajustar**.

3. Seleccione una de las propiedades siguientes en **VerticalAlignment** en la sección **Diseño** de la ventana Propiedades: **Superior**, **Centro**, **Inferior** o **Ajustar**.

Para alinear dos o más elementos mediante guías de alineación, en el Diseñador XAML, en un diseño que contenga al menos dos elementos, arrastre o cambie el tamaño de uno de los elementos de modo que el borde se alinee con otro elemento.

Cuando los bordes estén alineados, aparecerá un *límite de alineación* para indicar la alineación. El límite de alineación es una línea roja discontinua. Los límites de alineación aparecen solamente cuando está habilitado el **ajuste a las guías de alineación** . Para ver una ilustración de la mesa de trabajo que muestra los límites de alineación, vea [Crear una IU con el Diseñador XAML](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="change-an-elements-margins"></a>Cambio de los márgenes de un elemento

En XAML Designer, los márgenes determinan la cantidad de espacio vacío que hay alrededor de un elemento en la mesa de trabajo. Por ejemplo, los márgenes especifican la cantidad de espacio entre los bordes exteriores de un elemento y los límites de un panel de `Grid` que contiene el elemento. Los márgenes también especifican la cantidad de espacio que hay entre los objetos que están contenidos en un `StackPanel`.

Para cambiar los márgenes de un elemento en la ventana Propiedades:

1. Selecciona el elemento cuyos márgenes deseas cambiar.

2. En **Diseño**, en la ventana Propiedades, cambie el valor (en píxeles o unidades independientes del dispositivo, que tienen un tamaño aproximado de 1/96 de pulgada) de cualquiera de las propiedades de **Margen** (**Superior**, **Izquierdo**, **Derecho** o **Inferior**).

En la mesa de trabajo, para cambiar los márgenes de un elemento con respecto a su contenedor de diseño, haga clic en los *adornos de margen* que aparecen alrededor del elemento cuando el elemento esté seleccionado y se encuentre dentro de un contenedor de diseño. Para obtener una ilustración que muestra los adornos de margen, vea [Crear una IU con el Diseñador XAML](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

Si el adorno del margen está abierto, ya sea vertical u horizontalmente, el margen no está establecido. Si el adorno del margen está cerrado, ese margen está establecido.

Cuando se abre el control Adorner de margen y el margen opuesto no está establecido, el margen opuesto se establece en el valor correcto de acuerdo con la ubicación del elemento en la mesa de trabajo. Para los márgenes opuestos, como **Izquierdo** y **Derecho**, siempre se establece al menos una propiedad.

> [!IMPORTANT]
> Los elementos incluidos dentro de algunos contenedores de distribución, como [Canvas](xref:Windows.UI.Xaml.Controls.Canvas), no tienen adornos del margen. Los elementos incluidos dentro de [StackPanel](xref:Windows.UI.Xaml.Controls.StackPanel) tienen adornos del margen para los márgenes izquierdo y derecho o para los márgenes superior e inferior, en función de la orientación de `StackPanel`.

## <a name="group-and-ungroup-elements"></a>Agrupación y desagrupación de elementos

Al agrupar dos o más elementos en XAML Designer se crea un nuevo contenedor de distribución y esos elementos quedan colocados en ese contenedor. Cuando se colocan dos o más elementos juntos en un contenedor de diseño, se podrá seleccionar, mover y transformar fácilmente el grupo como si los elementos de este fuesen un único elemento. La agrupación también permite identificar elementos que están relacionados entre sí de alguna manera, como los botones que constituyen un elemento de navegación. Cuando se desagrupan elementos, simplemente se elimina el contenedor de diseño que los contiene.

Para agrupar elementos en un nuevo contenedor de diseño:

1. Selecciona los elementos que desees agrupar. (Para seleccionar varios elementos, mantenga presionada la tecla **Ctrl** mientras hace clic en ellos).

2. Haga clic con el botón derecho en los elementos seleccionados, seleccione **Agrupar en** y, después, haga clic en el tipo de contenedor de diseño en el que quiera incluir el grupo.

    > [!TIP]
    > Si selecciona [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox), [Border](xref:Windows.UI.Xaml.Controls.Border) o [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer) para agrupar los elementos, estos se colocarán en un panel de [cuadrícula](xref:Windows.UI.Xaml.Controls.Grid) nuevo dentro del elemento [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox), [Border](xref:Windows.UI.Xaml.Controls.Border) o [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer). Si desagrupa los elementos en uno de estos contenedores de diseño, solo se eliminan los elementos [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox), [Border](xref:Windows.UI.Xaml.Controls.Border) o [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer) y el panel de [cuadrícula](xref:Windows.UI.Xaml.Controls.Grid) se conservará. Para eliminar el panel `Grid`, vuelve a desagrupar los elementos.

Para desagrupar elementos y eliminar el diseño, haga clic con el botón derecho en el grupo que quiere desagrupar y elija **Desagrupar**. También puede agrupar o desagrupar elementos haciendo clic con el botón derecho en los elementos seleccionados en la ventana Esquema del documento y haciendo clic en **Agrupar en** o **Desagrupar**.

## <a name="reset-the-element-layout"></a>Restablecimiento del diseño de un elemento

Puede restaurar los valores predeterminados de las propiedades de diseño específicas de un elemento mediante el comando Restablecer diseño. Con este comando puedes restablecer el margen, la alineación, el ancho, el alto y el tamaño de un elemento, ya sea de forma individual o colectiva.

Para restablecer el diseño de los elementos, haga clic con el botón secundario en el elemento en la ventana esquema del documento o en la mesa de presentación y, a continuación, seleccione **diseño**  >  **restablecer** *PropertyName*, donde *PropertyName* es la propiedad que desea restablecer (o elija **diseño**  >  **restablecer todo** para restablecer todas las propiedades de diseño del elemento).

## <a name="see-also"></a>Consulte también

- [Crear una IU con el Diseñador XAML](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
