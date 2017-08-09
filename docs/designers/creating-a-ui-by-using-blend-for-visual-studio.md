---
title: "Creación de una interfaz de usuario con Blend para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 7/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Blend.Start.Dev12
ms.assetid: efd12263-cc2d-4081-a2bb-9a2cc17c442c
caps.latest.revision: 31
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 8124c2fc15bb6a62add758277a5d6946a24c36d1
ms.contentlocale: es-es
ms.lasthandoff: 07/18/2017

---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Creación de una interfaz de usuario con Blend para Visual Studio
Blend para Visual Studio le ayuda a diseñar aplicaciones web y de Windows basadas en XAML. Proporciona la misma experiencia de diseño XAML básica que Visual Studio y agrega diseñadores visuales para tareas avanzadas como animaciones y comportamientos. (Para ver una comparación entre las herramientas, consulte [Diseño de XAML en Visual Studio y Blend para Visual Studio](../designers/designing-xaml-in-visual-studio.md)).
  
Dado que Blend para Visual Studio se incluye como parte de Visual Studio, no es necesario descargarlo. Pero debe seleccionarlo en el instalador de Visual Studio para instalarlo en el sistema.  
 
Si no ha trabajado nunca con Blend para Visual Studio, tómese un momento para familiarizarse con las características exclusivas del área de trabajo. Este tema le servirá de paseo introductorio.  
  
