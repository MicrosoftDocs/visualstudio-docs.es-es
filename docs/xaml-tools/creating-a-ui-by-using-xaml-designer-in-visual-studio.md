---
title: Información general del Diseñador XAML
ms.date: 03/03/2020
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
- Blend.Start.Dev12
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 31a31e413ecd39b7d15f8ea3cd0417c2493463ca
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "82921356"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>Crear una IU con el Diseñador XAML

El Diseñador XAML en Visual Studio y Blend para Visual Studio proporciona una interfaz visual para ayudarle a diseñar aplicaciones basadas en XAML, como WPF y UWP. Puede crear interfaces de usuario para sus aplicaciones arrastrando controles desde la ventana Cuadro de herramientas (ventana Recursos en Blend para Visual Studio) y estableciendo propiedades en la ventana Propiedades. También puede modificar el XAML directamente en la vista XAML.

En el caso de los usuarios avanzados, incluso es posible [personalizar el Diseñador XAML](https://github.com/microsoft/xaml-designer-extensibility/blob/master/documents/xaml-designer-extensibility-migration.md).

> [!NOTE]
> Xamarin. Forms no admite un diseñador XAML. Para ver las IUs de XAML de Xamarin. Forms y editarlas mientras la aplicación se está ejecutando, use la recarga activa de XAML para Xamarin. Forms. Para obtener más información, consulte la página de [recarga activa de XAML para Xamarin. Forms (versión preliminar)](/xamarin/xamarin-forms/xaml/hot-reload/) .

## <a name="xaml-designer-workspace"></a>Área de trabajo del Diseñador XAML

El área de trabajo en el Diseñador XAML consta de varios elementos de la interfaz visual. Estos incluyen la *mesa de trabajo* (que es la superficie de diseño visual), el editor XAML, la ventana Esquema del documento (la ventana Objetos y escala de tiempo en Blend para Visual Studio) y la ventana Propiedades. Para abrir el Diseñador XAML, haga clic con el botón derecho en un archivo XAML en el **Explorador de soluciones** y elija **Ver diseñador**.

El Diseñador XAML proporciona una vista XAML y una vista Diseño sincronizada del marcado XAML representado de la aplicación. Con un archivo XAML abierto en Visual Studio o en Blend para Visual Studio, puede cambiar entre la vista Diseño y la vista XAML mediante las pestañas **Diseño** y **XAML**. Puede usar el botón **Intercambiar paneles**![botón Intercambiar paneles en el Diseñador XAML](media/swap-panes.PNG)para cambiar la ventana que aparece en la parte superior: la mesa de trabajo o el editor XAML.

### <a name="design-view"></a>Vista de diseño

En la vista Diseño, la ventana que contiene la mesa de trabajo es la ventana activa y se puede usar como superficie de trabajo principal. Puede usarla para diseñar visualmente una página en la aplicación si agrega, dibuja o modifica elementos. Para más información, consulte [Trabajar con elementos en el Diseñador XAML](../xaml-tools/working-with-elements-in-xaml-designer.md). Esta ilustración muestra la mesa de trabajo en la vista Diseño.

![Vista de diseño del diseñador XAML](media/xaml-artboard.png)

Las siguientes características están disponibles en la mesa de trabajo:

**Guías de alineación**

Las guías de alineación son *límites de alineación* que aparecen como líneas discontinuas de color rojo para mostrar cuándo se alinean los bordes de los controles o cuándo se alinean las líneas base de texto. Los límites de alineación aparecen solamente cuando está habilitado el **ajuste a las guías de alineación** .

**Raíles Grid**

Los raíles de cuadrícula se usan para administrar las filas y columnas en un panel de [cuadrícula](xref:Windows.UI.Xaml.Controls.Grid). Puede crear y eliminar filas y columnas, así como ajustar el alto y el ancho relativos. El raíl Grid vertical, que aparece a la izquierda de la mesa de trabajo, se usa para las filas, mientras que la línea horizontal, que aparece en la parte superior, se usa para las columnas.

**Controles Adorner de Grid**

Un control Adorner de Grid aparece como un triángulo con una línea vertical u horizontal asociada a él en el raíl Grid. Cuando se arrastra un control Adorner de Grid, el ancho o el alto de las filas o las columnas adyacentes se actualiza al mover el mouse.

Los controles Adorner de Grid se usan para controlar el ancho y alto de las filas y las columnas de Grid. Puede agregar una columna o fila nuevas haciendo clic en el raíl Grid. Cuando se agrega una línea de fila o columna nueva para un panel Grid que tiene dos o más columnas o filas, aparece una minibarra de herramientas fuera del raíl que permite establecer explícitamente el ancho y el alto. La minibarra de herramientas permite establecer las opciones de ajuste de tamaño de las filas y columnas Grid.

![Control Adorner de cuadrícula en el Diseñador XAML](media/grid-adorner.png)

**Controladores de tamaño**

Los controladores de tamaño aparecen en los controles seleccionados y le permiten cambiar el tamaño del control. Cuando cambia el tamaño de un control, suelen aparecer los valores de ancho y alto para ayudarle a ajustar el tamaño del control. Para más información sobre cómo manipular los controles en la vista **Diseño**, consulte [Trabajar con elementos en el Diseñador XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

**Márgenes**

Los márgenes representan la cantidad de espacio fijo comprendido entre el borde de un control y el borde de su contenedor. Puede establecer los márgenes de un control mediante propiedades [Margin](xref:Windows.UI.Xaml.FrameworkElement.Margin) en **Diseño** en la ventana **Propiedades**.

**Controles Adorner de margen**

Use los controles Adorner de margen para cambiar los márgenes de un elemento con respecto a su contenedor de diseño. Cuando un control Adorner de margen está abierto, no se establece un margen y el control Adorner de margen muestra una cadena rota. Cuando el margen no está establecido, los elementos permanecen en su lugar cuando se cambia el tamaño del contenedor de diseño en tiempo de ejecución. Cuando el control Adorner de margen está cerrado, dicho control muestra una cadena intacta y los elementos se mueven con el margen cuando se cambie el tamaño del contenedor de diseño en tiempo de ejecución (el margen permanece fijo).

**Manipuladores de elemento**

Puede modificar un elemento con los manipuladores de elemento que aparecen en la mesa de trabajo cuando se mueve el puntero del mouse sobre los vértices del cuadro azul que rodea al elemento. Estos manipuladores permiten girar, cambiar el tamaño, voltear, mover o agregar un radio de redondeo al elemento. El símbolo del manipulador de elemento varía según la función y cambia según la ubicación exacta del puntero. Si no ve los manipuladores de elemento, asegúrese de que el elemento está seleccionado.

En la vista **Diseño**, en el área inferior izquierda de la ventana, están disponibles otros comandos de la mesa de trabajo, tal como se muestra aquí:

![Comandos de la Vista de diseño](media/xaml-design-view-controls.png)

Estos comandos están disponibles en esta barra de herramientas:

**Zoom**

El zoom le permite cambiar el tamaño de la superficie de diseño. Puede usar un zoom con un valor del 12,5 % al 800 %, o bien seleccionar opciones como **Ajustar a la selección** y **Ajustarse a todos**.

**Mostrar u ocultar cuadrícula de ajuste**

Muestra u oculta la cuadrícula de ajuste que hace visibles las líneas de cuadrícula. Las líneas de cuadrícula se usan al habilitar **Ajustar a las líneas de cuadrícula** o **Ajustar a las guías de alineación**.

**Activar o desactivar el ajuste a las líneas de cuadrícula**

Si está habilitado el **ajuste a las líneas de cuadrícula** , un elemento tiende a alinearse con la línea de cuadrícula vertical y horizontal más cercana al arrastrarla a la mesa de la mesa.

**Alternar el fondo de la mesa de trabajo**

Alterna entre un fondo claro y uno oscuro.

**Activar o desactivar el ajuste a las guías de alineación**

Las guías de alineación le ayudan a alinear los controles entre sí. Si el **ajuste a las guías de alineación** está habilitado, al arrastrar un control en relación con otros controles, aparecerán los límites de alineación cuando los bordes y el texto de algunos controles estén alineados horizontal o verticalmente. El límite de alineación es una línea roja discontinua.

**Deshabilitar el código de proyecto**

Deshabilita el [código de proyecto](debugging-or-disabling-project-code-in-xaml-designer.md), por ejemplo, los controles personalizados y los convertidores de valores, y recarga el diseñador.

### <a name="xaml-view"></a>Vista XAML

En la vista **XAML**, la ventana que contiene el editor XAML es la ventana activa, y el Editor XAML es la herramienta de creación principal. El lenguaje XAML proporciona un vocabulario declarativo basado en XML para especificar la interfaz de usuario de una aplicación. La vista XAML incluye IntelliSense, formato automático, resaltado de sintaxis y navegación por etiquetas. En la imagen siguiente se muestra una vista XAML con un menú de IntelliSense abierto:

![Vista XAML](media/xaml-editor.png)

## <a name="document-outline-window"></a>Ventana Esquema del documento

La ventana Esquema del documento de Visual Studio es similar a la ventana [Objetos y escala de tiempo](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) de Blend para Visual Studio. Esquema de documento le ayuda a realizar estas tareas:

- Ver la estructura jerárquica de todos los elementos de la mesa de trabajo.

- Seleccione los elementos para poder modificarlos. Por ejemplo, puede moverlos por la jerarquía o establecer sus propiedades en el ventana Propiedades. Para más información, consulte [Trabajar con elementos en el Diseñador XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

- Crear y modificar plantillas para elementos que son controles.

- [Crear animaciones](animate-objects-in-xaml-designer.md) (solo en Blend para Visual Studio).

Para ver la ventana esquema del documento en Visual Studio, en la barra de menús, seleccione **Ver** > **otro** > **esquema del documento**de Windows.
Para ver la ventana de objetos y escala de tiempo en Blend para Visual Studio, en la barra de menús, seleccione **Ver** > **esquema del documento**.

![Ventana Esquema del documento en Visual Studio](media/document-outline-window.png)

La vista principal de la ventana Esquema del documento/Objetos y escala de tiempo muestra la jerarquía de un documento en una estructura de árbol. Puede usar la naturaleza jerárquica del esquema del documento para examinar el documento en los distintos niveles de detalle y para bloquear y ocultar elementos individualmente o en grupos. Las siguientes opciones están disponibles en la ventana esquema/Objetos y escala de tiempo del documento:

**Mostrar u ocultar**

Muestra u oculta los elementos de la mesa de trabajo. Cuando se muestra, aparece como el símbolo de un ojo. También puede presionar **Ctrl**+**h** para ocultar un elemento y **desplazar**+**Ctrl**+**h** para mostrarlo.

**Bloquear o desbloquear**

Bloquea o desbloquea los elementos de la mesa de trabajo. Los elementos bloqueados no se pueden modificar. Cuando se bloquea un elemento, aparece un símbolo de candado. También puede presionar **Ctrl**+**l** para bloquear un elemento y **MAYÚS**+**Ctrl**+**l** para desbloquearlo.

**Devolver ámbito a pageRoot**

La opción que aparece en la parte superior de la ventana Esquema del documento/Objetos y escala de tiempo, que muestra un símbolo de flecha hacia arriba, se mueve al ámbito anterior. Esta opción solo es aplicable cuando se está en el ámbito de un estilo o una plantilla.

## <a name="properties-window"></a>Propiedades (ventana)

La ventana **Propiedades** permite establecer valores de propiedad en los controles. Este es su aspecto:

![Propiedades (ventana)](media/xaml-designer-properties-window.png)

Hay varias opciones en la parte superior de la ventana **Propiedades**:

- Cambie el nombre del elemento actualmente seleccionado en el cuadro **Nombre**.
- En la esquina superior izquierda, hay un icono que representa el elemento actualmente seleccionado.
- Para organizar las propiedades por categoría o alfabéticamente, haga clic en **Categoría**, **Nombre**u **Origen** en la lista **Organizar por** .
- Para ver la lista de eventos de un control, haga clic en el botón **Eventos**, que aparece como un símbolo de rayo.
- Para buscar una propiedad, empiece a escribir el nombre de la propiedad en el cuadro de búsqueda. La ventana **Propiedades** muestra las propiedades que coinciden con la búsqueda a medida que escribe.

Algunas propiedades permiten establecer propiedades avanzadas si selecciona un botón de flecha hacia abajo.

A la derecha de cada propiedad de valor se encuentra un *marcador de propiedad* que aparece como un símbolo de cuadro. La apariencia del marcador de propiedad indica si se aplicó a la propiedad un enlace de datos o un recurso. Por ejemplo, un símbolo de cuadro blanco indica un valor predeterminado, un símbolo de cuadro negro suele indicar que se ha aplicado un recurso local y un símbolo de cuadro naranja suele indicar que se ha aplicado un enlace de datos. Al hacer clic en el marcador de propiedad, puede navegar a la definición de un estilo, abrir el generador de enlace de datos o abrir el selector de recursos.

Para más información sobre cómo usar las propiedades y controlar los eventos, consulte [Introducción a los controles y patrones](/windows/uwp/design/controls-and-patterns/controls-and-events-intro).

## <a name="see-also"></a>Consulte también

- [Trabajo con elementos en el Diseñador XAML](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Cómo crear y aplicar un recurso](../xaml-tools/how-to-create-and-apply-a-resource.md)
- [Tutorial: Enlace a datos en el Diseñador XAML](../xaml-tools/walkthrough-binding-to-data-in-xaml-designer.md)
