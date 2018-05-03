---
title: Insertar controles y modificar su comportamiento en el Diseñador XAML
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 0b2572194d2eb154822355f8dffef506fb1c3ffb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Insertar controles y modificar su comportamiento en el Diseñador XAML

Los controles permiten a los usuarios interactuar con la aplicación. Puede utilizarlos para recopilar información y realizar acciones como animar un objeto o realizar una consulta en un origen de datos.

## <a name="add-controls-to-the-artboard"></a>Agregar controles a la mesa de trabajo

Puede arrastrar controles desde el panel **Activos** a la **mesa de trabajo**y, a continuación, modificarlos en la ventana **Propiedades** .

![Controles de pestañas de recursos de Blend](../designers/media/blend_assetsflipview_xaml.png)

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Crear un control a partir de una imagen, una forma o un trazado

Puede convertir cualquier objeto en un control.

![Cuadro de diálogo Convertir en control de Blend](../designers/media/blend_makeintocontrol_xaml.png)

Imagine, por ejemplo, la imagen de una televisión en el centro de una página. A partir de imágenes pequeñas podría crear controles que tuviesen el aspecto de botones de televisión y en los que los usuarios podrían hacer clic para cambiar de canal.

Esto es posible porque los botones ahora son controles que permiten responder a las interacciones del usuario; en este caso, al hacer clic en un botón.

Para crear un control, seleccione un objeto. A continuación, en el menú **Herramientas** , haga clic en **Crear control**.

## <a name="make-controls-do-things"></a>Acciones de los controles

Los controles pueden realizar acciones cuando los usuarios interactúan con ellos. Por ejemplo, pueden iniciar una animación, actualizar un origen de datos o reproducir un vídeo.

Utilice *desencadenadores*, *comportamientos*y *eventos* para que los controles realicen accines.

### <a name="triggers"></a>desencadenadores

Un *desencadenador* cambia una propiedad o realiza una tarea en respuesta a un evento o a un cambio en otra propiedad. Por ejemplo, puede cambiar el color de un botón cuando los usuarios se mantenga el ratón sobre él.

![Panel "Desencadenadores"](../designers/media/custom_button_blend_propertytriggerinfo.png)

### <a name="behaviors"></a>comportamientos

Un *comportamiento* es un paquete de código reutilizable. Es un poco más completo que cambiar las propiedades y puede realizar acciones como consultas a un servicio de datos. Blend trae incorporada una pequeña colección de comportamientos, pero se pueden agregar más. Arrastre un comportamiento a cualquier objeto de la mesa de trabajo y después personalícelo mediante la configuración de sus propiedades.

![FluidMoveBehavior en el panel Propiedades](../designers/media/b4_fluidmovebehaviorproperties_sample.png)

**Vea un vídeo:** ![Icono de reproducción](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Consejos de Blend: introducción al uso de comportamientos, parte 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).

### <a name="events"></a>Eventos

Para una flexibilidad óptima, controle un *evento*. Tendrá que escribir código.