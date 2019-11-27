---
title: 'Tutorial: Crear una UI usando el Diseñador XAML'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 879d8457a0f5fd4bf63a2d69a4f3f026ce4c6fe1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74294664"
---
# <a name="creating-a-ui-by-using-xaml-designer-in-visual-studio"></a>Crear una IU con el Diseñador XAML en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El Diseñador XAML en Visual Studio proporciona una interfaz visual para ayudarle a diseñar aplicaciones de la Tienda Windows, Windows Phone, WPF y Silverlight basadas en XAML. Puede crear interfaces de usuario para sus aplicaciones arrastrando controles desde el **Cuadro de herramientas** y estableciendo las propiedades en la ventana **Propiedades** . También puede modificar el XAML directamente en la vista XAML.

 Para tareas de diseño XAML avanzadas, como animaciones y comportamientos, consulte [Creating a UI by using Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="xaml-designer-workspace"></a>Área de trabajo del Diseñador XAML
 El área de trabajo en el Diseñador XAML consta de varios elementos de la interfaz visual. Entre estos se incluyen la mesa de trabajo, el Editor XAML, la ventana Dispositivo, la ventana Esquema del documento y la ventana Propiedades. Para abrir el Diseñador XAML, haga clic con el botón derecho en un archivo XAML en el **Explorador de soluciones** y elija **Ver diseñador**.

## <a name="authoring-views"></a>Vistas de creación
 El Diseñador XAML proporciona una vista XAML y una vista Diseño sincronizada del marcado XAML representado de la aplicación. Con un archivo XAML abierto en Visual Studio, puede cambiar entre la vista Diseño y la vista XAML mediante las pestañas **Diseño** y **XAML** . Puede usar el botón **Intercambiar paneles** para cambiar la ventana que aparece en la parte superior: la mesa de trabajo o el Editor XAML.

 En la vista Diseño, la ventana que contiene la *mesa de trabajo* es la ventana activa y se puede usar como superficie de trabajo principal. Puede usarla para diseñar visualmente una página en la aplicación agregando o dibujando elementos y modificándolos. Para obtener más información, consulta [Working with elements in XAML Designer](../designers/working-with-elements-in-xaml-designer.md). Esta ilustración muestra la mesa de trabajo en la vista Diseño.

 ![Vista de diseño de Diseñador XAML](../designers/media/xaml-editor-design-view.png "xaml_editor_design_view")

 Las siguientes características están disponibles en la mesa de trabajo:

 **Guías de alineación** Las guías de alineación son *límites de alineación* que aparecen como líneas discontinuas de color rojo para mostrar cuándo se alinean los bordes de los controles o cuándo se alinean las líneas base de texto. Los límites de alineación aparecen solamente cuando está habilitado el **ajuste a las guías de alineación** .

 **Raíles Grid** Los raíles `Grid` se usan para administrar las filas y columnas en un panel [Grid](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx). Puede crear y eliminar filas y columnas, así como ajustar el alto y el ancho relativos. El raíl Grid vertical, que aparece a la izquierda de la mesa de trabajo, se usa para las filas, mientras que la línea horizontal, que aparece en la parte superior, se usa para las columnas.

 **Controles Adorner de Grid** Un control Adorner de `Grid` aparece como un triángulo con una línea vertical u horizontal asociada a él en el raíl `Grid`. Cuando se arrastra un control Adorner de `Grid` , el ancho o el alto de las filas o las columnas adyacentes se actualiza al mover el mouse.

 Los controles Adorner de`Grid` se usan para controlar el ancho y alto de las filas y las columnas de `Grid`. Puede agregar una columna o fila nuevas haciendo clic en el raíl `Grid` . Cuando se agrega una línea de fila o columna nueva para un panel `Grid` que tiene dos o más columnas o filas, aparece una minibarra de herramientas fuera del raíl que le permite establecer explícitamente el ancho y el alto. La minibarra de herramientas le permite establecer las opciones de ajuste de tamaño de las filas y columnas `Grid` .

 **Controladores de tamaño** Los controladores de tamaño aparecen en los controles seleccionados y le permiten cambiar el tamaño del control. Cuando cambia el tamaño de un control, suelen aparecer los valores de ancho y alto para ayudarle a ajustar el tamaño del control. Para obtener más información sobre cómo manipular los controles en la Vista de diseño, consulta [Working with elements in XAML Designer](../designers/working-with-elements-in-xaml-designer.md).

 **Márgenes** Los márgenes representan la cantidad de espacio fijo comprendido entre el borde de un control y el borde de su contenedor. Puede establecer los márgenes de un control mediante propiedades [Margin](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.margin.aspx) en **Diseño** en la ventana Propiedades.

 **Controles Adorner de margen** Puede usar los controles Adorner de margen para cambiar los márgenes de un elemento con respecto a su contenedor de diseño. Cuando un control Adorner de margen está abierto, no se establece un margen y el control Adorner de margen muestra una cadena rota. Cuando el margen no está establecido, los elementos permanecen en su lugar cuando se cambia el tamaño del contenedor de diseño en tiempo de ejecución. Cuando el control Adorner de margen está cerrado, dicho control muestra una cadena intacta y los elementos se moverán con el margen cuando se cambie el tamaño del contenedor de diseño en tiempo de ejecución (el margen permanece fijo).

 **Manipuladores de elementos** Puede modificar un elemento con los manipuladores de elemento que aparecen en la mesa de trabajo cuando se mueve el puntero del mouse sobre los vértices del cuadro azul que rodea al elemento. Estos manipuladores permiten girar, cambiar el tamaño, voltear, mover o agregar un radio de redondeo al elemento. El símbolo del manipulador de elemento varía según la función y cambia según la ubicación exacta del puntero. Si no ve los manipuladores de elemento, asegúrese de que el elemento está seleccionado.

 En la vista Diseño, en el área inferior izquierda de la pantalla, están disponibles otros comandos de la mesa de trabajo, tal como se muestra aquí:

 ![Vista de diseño comandos](../designers/media/xaml-editor-design-controls.png "xaml_editor_design_controls")

 Estos comandos están disponibles en esta barra de herramientas:

 **Zoom** El zoom le permite cambiar el tamaño de la superficie de diseño. Puede usar un zoom con un valor del 12,5% al 800%, o bien seleccionar opciones como **Ajustar a la selección** y **Ajustarse a todos**.

 **Mostrar u ocultar cuadrícula de ajuste** Muestra u oculta la cuadrícula de ajuste que hace visibles las líneas de cuadrícula. Se usan líneas de cuadrícula cuando está habilitado **Ajustar a las líneas de cuadrícula** o **Ajustar a las guías de alineación** .

 **Activar o desactivar el ajuste a las líneas de cuadrícula** Si el **ajuste a las líneas de cuadrícula** está habilitado cuando se arrastra un elemento por la mesa de trabajo, el elemento tiende a alinearse con la línea de cuadrícula vertical u horizontal más cercana.

 **Activar o desactivar el ajuste a las guías de alineación** Las guías de alineación le ayudan a alinear los controles entre sí. Si el **ajuste a las guías de alineación** está habilitado, al arrastrar un control en relación con otros controles, aparecerán los límites de alineación cuando los bordes y el texto de algunos controles estén alineados horizontal o verticalmente. El límite de alineación es una línea roja discontinua.

 En la vista XAML, la ventana que contiene el editor XAML es la ventana activa, y el Editor XAML es la herramienta de creación principal. El lenguaje XAML proporciona un vocabulario declarativo basado en XML para especificar la interfaz de usuario de una aplicación. La vista XAML incluye IntelliSense, formato automático, resaltado de sintaxis y navegación por etiquetas. Esta ilustración muestra la vista XAML:

 ![Vista XAML](../designers/media/xaml-editor.png "xaml_editor")

 **Barra de vista en dos paneles** La barra de vista en dos paneles aparece en la parte superior de la vista XAML cuando el Editor XAML está en la ventana inferior. La barra de vista en dos paneles permite controlar los tamaños relativos de la vista Diseño y la vista XAML. También puede intercambiar las ubicaciones de las vistas (con el botón **Intercambiar paneles** ), especificar si las vistas están organizadas horizontal o verticalmente y contraer cualquiera de las vistas.

 **Zoom de marcado** El zoom de marcado permite cambiar el tamaño de la vista XAML. Puede hacer zoom del 20% al 400%.

## <a name="device-window"></a>Ventana de dispositivo
 La ventana Dispositivo del Diseñador XAML permite simular en tiempo de diseño varias vistas, presentaciones y opciones de visualización para el proyecto de la Tienda Windows o Windows Phone. La ventana Dispositivo está disponible en el menú **Diseño** cuando se trabaja en el Diseñador XAML. Este es su aspecto:

 ![Ventana del dispositivo](../designers/media/xaml-editor-device-panel.png "xaml_editor_device_panel")

 Estas son las opciones disponibles en la ventana Dispositivo:

 **Presentación** Especifica los diferentes tamaños y resoluciones de la aplicación.

 **Orientación** Especifica las diferentes orientaciones de la aplicación: **Horizontal** o **Vertical**.

 **Borde** Especifica las diferentes alineaciones de los bordes de la aplicación: **Ambos**, **Izquierdo**, **Derecho** o **Ninguno**.

 **Contraste alto** Muestra una vista previa de la aplicación en función de la configuración de contraste seleccionada. Al establecerse en un valor distinto de **Predeterminado**, esta configuración invalidará la propiedad `RequestedTheme` establecida en App.xaml.

 **Invalidar ajuste de escala** Activa o desactiva la emulación de un ajuste de escala del documento en la superficie de diseño. Esto permite aumentar el porcentaje de escala en un factor. Active la casilla para activar la emulación. Por ejemplo, si el porcentaje de ajuste de escala es del 100%, el documento dentro de la superficie de diseño escalará hasta el 140%. Esta opción está deshabilitada si el porcentaje actual de ajuste de escala es de 180.

 **Ancho mínimo** Especifica el ajuste de ancho mínimo. El ancho mínimo se puede cambiar en App.xaml.

 **Tema** Especifica el tema de la aplicación. Por ejemplo, puede cambiar entre un tema oscuro y un tema claro.

 **Mostrar cromo** Activa y desactiva el marco de tableta simulado alrededor de la aplicación en la vista Diseño. Active la casilla para mostrar el marco.

 **Recortar para mostrar** Especifica el modo de presentación. Seleccione la casilla para recortar el tamaño del documento con el tamaño de presentación.

## <a name="document-outline-window"></a>Ventana Esquema del documento
 La ventana Esquema del documento del Diseñador XAML ayuda a realizar estas tareas:

- Ver la estructura jerárquica de todos los elementos de la mesa de trabajo.

- Seleccionar elementos para poder modificarlos (moverlos por la jerarquía, modificarlos en la mesa de trabajo, establecer sus propiedades en la ventana Propiedades, etc.). Para obtener más información, consulta [Working with elements in XAML Designer](../designers/working-with-elements-in-xaml-designer.md).

- Crear y modificar plantillas para elementos que son controles.

- Usar el menú contextual para los elementos seleccionados. El mismo menú también está disponible para los elementos seleccionados en la mesa de trabajo.

  Para ver la ventana Esquema del documento, en la barra de menús elija **Vista**, **Otras ventanas**, **Esquema del documento**.

  ![Ventana esquema del documento](../designers/media/xaml-editor-doc-outline.png "xaml_editor_doc_outline")

  Estas son las opciones disponibles en la ventana Esquema del documento:

  **Esquema del documento** La vista principal de la ventana Esquema del documento muestra la jerarquía de un documento en una estructura de árbol. Puede usar la naturaleza jerárquica del esquema del documento para examinar el documento en los distintos niveles de detalle y para bloquear y ocultar elementos individualmente o en grupos.

  **Mostrar/ocultar** Muestra u oculta los elementos de la mesa de trabajo que corresponden a elementos del esquema del documento. Use los botones **Mostrar u ocultar** , en los que aparece un símbolo de un ojo si se muestran los elementos, o bien presione CTRL+H para ocultar elementos y CTRL+MAYÚS+H para mostrarlos.

  **Bloquear/desbloquear** Bloquea o desbloquea los elementos de la mesa de trabajo que corresponden a elementos del esquema del documento. Los elementos bloqueados no se pueden modificar. Use los botones **Bloquear o desbloquear** , en los que aparece un símbolo de un candado si se bloquean los elementos, o bien presione CTRL+L para bloquear elementos y CTRL+MAYÚS+L para desbloquearlos.

  **Devolver ámbito a pageRoot** La opción de la parte superior de la ventana Esquema del documento, que muestra un símbolo de flecha hacia arriba, devuelve el esquema del documento al ámbito anterior. Esta opción solo es aplicable cuando se está en el ámbito de un estilo o una plantilla.

## <a name="properties-window"></a>Propiedades (ventana)
 La ventana Propiedades permite establecer valores de propiedad en los controles. Este es su aspecto:

 ![Ventana Propiedades](../designers/media/xaml-editor-prop-window.png "xaml_editor_prop_window")

 Hay varias opciones en la parte superior de la ventana Propiedades. Puede cambiar el nombre del elemento seleccionado actualmente mediante el cuadro **Nombre** . En la esquina superior izquierda, hay un icono que representa el elemento actualmente seleccionado. Para organizar las propiedades por categoría o alfabéticamente, haga clic en **Categoría**, **Nombre**u **Origen** en la lista **Organizar por** . Para ver la lista de eventos de un control, haga clic en el botón **Eventos** , que muestra un símbolo de rayo. Para buscar una propiedad, empiece a escribir el nombre de la propiedad en el cuadro **Buscar propiedades** . La ventana Propiedades muestra las propiedades que coinciden con la búsqueda a medida que escribe. Algunas propiedades permiten establecer propiedades avanzadas si selecciona un botón de flecha hacia abajo. Para obtener más información sobre el uso de propiedades y el control de eventos, consulte [Inicio rápido: agregar controles y administrar eventos (XAML)](https://go.microsoft.com/fwlink/?LinkID=247983)

 A la derecha de cada propiedad de valor se encuentra un *marcador de propiedad* que aparece como un símbolo de cuadro. La apariencia del marcador de propiedad indica si se aplicó a la propiedad un enlace de datos o un recurso. Por ejemplo, un símbolo de cuadro blanco indica un valor predeterminado, un símbolo de cuadro negro suele indicar que se ha aplicado un recurso local y un símbolo de cuadro naranja suele indicar que se ha aplicado un enlace de datos. Al hacer clic en el marcador de propiedad, puede navegar a la definición de un estilo, abrir el generador de enlace de datos o abrir el selector de recursos.

## <a name="see-also"></a>Vea también
 [Trabajar con elementos en diseñador XAML](../designers/working-with-elements-in-xaml-designer.md) [Cómo crear y aplicar un recurso](../designers/how-to-create-and-apply-a-resource.md) [Tutorial: enlazar a datos en diseñador XAML](../designers/walkthrough-binding-to-data-in-xaml-designer.md)
