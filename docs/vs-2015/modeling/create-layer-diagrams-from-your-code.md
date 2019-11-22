---
title: Create layer diagrams from your code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e6cd77e785adb59fc8b2cf3b28724ed0efe1ae3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300277"
---
# <a name="create-layer-diagrams-from-your-code"></a>Crear diagramas de capas a partir del código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To visualize your software system's high-level, logical architecture, create a *layer diagram* in Visual Studio. Para asegurarse de que el código mantiene la coherencia con este diseño, valide el código con un diagrama de capas. Se pueden crear diagramas de capas para proyectos de Visual C# .NET y Visual Basic .NET. To see which versions of Visual Studio support this feature, see [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

 ![Create a layer diagram](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")

 A layer diagram lets you organize Visual Studio solution items into logical, abstract groups called *layers*. Las capas se pueden usar para describir las tareas principales que realizan estos artefactos o los componentes principales del sistema. Cada capa puede contener otras capas que describen tareas más detalladas. You can also specify the intended or existing *dependencies* between layers. Estas dependencias, que se representan como flechas, muestran qué capas pueden usar o usan actualmente la funcionalidad representada por otras capas. Para mantener el control de la arquitectura del código, muestre las dependencias previstas en el diagrama y, a continuación, valide el código con el diagrama.

## <a name="CreateDiagram"></a> Create a layer diagram
 Antes de poder crear un diagrama de capas, asegúrese de que la solución tenga un proyecto de modelado. See [Create UML modeling projects and diagrams](../modeling/create-uml-modeling-projects-and-diagrams.md).

> [!IMPORTANT]
> No agregue, arrastre ni copie un diagrama de capas de un proyecto de modelado a otro, ni a otro lugar de la solución. Esto conserva las referencias del diagrama original, aunque se cambie el diagrama. Esto también impide que la validación de capas se haga correctamente y es posible que cause otros problemas, como la pérdida de elementos u otros errores al intentar abrir el diagrama.
>
> En su lugar, agregue un nuevo diagrama de capas al proyecto de modelado. Copie los elementos del diagrama de origen en el nuevo diagrama. Guarde el proyecto de modelado y el nuevo diagrama de capas.

#### <a name="to-add-a-new-layer-diagram-to-a-modeling-project"></a>Para agregar un nuevo diagrama de capas a un proyecto de modelado

1. On the **Architecture** menu, choose **New UML or Layer Diagram**.

2. Under **Templates**, choose **Layer Diagram**.

3. Especifique un nombre para el diagrama.

4. In **Add to Modeling Project**, browse to and select an existing modeling project in your solution.

     o bien

     Choose **Create a new modeling project** to add a new modeling project to the solution.

    > [!NOTE]
    > Los diagramas de capas solo pueden existir dentro de un proyecto de modelado. Sin embargo, puede vincularlos a elementos en cualquier parte de la solución.

5. Asegúrese de guardar tanto el proyecto de modelado como el diagrama de capas.

## <a name="CreateLayers"></a> Create layers from artifacts
 Puede crear capas a partir de elementos de una solución de Visual Studio, como proyectos, archivos de código, espacios de nombres, clases y métodos. Esto crea automáticamente vínculos entre las capas y los elementos, que se incluyen en el proceso de validación de capas.

 También puede vincular capas a los elementos que no admiten validación, como documentos de Word o presentaciones de PowerPoint, para poder asociar una capa con especificaciones o planes. También puede vincular capas a archivos en proyectos que se comparten entre varias aplicaciones, pero el proceso de validación no incluirá esas capas, que aparecen con nombres genéricos como “Layer1" y “Layer2".

 To see if a linked item supports validation, open **Layer Explorer** and examine the **Supports Validation** property of the item. See [Managing links to artifacts](#Managing).

|**En**|**Follow these steps**|
|------------|----------------------------|
|Crear una capa para un único artefacto|<ol><li>Arrastre el elemento hasta el diagrama de capas desde estos orígenes:<br /><br /> <ul><li>**Explorador de soluciones**<br /><br />         Por ejemplo, puede arrastrar archivos o proyectos.</li><li>Mapas de código<br /><br />         See [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md) and [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Class View** or **Object Browser**</li></ul><br />     Aparecerá una capa en el diagrama que estará vinculada al artefacto.</li><li>Cambie el nombre de la capa para que refleje las responsabilidades del código asociado u otros artefactos.</li></ol> **Important:**  Dragging binary files to the layer diagram does not automatically add their references to modeling project. Debe agregar manualmente los archivos binarios que desee validar al proyecto de modelado. **To add binary files to the modeling project** <ol><li>In **Solution Explorer**, open the shortcut menu for the modeling project, and then choose **Add Existing Item**.</li><li>In the **Add Existing Item** dialog box, browse to the binary files, select them, and then choose **OK**.     Los archivos binarios aparecen en el proyecto de modelado.</li><li>In **Solution Explorer**, choose a binary file that you added, and then press **F4** to open the **Properties** window.</li><li>On each binary file, set the **Build Action** property to **Validate**.</li></ol>|
|Crear una única capa para todos los artefactos seleccionados|Arrastre todos los artefactos hasta el diagrama de capas al mismo tiempo.<br /><br /> Aparecerá una capa en el diagrama que estará vinculada a todos los artefactos.|
|Crear una capa para cada artefacto seleccionado|Press and hold the **SHIFT** key while you drag all of the artifacts to the layer diagram at the same time. **Note:**  If you use the **SHIFT** key to select a range of items, release the key after you select the artifacts. Cuando arrastre los artefactos al diagrama, vuelva a mantener la tecla presionada. <br /><br /> Aparecerá una capa para cada artefacto y cada capa estará vinculada a cada uno de los artefactos.|
|Agregar un artefacto a una capa|Arrastre el artefacto hasta la capa.|
|Crear una nueva capa que no tenga vínculos|In the **Toolbox**, expand the **Layer Diagram** section, and then drag a **Layer** to the layer diagram.<br /><br /> Para agregar varias capas, haga doble clic en la herramienta. When you are finished, choose the **Pointer** tool or press the **ESC** key.<br /><br /> O bien<br /><br /> Open the shortcut menu for the layer diagram, choose **Add**, and then choose **Layer**.|
|Crear capas anidadas|Arrastre una capa existente a otro nivel.<br /><br /> O bien<br /><br /> Open the shortcut menu for a layer, choose **Add**, and then choose **Layer**.|
|Crear una nueva capa que contenga dos o más capas existentes|Select the layers, open the shortcut menu for your selection, and then choose **Group**.|
|Cambiar el color de una capa|Set its **Color** property to the color that you want.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a los espacios de nombres especificados|Type the namespaces in the layer's **Forbidden Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Especificar qué artefactos asociados a una capa no pueden depender de los espacios de nombres especificados|Type the namespaces in the layer's **Forbidden Namespace Dependencies** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a uno de los espacios de nombres especificados|Type the namespace in the layer's **Required Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|

 El número de una capa indica el número de artefactos vinculados a ella. Sin embargo, cuando lea este número, recuerde lo siguiente:

- Si una capa se vincula a un artefacto que contiene otros artefactos, pero no se vincula directamente a estos otros artefactos, el número incluye únicamente el artefacto vinculado. Sin embargo, los demás artefactos se incluyen para el análisis durante la validación de capas.

     Por ejemplo, si una capa está vinculada a un solo espacio de nombres, el número de artefactos vinculados es 1, aunque el espacio de nombres contenga clases. Si la capa tiene también vínculos a cada clase del espacio de nombres, el número incluirá las clases vinculadas.

- Si una capa contiene otras que están vinculadas a artefactos, la capa contenedora también está vinculada a esos artefactos, incluso aunque el número de la capa contenedora no los incluya.

## <a name="Managing"></a> Manage links between layers and artifacts

1. On the layer diagram, open the shortcut menu for the layer, and then choose **View Links**.

     **Layer Explorer** shows the artifact links for the selected layer.

2. Use las tareas siguientes para administrar estos vínculos:

|**En**|**In Layer Explorer**|
|------------|---------------------------|
|Eliminar el vínculo entre la capa y un artefacto|Open the shortcut menu for the artifact link, and then choose **Delete**.|
|Mover el vínculo de una capa a otra|Arrastre el vínculo del artefacto a una capa del diagrama.<br /><br /> O bien<br /><br /> 1.  Open the shortcut menu for the artifact link, and then choose **Cut**.<br />2.  On the layer diagram, open the shortcut menu for the layer, and then choose **Paste**.|
|Copiar el vínculo de una capa a otra|1.  Open the shortcut menu for the artifact link, and then choose **Copy**.<br />2.  On the layer diagram, open the shortcut menu for the layer, and then choose **Paste**.|
|Crear una nueva capa a partir del vínculo de un artefacto existente|Arrastre el vínculo del artefacto a un espacio en blanco del diagrama.|
|Compruebe que el artefacto vinculado admite la validación con el diagrama de capas.|Look at the **Supports Validation** column for the artifact link.|

## <a name="Discovering"></a> Reverse-engineer existing dependencies
 Una dependencia existe cuando un artefacto que está asociado a una capa tiene una referencia a un artefacto que está asociado a otra capa. Por ejemplo, una clase de una capa declara una variable que tiene una clase en otra capa. Puede realizar ingeniería inversa de las dependencias existentes en los artefactos vinculados a las capas del diagrama.

> [!NOTE]
> No se puede realizar ingeniería inversa en las dependencias de ciertos tipos de artefactos. Por ejemplo, no se va a realizar ingeniería inversa en ninguna dependencia que tenga como origen o destino una capa vinculada a un archivo de texto. To see which artifacts have dependencies that you can reverse-engineer, open the shortcut menu for one or multiple layers, and then choose **View Links**. In **Layer Explorer**, examine the **Supports Validation** column. Dependencies will not be reverse-engineered for artifacts for which this column shows **False**.

- Select one or multiple layers, open the shortcut menu for a selected layer, and then choose **Generate Dependencies**.

  Normalmente, verá algunas dependencias que no deberían existir. Puede editar estas dependencias para alinearlas con el diseño buscado.

## <a name="EditDependencies"></a> Edit layers and dependencies to show the intended design
 Para describir los cambios que piensa realizar en el sistema o la arquitectura deseada, edite el diagrama de capas:

|**En**|**Perform these steps**|
|------------|-----------------------------|
|Cambiar o restringir la dirección de una dependencia|Set its **Direction** property.|
|Crear nuevas dependencias|Use the **Dependency** and **Bidirectional Dependency** tools.<br /><br /> Para dibujar varias dependencias, haga doble clic en la herramienta. When you are finished, choose the **Pointer** tool or press the **ESC** key.|
|Especificar qué artefactos asociados a una capa no pueden depender de los espacios de nombres especificados|Type the namespaces in the layer's **Forbidden Namespace Dependencies** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a los espacios de nombres especificados|Type the namespaces in the layer's **Forbidden Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a uno de los espacios de nombres especificados|Type the namespace in the layer's **Required Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|

## <a name="EditLayout"></a> Change how elements appear on the diagram
 Puede cambiar el tamaño, la forma, el color y la posición de las capas o el color de las dependencias mediante la edición de sus propiedades.

## <a name="Codemaps"></a> Discover patterns and dependencies on a code map
 While creating layer diagrams, you might also create **code maps**. Estos diagramas pueden ayudarle a detectar patrones y dependencias mientras explora el código. Use el Explorador de soluciones, la Vista de clases o el Examinador de objetos para explorar los ensamblados, los espacios de nombres y las clases, que a menudo corresponden a las capas existentes. Para obtener más información sobre mapas de código, vea:

- [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)

- [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)

- [Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>Vea también
 [Channel 9 Video: Design and validate your architecture using layer diagrams](https://go.microsoft.com/fwlink/?LinkID=252073) [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md) [Layer Diagrams: Guidelines](../modeling/layer-diagrams-guidelines.md) [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md) [Visualize code](../modeling/visualize-code.md)