> [!NOTE]
>  Para recorrer las características de diseño compartido como la mesa de trabajo, la ventana Esquema del documento y la ventana Dispositivo, vea [Crear una IU con el Diseñador XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
 **En este tema**:  
  
-   [Paseo por el panel Herramientas](#Tools)  
  
-   [Paseo por el panel Activos](#Assets)  
  
-   [Paseo por el panel Objetos y escala de tiempo](#Objects)  
  
-   [Paseo por el panel Propiedades](#Properties)  
  
##  <a name="Tools"></a> Paseo por el panel Herramientas  
 Puede usar el panel **Herramientas** en Blend para Visual Studio para crear y modificar objetos en la aplicación. Para crear objetos, seleccione una herramienta y dibuje en la mesa de trabajo utilizando el mouse.  
  
 ![Panel Herramientas](../designers/media/blend5toolspanel.png "Blend5Toolspanel")  
  
|||||  
|-|-|-|-|  
|![](../designers/media/b1_1.png "B1_1")|**Herramientas de selección** Seleccione objetos y trazados.<br /><br /> Use la herramienta **Selección directa** para seleccionar objetos anidados y segmentos de trazados.|![Llamada A](../designers/media/b5_label_a.png "b5_label_A")|**Herramientas de pincel y degradado**|  
|![](../designers/media/b1_2.png "B1_2")|**Herramientas de vista** Ajuste la vista de la mesa de trabajo, por ejemplo para movimiento panorámico y zoom.|![Llamada B](../designers/media/b5_label_b.png "b5_label_B")|**Herramientas de trazado**|  
|![](../designers/media/b1_3.png "B1_3")|**Herramientas de pincel** Trabaje con los atributos visuales de un objeto, por ejemplo, transformar un pincel, pintar un objeto o seleccionar los atributos de un objeto para aplicarlos a otro.|![Llamada C](../designers/media/b5_label_c.png "b5_label_C")|**Herramientas de forma**|  
|![](../designers/media/b1_4.png "B1_4")|**Herramientas de objeto** Dibuje en la mesa de trabajo los objetos más habituales, como trazados, formas, paneles de diseño, texto y controles.|![Llamada D](../designers/media/b5_label_d.png "b5_label_D")|**Paneles de diseño**|  
|![](../designers/media/b1_5.png "B1_5")|**Herramientas de activos** Acceda al panel **Activos** y muestre el último activo usado de la biblioteca.|![Llamada E](../designers/media/b5_label_e.png "b5_label_E")|**Controles de texto**|  
|||![Llamada E](../designers/media/b5_label_f.png "b5_label_F")|**Controles comunes**|  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [La barra de herramientas](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).  
  
##  <a name="Assets"></a> Paseo por el panel Activos  
 Puede encontrar todos los controles en el panel **Activos**, similar al **Cuadro de herramientas** de Visual Studio. Además de los controles, encontrará todo lo que puede agregar a la mesa de trabajo en el panel **Activos**, incluidos estilos, elementos multimedia, comportamientos y efectos.  
  
 ![Panel Activos](../designers/media/blend5_assets_panel.png "Blend5_Assets_panel")  
  
|||  
|-|-|  
|![](../designers/media/b1_1.png "B1_1")|**Cuadro de búsqueda** Escriba texto en el cuadro **Buscar** para filtrar la lista de activos.|  
|![](../designers/media/b1_2.png "B1_2")|**Modo de cuadrícula y Modo de lista** Permite alternar entre la vista **Modo de cuadrícula** y la vista **Modo de lista** de los activos.|  
|![](../designers/media/b1_3.png "B1_3")|**Categorías de activos** Haga clic en una categoría o subcategoría para ver la lista de activos de esa categoría.|  
|![](../designers/media/b1_4.png "B1_4")|**Estilos** Muestre todos los estilos que se encuentran en el diccionario de recursos.|  
|![](../designers/media/b1_5.png "B1_5")|**Descripción** Vea una descripción de la categoría o subcategoría de activos seleccionada.|  
  
##  <a name="Objects"></a> Paseo por el panel Objetos y escala de tiempo  
 Utilice este panel para organizar los objetos en la mesa de trabajo y, si lo desea, para animarlos.  
  
 ![Panel Objetos y escala de tiempo en modo de animación](../designers/media/b5_object_timeline_animation.png "b5_object_timeline_animation")  
  
|||  
|-|-|  
|![](../designers/media/b1_1.png "B1_1")|**Vista de objetos** Vea el árbol visual de un documento. Se pueden mostrar varios niveles de detalle. También se pueden agregar capas para organizar aún más los objetos en la mesa de trabajo, lo que permite bloquear y ocultarlos como grupo.|  
|![](../designers/media/b1_2.png "B1_2")|**Indicador de modo de grabación** Vea si se están grabando cambios de propiedad en una escala de tiempo.|  
|![](../designers/media/b1_3.png "B1_3")|**Selector de guiones gráficos** Vea una lista de los guiones gráficos creados.|  
|![](../designers/media/b1_4.png "B1_4")|**Cerrar guión gráfico** Cierre el guión gráfico actual.|  
|![](../designers/media/b1_5.png "B1_5")|**Opciones de guión gráfico** Puede crear, duplicar, revertir, eliminar o cerrar un guión gráfico, y también cambiarle el nombre.|  
|![](../designers/media/b1_6.png "B1_6")|**Controles de reproducción** Navegue a través de la escala de tiempo. También puede *arrastrar el cabezal de reproducción* para navegar por la escala de tiempo.|  
|![](../designers/media/b1_7.png "B1_7")|**Devolver ámbito a** Establezca de nuevo el ámbito de la vista de objetos en el ámbito u objeto raíz anterior. Solo puede hacerlo cuando está modificando un estilo o una plantilla.|  
|![](../designers/media/b1_8.png "B1_8")|**Registro de un fotograma clave** Registre una instantánea de las propiedades del objeto seleccionado en el momento actual.|  
|![](../designers/media/b1_9.png "B1_9")|**Opciones de ajuste** Establezca el ajuste de escala de tiempo, la resolución de ajuste y desactive el ajuste a la escala de tiempo.|  
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**Mostrar/Ocultar**, **Bloquear/Desbloquear** Muestre u oculte las opciones de visibilidad y bloqueo para la vista de objetos.|  
|![](../designers/media/b1_11.png "B1_11")|**Posición del cabezal de reproducción en la escala de tiempo** Muestre la hora actual en milisegundos. Además, se puede escribir directamente un valor de tiempo en este campo para ir a un momento concreto. La precisión depende de la resolución de ajuste establecida en las **Opciones de ajuste**.|  
|![](../designers/media/b1_12.png "B1_12")|**Cabezal de reproducción** Determine el momento en el que se encuentra la animación. El cabezal de reproducción se puede arrastrar a lo largo de la escala de tiempo para obtener una vista previa de la animación.|  
|![](../designers/media/b1_13.png "B1_13")|**Fotogramas clave establecidos en escalas de tiempo** Cambie el valor de una propiedad en un momento específico en el tiempo.|  
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**Cambiar orden de los objetos** Establezca el orden de presentación de los objetos. Haga clic en este botón para organizar los objetos de la vista de estructura por orden Z (de delante hacia atrás) o por orden de marcado (el orden en que aparecen en la vista **XAML**).|  
|![](../designers/media/b1_15.png "B1_15")|**Zoom de escala de tiempo** Establezca la resolución de zoom de la escala de tiempo. El acercamiento le permite modificar una animación con más detalle, mientras que el alejamiento muestra una visión general de lo que ocurre en períodos de tiempo más largos. Si se acerca pero no puede establecer un fotograma clave en la posición temporal que desee, compruebe si la resolución de ajuste es lo bastante alta.|  
|![Llamada 16](../designers/media/b5_label_16.png "b5_label_16")|**Área de composición de la escala de tiempo** Vea la escala de tiempo y mueva los fotogramas clave arrastrándolos o usando sus menús contextuales.|  
  
##  <a name="Properties"></a> Paseo por el panel Propiedades  
 Utilice este panel para ver y modificar las propiedades de un objeto. También puede establecer esas propiedades directamente en la mesa de trabajo. Si lo hace, los cambios de propiedad se reflejarán en el panel **Propiedades**.  
  
 ![Panel Propiedades](../designers/media/blend5_properties_panel.png "Blend5_properties_panel")  
  
 **Categorías** Expanda y contraiga las categorías de propiedades. Haga clic en **Expandir** ![](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png "6375953d-074c-421a-bbb3-6f5055b67b64") y **Contraer** ![Contraer](../designers/media/b5_collapse_button.png "b5_collapse_button") para mostrar u ocultar los detalles de la categoría.  
  
|||  
|-|-|  
|![](../designers/media/b1_1.png "B1_1")|**Nombre y tipo** Vea el icono, el nombre y el tipo del objeto seleccionado.|  
|![](../designers/media/b1_2.png "B1_2")|**Organizar por** Organice las propiedades alfabéticamente por nombre, origen o categoría.|  
|![](../designers/media/b1_3.png "B1_3")|**Propiedades del pincel** Establezca las propiedades visuales de pinceles como los pinceles de relleno, trazo y primer plano.|  
|![](../designers/media/b1_4.png "B1_4")|**Editor de colores** Sirve para los pinceles de color sólido y degradado.|  
|![](../designers/media/b1_5.png "B1_5")|**Selector de color** Seleccione un color.|  
|![](../designers/media/b1_6.png "B1_6")|**Chips de color** Vea los colores inicial, actual y último.|  
|![](../designers/media/b1_7.png "B1_7")|**Cuentagotas** Use el color de cualquier elemento de la pantalla. El **Cuentagotas de color** está disponible cuando se selecciona **Pincel de color sólido**. El **Cuentagotas de degradado** está disponible cuando se selecciona **Pincel de degradado**.|  
|![](../designers/media/b1_8.png "B1_8")|**Propiedades y eventos** Establezca las propiedades o elija los eventos para un elemento seleccionado.|  
|![](../designers/media/b1_9.png "B1_9")|**Cuadro de búsqueda** Permite buscar propiedades. Filtre las propiedades que se muestran al escribir en el cuadro **Búsqueda**.||  
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**Pestañas del Editor de pinceles** Permite seleccionar un editor de pinceles. Puede elegir **Sin pincel**, **Pincel de color sólido**, **Pincel de degradado**, **Pincel de diseño en mosaico** o **Recurso de pincel**.|  
|![](../designers/media/b1_11.png "B1_11")|**Recursos de color** Aplique exactamente el mismo color a diferentes propiedades. La pestaña **Recursos de color** incluye **Recursos locales** y **Recursos del sistema**.|  
|![](../designers/media/b1_12.png "B1_12")|**Espacio de colores RGB** Modifique los colores mediante el ajuste de los valores de los editores de números **R**, **G** o **B** (rojo, verde, azul).|  
|![](../designers/media/b1_13.png "B1_13")|**Canal alfa** Modifique el valor alfa mediante el editor de números situado al lado de **A**.|  
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**Convertir color en recurso** Convierta el color seleccionado en un recurso de color. Los recursos de color están disponibles al hacer clic en la pestaña Recursos de color.|  
|![](../designers/media/b1_15.png "B1_15")|**Valor hexadecimal** Vea el valor hexadecimal del color mostrado.|  
|![Llamada 16](../designers/media/b5_label_16.png "b5_label_16")|**Control deslizante de degradado** Aparece únicamente si se selecciona un pincel de degradado.|  
|![](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png "d50027a1-6824-4ad8-8b4e-558b0756dcf8")|**Mostrar propiedades avanzadas** Vea las categorías de propiedades que se usan con menos frecuencia.|  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Panel Propiedades](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).  
  
## <a name="see-also"></a>Vea también  
 [Insertar controles y modificar su comportamiento](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)   
 [Animar objetos](../designers/animate-objects-in-xaml-designer.md)   
 [Dibujar formas y trazados](../designers/draw-shapes-and-paths.md)   
 [Diseño de XAML en Visual Studio y Blend para Visual Studio](../designers/designing-xaml-in-visual-studio.md)
