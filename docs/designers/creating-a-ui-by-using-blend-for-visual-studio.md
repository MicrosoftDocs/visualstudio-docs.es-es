---
title: 'Creación de una interfaz de usuario: Blend para Visual Studio'
titleSuffix: ''
ms.date: 07/17/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b44f49c08be44ec16cbd90d06cef96cb091e67f6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934510"
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Creación de una interfaz de usuario con Blend para Visual Studio

Blend para Visual Studio le ayuda a diseñar aplicaciones web y de Windows basadas en XAML. Proporciona la misma experiencia de diseño XAML básica que Visual Studio y agrega diseñadores visuales para tareas avanzadas como animaciones y comportamientos. Para ver una comparación entre Blend y Visual Studio, vea [Diseño de XAML en Visual Studio y Blend para Visual Studio](../designers/designing-xaml-in-visual-studio.md).

Blend para Visual Studio es un componente de Visual Studio. Para instalar Blend, en el **instalador de Visual Studio** elija la carga de trabajo **Desarrollo de la plataforma universal de Windows** o **Desarrollo de escritorio de .NET**. Ambas cargas de trabajo incluyen el componente Blend para Visual Studio.

![Componentes de carga de trabajo de UWP](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![Componentes de carga de trabajo de desarrollo de escritorio de .NET](media/installer-dotnet-desktop.png)

Si no ha trabajado nunca con Blend para Visual Studio, tómese un momento para familiarizarse con las características exclusivas del área de trabajo. Este tema le servirá de paseo introductorio.

> [!NOTE]
> Para recorrer las características de diseño compartido como la mesa de trabajo, la ventana **Esquema del documento** y la ventana **Dispositivo**, vea [Crear una IU con el Diseñador XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="tour-of-the-tools-panel"></a>Paseo por el panel Herramientas 

Puede usar el panel **Herramientas** en Blend para Visual Studio para crear y modificar objetos en la aplicación. Para crear objetos, seleccione una herramienta y dibuje en la mesa de trabajo utilizando el mouse.

![Panel Herramientas](../designers/media/blend5toolspanel.png)

|||||
|-|-|-|-|
|![Herramientas de selección](../designers/media/b1_1.png)|**Herramientas de selección** Seleccione objetos y trazados.<br /><br /> Use la herramienta **Selección directa** para seleccionar objetos anidados y segmentos de trazados.|![Llamada A](../designers/media/b5_label_a.png)|**Herramientas de pincel y degradado**|
|![Herramientas de vista](../designers/media/b1_2.png)|**Herramientas de vista** Ajuste la vista de la mesa de trabajo, por ejemplo para movimiento panorámico y zoom.|![Llamada B](../designers/media/b5_label_b.png)|**Herramientas de trazado**|
|![Herramientas de pincel](../designers/media/b1_3.png)|**Herramientas de pincel** Trabaje con los atributos visuales de un objeto, por ejemplo, transformar un pincel, pintar un objeto o seleccionar los atributos de un objeto para aplicarlos a otro.|![Llamada C](../designers/media/b5_label_c.png)|**Herramientas de forma**|
|![Herramientas de objeto](../designers/media/b1_4.png)|**Herramientas de objeto** Dibuje en la mesa de trabajo los objetos más habituales, como trazados, formas, paneles de diseño, texto y controles.|![Llamada D](../designers/media/b5_label_d.png)|**Paneles de diseño**|
|![Herramientas de recursos](../designers/media/b1_5.png)|**Herramientas de activos** Acceda al panel **Activos** y muestre el último activo usado de la biblioteca.|![Llamada E](../designers/media/b5_label_e.png)|**Controles de texto**|
|||![Llamada F](../designers/media/b5_label_f.png)|**Controles comunes**|

**Vea un vídeo corto:** ![Configuración de las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png) [La barra de herramientas](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).

## <a name="tour-of-the-assets-panel"></a>Paseo por el panel Activos

Puede encontrar todos los controles en el panel **Activos**, similar al **Cuadro de herramientas** de Visual Studio. Además de los controles, encontrará todo lo que puede agregar a la mesa de trabajo en el panel **Activos**, incluidos estilos, elementos multimedia, comportamientos y efectos.

![Panel Activos](../designers/media/blend5_assets_panel.png)

|||
|-|-|
|![](../designers/media/b1_1.png)|**Cuadro de búsqueda** Escriba texto en el cuadro **Buscar** para filtrar la lista de activos.|
|![Modo de cuadrícula y modo de lista](../designers/media/b1_2.png)|**Modo de cuadrícula y Modo de lista** Permite alternar entre la vista **Modo de cuadrícula** y la vista **Modo de lista** de los activos.|
|![Categorías de recursos](../designers/media/b1_3.png)|**Categorías de activos** Haga clic en una categoría o subcategoría para ver la lista de activos de esa categoría.|
|![Estilos](../designers/media/b1_4.png)|**Estilos** Muestre todos los estilos que se encuentran en el diccionario de recursos.|
|![Descripción](../designers/media/b1_5.png)|**Descripción** Vea una descripción de la categoría o subcategoría de activos seleccionada.|

## <a name="tour-of-the-objects-and-timeline-panel"></a>Paseo por el panel Objetos y escala de tiempo

Utilice este panel para organizar los objetos en la mesa de trabajo y, si lo desea, para animarlos.

![Panel Objetos y escala de tiempo en modo de animación](../designers/media/b5_object_timeline_animation.png)

|||
|-|-|
|![Vista de objetos](../designers/media/b1_1.png)|**Vista de objetos** Vea el árbol visual de un documento. Se pueden mostrar varios niveles de detalle. También se pueden agregar capas para organizar aún más los objetos en la mesa de trabajo, lo que permite bloquear y ocultarlos como grupo.|
|![Indicador de modo de grabación](../designers/media/b1_2.png)|**Indicador de modo de grabación** Vea si se están grabando cambios de propiedad en una escala de tiempo.|
|![Selector de guiones gráficos](../designers/media/b1_3.png)|**Selector de guiones gráficos** Vea una lista de los guiones gráficos creados.|
|![Cerrar guión gráfico](../designers/media/b1_4.png)|**Cerrar guión gráfico** Cierre el guión gráfico actual.|
|![Opciones de guión gráfico](../designers/media/b1_5.png)|**Opciones de guión gráfico** Puede crear, duplicar, revertir, eliminar o cerrar un guión gráfico, y también cambiarle el nombre.|
|![Controles de reproducción](../designers/media/b1_6.png)|**Controles de reproducción** Navegue a través de la escala de tiempo. También puede *arrastrar el cabezal de reproducción* para navegar por la escala de tiempo.|
|![Devolver ámbito a](../designers/media/b1_7.png)|**Devolver ámbito a** Establezca de nuevo el ámbito de la vista de objetos en el ámbito u objeto raíz anterior. Solo puede hacerlo cuando está modificando un estilo o una plantilla.|
|![Registrar un fotograma clave](../designers/media/b1_8.png)|**Registro de un fotograma clave** Registre una instantánea de las propiedades del objeto seleccionado en el momento actual.|
|![Opciones de ajuste](../designers/media/b1_9.png)|**Opciones de ajuste** Establezca el ajuste de escala de tiempo, la resolución de ajuste y desactive el ajuste a la escala de tiempo.|
|![Mostrar ocultar bloquear desbloquear](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png)|**Mostrar/Ocultar**, **Bloquear/Desbloquear** Muestre u oculte las opciones de visibilidad y bloqueo para la vista de objetos.|
|![Posición del cabezal de reproducción en la escala de tiempo](../designers/media/b1_11.png)|**Posición del cabezal de reproducción en la escala de tiempo** Muestre la hora actual en milisegundos. Además, se puede escribir directamente un valor de tiempo en este campo para ir a un momento concreto. La precisión depende de la resolución de ajuste establecida en las **Opciones de ajuste**.|
|![Cabezal de reproducción](../designers/media/b1_12.png)|**Cabezal de reproducción** Determine el momento en el que se encuentra la animación. El cabezal de reproducción se puede arrastrar a lo largo de la escala de tiempo para obtener una vista previa de la animación.|
|![Fotogramas clave establecidos en escalas de tiempo](../designers/media/b1_13.png)|**Fotogramas clave establecidos en escalas de tiempo** Cambie el valor de una propiedad en un momento específico en el tiempo.|
|![Cambiar el orden de los objetos](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png)|**Cambiar orden de los objetos** Establezca el orden de presentación de los objetos. Haga clic en este botón para organizar los objetos de la vista de estructura por orden Z (de delante hacia atrás) o por orden de marcado (el orden en que aparecen en la vista **XAML**).|
|![Zoom de escala de tiempo](../designers/media/b1_15.png)|**Zoom de escala de tiempo** Establezca la resolución de zoom de la escala de tiempo. El acercamiento le permite modificar una animación con más detalle, mientras que el alejamiento muestra una visión general de lo que ocurre en períodos de tiempo más largos. Si se acerca pero no puede establecer un fotograma clave en la posición temporal que desee, compruebe si la resolución de ajuste es lo bastante alta.|
|![Llamada 16](../designers/media/b5_label_16.png)|**Área de composición de la escala de tiempo** Vea la escala de tiempo y mueva los fotogramas clave arrastrándolos o usando sus menús contextuales.|

## <a name="tour-of-the-properties-panel"></a>Paseo por el panel Propiedades

Utilice este panel para ver y modificar las propiedades de un objeto. También puede establecer esas propiedades directamente en la mesa de trabajo. Si lo hace, los cambios de propiedad se reflejarán en el panel **Propiedades**.

![Panel Propiedades](../designers/media/blend5_properties_panel.png)

**Categorías** Expanda y contraiga las categorías de propiedades. Haga clic en **Expandir** ![Expand](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png) y en **Contraer** ![Collapse](../designers/media/b5_collapse_button.png) para mostrar u ocultar los detalles de la categoría.

|||
|-|-|
|![Nombre y tipo](../designers/media/b1_1.png)|**Nombre y tipo** Vea el icono, el nombre y el tipo del objeto seleccionado.|
|![Organizar por](../designers/media/b1_2.png)|**Organizar por** Organice las propiedades alfabéticamente por nombre, origen o categoría.|
|![Propiedades de pincel](../designers/media/b1_3.png)|**Propiedades del pincel** Establezca las propiedades visuales de pinceles como los pinceles de relleno, trazo y primer plano.|
|![Editor de colores](../designers/media/b1_4.png)|**Editor de colores** Sirve para los pinceles de color sólido y degradado.|
|![Selector de colores](../designers/media/b1_5.png)|**Selector de color** Seleccione un color.|
|![Chips de color](../designers/media/b1_6.png)|**Chips de color** Vea los colores inicial, actual y último.|
|![Cuentagotas](../designers/media/b1_7.png)|**Cuentagotas** Use el color de cualquier elemento de la pantalla. El **Cuentagotas de color** está disponible cuando se selecciona **Pincel de color sólido**. El **Cuentagotas de degradado** está disponible cuando se selecciona **Pincel de degradado**.|
|![Propiedades y eventos](../designers/media/b1_8.png)|**Propiedades y eventos** Establezca las propiedades o elija los eventos para un elemento seleccionado.|
|![Cuadro de búsqueda](../designers/media/b1_9.png)|**Cuadro de búsqueda** Permite buscar propiedades. Filtre las propiedades que se muestran al escribir en el cuadro **Búsqueda**.|
|![Pestañas de editor de pinceles](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png)|**Pestañas del Editor de pinceles** Permite seleccionar un editor de pinceles. Puede elegir **Sin pincel**, **Pincel de color sólido**, **Pincel de degradado**, **Pincel de diseño en mosaico** o **Recurso de pincel**.|
|![Recurso de color](../designers/media/b1_11.png)|**Recursos de color** Aplique exactamente el mismo color a diferentes propiedades. La pestaña **Recursos de color** incluye **Recursos locales** y **Recursos del sistema**.|
|![Espacio de colores RGB](../designers/media/b1_12.png)|**Espacio de colores RGB** Modifique los colores mediante el ajuste de los valores de los editores de números **R**, **G** o **B** (rojo, verde, azul).|
|![Canal alfa](../designers/media/b1_13.png)|**Canal alfa** Modifique el valor alfa mediante el editor de números situado al lado de **A**.|
|![Convertir color en recurso](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png)|**Convertir color en recurso** Convierta el color seleccionado en un recurso de color. Los recursos de color están disponibles al hacer clic en la pestaña Recursos de color.|
|![](../designers/media/b1_15.png)|**Valor hexadecimal** Vea el valor hexadecimal del color mostrado.|
|![Llamada 16](../designers/media/b5_label_16.png)|**Control deslizante de degradado** Aparece únicamente si se selecciona un pincel de degradado.|
|![Mostrar propiedades avanzadas](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png)|**Mostrar propiedades avanzadas** Vea las categorías de propiedades que se usan con menos frecuencia.|

**Vea un vídeo corto:** ![Configuración de las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png) [El panel Propiedades](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).

## <a name="see-also"></a>Vea también

- [Insertar controles y modificar su comportamiento](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)
- [Animar objetos](../designers/animate-objects-in-xaml-designer.md)
- [Dibujar formas y trazados](../designers/draw-shapes-and-paths.md)
- [Diseño de XAML en Visual Studio y Blend para Visual Studio](../designers/designing-xaml-in-visual-studio.md)
