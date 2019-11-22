---
title: Edit UML models and diagrams | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.modelingproject
- vs.teamarch.UMLModelExplorer
- vs.teamarch.UMLModelExplorer.rootnode
helpviewer_keywords:
- diagrams - modeling
- UML, copy and paste
- UML, models
- UML model
- UML, element properties
- UML
- UML, diagrams
ms.assetid: 87affd40-8127-4ee9-9d3a-ad977abe2ed6
caps.latest.revision: 86
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 00ac30cc7e9ee3aff0dd64f015a4b4954972c09a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295523"
---
# <a name="edit-uml-models-and-diagrams"></a>Editar modelos y diagramas UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede crear y modificar un modelo UML a través de las vistas proporcionadas por los distintos tipos de diagrama. Al ofrecer perspectivas diferentes en su sistema, estos diagramas ayudan a comprender y analizar diferentes aspectos de su diseño y los requisitos. Visual Studio proporciona plantillas para cinco de los tipos de diagramas de UML utilizados con más frecuencia.

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 En este tema se describen las técnicas para modificar el modelo que son comunes entre los diferentes tipos de diagramas. For more information that is specific to particular types of diagrams, see [Create models for your app](../modeling/create-models-for-your-app.md).

## <a name="in-this-topic"></a>En este tema

- [UML Diagrams are Views of a UML Model](#Views)

- [Creating UML Modeling Diagrams](#Creating)

- [Drawing UML Modeling Diagrams](#Drawing)

- [Editing Shapes and Connectors](#Editing)

- [Undoing Changes to the Model](#Undo)

- [Sharing Elements between Diagrams](#Sharing)

- [Copying Elements and Groups of Related Elements](#Copying)

- [Deleting a Model Element or its Views](#Deleting)

- [Searching text in a diagram](#Searching)

- [Preparing a Diagram for Presentation](#presentation)

- [Extending the UML Designers](#extensions)

## <a name="Views"></a> UML Diagrams are Views of a UML Model
 Puede crear y usar diagramas de UML solo en proyectos de modelado. For more information about how to create diagrams and projects, see [Create UML modeling projects and diagrams](../modeling/create-uml-modeling-projects-and-diagrams.md).

- Un proyecto de modelado contiene un solo modelo UML. Cada diagrama de UML del proyecto es una vista del modelo UML.

- You can see the model in **UML Model Explorer**. On the **Architecture** menu, point to **Windows**, and then click **UML Model Explorer**.

- Cada forma de un diagrama es una vista de un elemento en el modelo. Cuando se coloca una forma nueva en un diagrama, se crea un nuevo elemento en el modelo.

- When you save any diagram, Visual Studio saves the whole model, all its diagrams, and the modeling project file.

## <a name="Creating"></a> Creating UML Modeling Diagrams

1. On the **Architecture** menu in Visual Studio, click **New UML or Layer Diagram**.

2. Seleccione el diagrama y asígnele un nombre.

3. In **Add to modeling project**, select an existing modeling project, or select **Create a new modeling project**.

   > [!NOTE]
   > Los diagramas de modelado solo pueden existir dentro de un proyecto de modelado.

   También puede agregar un diagrama a un proyecto de modelado existente en el Explorador de soluciones. Right-click the modeling project, point to **Add**, and then click **New Item**.

#### <a name="to-create-an-empty-uml-modeling-project"></a>Para crear un proyecto de modelado UML vacío

- On the **File** menu, point to **New**, click **Project**, and in the **New Project** dialog box, double-click **Modeling Projects**.

  For more information about how to manage modeling projects, see [Create UML modeling projects and diagrams](../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="Drawing"></a> Drawing UML Modeling Diagrams
 Un diagrama de modelado muestra una colección de elementos del modelo vinculados mediante relaciones. Cada elemento se muestra como una forma y cada relación se muestra como un conector entre dos formas.

 Hay dos tipos de herramientas: una para los elementos y otra para las relaciones. For example, in the UML class diagram Toolbox, **Class** is an element tool, and **Association** is a relationship tool.

> [!NOTE]
> If you want information that is specific to particular diagram types, see [Create models for your app](../modeling/create-models-for-your-app.md).

#### <a name="to-create-elements-and-relationships-in-a-uml-modeling-diagram"></a>Para crear elementos y relaciones en un diagrama de modelado UML

1. Para crear un elemento del modelo, haga clic en una herramienta de elemento en el cuadro de herramientas y, a continuación, haga clic en el diagrama donde desea que aparezca. Después de haber creado el elemento, ajuste su tamaño y forma arrastrando sus controladores.

    En algunos casos, puede colocar un nuevo elemento dentro de otro elemento. Por ejemplo, en un diagrama de clases UML, puede colocar una clase dentro de un paquete.

   > [!NOTE]
   > If you cannot see the toolbox, click **Toolbox** on the **View** menu.

2. Para crear una relación, haga clic en una herramienta de relación, haga clic en el elemento donde desea que inicie la relación y, a continuación, haga clic en el elemento donde desea que finalice.

    Distintos tipos de relaciones pueden iniciar o finalizar en distintos tipos de elementos. Por ejemplo, en un diagrama de clases UML, una relación de asociación no puede iniciar o finalizar en un elemento de comentario.

   > [!NOTE]
   > Para usar la misma herramienta varias veces, haga doble clic en la herramienta. When you have finished, click the **Pointer** tool.

   En algunos tipos de diagramas, también puede dibujar formas simples. Estas formas no son parte del modelo, pero puede usarlas para llamar la atención sobre los elementos del diagrama o para dividirlo en áreas diferentes.

## <a name="Editing"></a> Editing Shapes and Connectors
 Al cambiar el tamaño o color de una forma o reenrutar un conector, no hay ningún efecto en el modelo subyacente. Sin embargo, cuando al cambiar el nombre de una forma en el diagrama o en el Explorador de modelos UML, se cambia el nombre del elemento correspondiente en el Explorador de modelos UML y en cualquier otro diagrama que presente ese elemento.

> [!NOTE]
> Hay una forma sencilla de crear nuevos elementos de cuadro de herramientas desde los que puede crear grupos de elementos o elementos con su propia elección de propiedades. For more information, see [Define a custom modeling toolbox item](../modeling/define-a-custom-modeling-toolbox-item.md).

 En la siguiente ilustración se muestra cómo cambiar el tamaño de una forma o su nombre.

 ![Adjusting a model element](../modeling/media/uml-drawadjust1.png "UML_DrawAdjust1")

> [!TIP]
> Los comandos integrados no incluyen un comando para alinear las formas perfectamente. However, you can easily create your own alignment command by copying the code in the example in [Display a UML model on diagrams](../modeling/display-a-uml-model-on-diagrams.md).

 En la siguiente ilustración se muestra cómo ajustar la ruta y la posición de un conector o de sus etiquetas.

 ![Adjusting a connector](../modeling/media/uml-drawadjust2.png "UML_DrawAdjust2")

#### <a name="to-move-one-end-of-a-connector-to-another-shape"></a>Para mover un extremo de un conector a otra forma

1. Realice una de las siguientes acciones:

   - Press **CTRL** and move the end.

     \- o -

   - Right-click the connector and then click **Reconnect**.

2. Haga clic en el extremo del conector que desea mover.

3. Haga clic en la forma a la que desea que el conector se mueva.

#### <a name="to-change-color-or-other-properties-of-an-element-relationship-or-diagram"></a>Para cambiar el color u otras propiedades de un elemento, relación o diagrama

- Click the element and set the fields in the **Properties** window.

     If you cannot see the **Properties** window, right-click the element, and then click **Properties.**

#### <a name="to-zoom-in-and-out-on-a-modeling-diagram"></a>Para acercar y alejar en un diagrama de modelado

- Press and hold the **CTRL** key while you rotate the mouse wheel.

     \- o -

- Press and hold **CTRL+SHIFT**, and then click the left or right mouse button.

     \- o -

- On the **Architecture Designers** toolbar, click the plus sign ( **+** ) or minus sign ( **-** ), or choose a zoom level.

## <a name="Searching"></a> Searching in a Diagram
 La función de búsqueda rápida busca elementos en un diagrama. You must set **Look in:** to **Current Document**.

#### <a name="to-search-for-text-in-a-modeling-diagram"></a>Para buscar texto en un diagrama de modelado

1. Press **CTRL+F**.

     \- o -

     On the **Edit** menu, point to **Find and Replace**, and then click **Quick Find**.

    > [!NOTE]
    > In the **Find and Replace** dialog box, you must leave the **Look in** field set to **Current Document**. No se admiten las demás opciones.

2. Type the text that you want to find, and then click **Find Next**.

    > [!NOTE]
    > Si el texto que desea buscar está dentro de una forma contraída, la forma aparecerá resaltada. Expand the shape, and then click **Find Next** again.

## <a name="Undo"></a> Undoing Changes to the Model
 You can undo and redo changes that you have made to the model and diagrams by using the **Undo** and **Redo** commands on the **Edit** menu.

 **Each modeling project has a single stack of changes.** Todos los cambios que realiza en el modelo y los diagramas se mantienen en esta pila. La pila también incluye cambios de foco de un diagrama a otro. El comando Deshacer revierte los cambios de esta pila.

 Por ejemplo, supongamos que realiza las siguientes operaciones: realizar un cambio en Diagrama1, cambiar el foco en Diagrama 2, cambiar Diagrama2. Al deshacer los cambios, la primera vez se revertirá el último cambio, la siguiente vez se volverá a cambiar el foco a Diagrama 1 y la tercera vez se revertirá el cambio en Diagrama1.

 **Closing a diagram truncates the stack of changes.** Si cierra un diagrama, no podrá deshacer los cambios que realizó en dicho diagrama y no podrá deshacer los cambios anteriores en el modelo o cualquiera de sus diagramas.

 **You cannot undo while you are editing a property.** Mientras se edita una propiedad en la ventana Propiedades, o en una etiqueta de un diagrama, solo se pueden deshacer los cambios realizados en esa propiedad. Complete el cambio en la propiedad presionando ENTRAR o cancélelo presionando la tecla ESC. A continuación, podrá deshacer los cambios en el modelo y los diagramas.

 **Closing a diagram without saving might not have the effect you expect.** Si realiza algunos cambios y luego cierra un diagrama sin guardarlo, todavía se conservarán los cambios en el modelo. Se recomienda cerrar todo el modelo si desea hacerlo sin guardarlo.

## <a name="Sharing"></a> Sharing Elements between Diagrams
 Puede hacer que una instancia específica de un elemento de modelo aparezca más de una vez en los diagramas. Esto se aplica a las clases, interfaces, componentes, casos de uso y actores.

 Esto resulta útil si desea mostrar distintos grupos de relaciones en distintos diagramas. Por ejemplo, en un diagrama, puede mostrar las asociaciones entre las clases de dirección y cliente. En otro diagrama puede mostrar de nuevo la clase de dirección con su asociación al área postal.

 Para cambiar las propiedades de un elemento de modelo, como su nombre, seleccione cualquiera de sus vistas en un diagrama o selecciónelo en el Explorador de modelos UML.

 Cada tipo de diagrama solo puede mostrar algunos tipos de elemento de modelo. Por ejemplo, no puede mostrar un caso de uso en un diagrama de componentes. Por lo tanto, los procedimientos siguientes funcionarán exclusivamente en algunas combinaciones de elementos de modelo y diagramas.

#### <a name="to-add-a-new-view-of-a-model-element-by-using-uml-model-explorer"></a>Para agregar una nueva vista de un elemento de modelo mediante el Explorador de modelos UML

1. To open **UML Model Explorer**, on the **Architecture** menu, point to **Windows**, and then click **UML Model Explorer**.

2. Drag the model element from **UML Model Explorer** to a compatible diagram in the same project.

     Aparece una forma que proporciona una vista del elemento del modelo, además de las vistas en otros diagramas o en el mismo diagrama.

    > [!NOTE]
    > El efecto es diferente cuando arrastra una clase o un componente a un diagrama de secuencia. En ese caso, se crea una nueva línea de vida cuyo tipo sea esa clase o componente. For more information, see [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

#### <a name="to-add-a-new-view-of-a-model-element-by-using-paste-reference"></a>Para agregar una nueva vista de un elemento de modelo mediante Pegar referencia

1. Right-click an existing element, and then click **Copy**.

    - Puede copiar varios elementos al mismo tiempo. Hold down the CTRL key while you click each element, right-click one of them, and then click **Copy**.

2. Right-click an empty part of a compatible diagram, and then click **Paste Reference**.

     Aparecerá otra vista del mismo elemento.

    > [!NOTE]
    > This differs from the **Paste** command, which creates a new element in the model. For more information, see [Copying Elements and Groups of Related Elements](#Copying).

> [!NOTE]
> Si agrega a un diagrama vistas de dos elementos de modelo que ya están conectados por una relación, también aparecerá una vista de la relación en el diagrama. Para eliminar esta vista, simplemente quite uno de los elementos del diagrama o elimine la relación del modelo.

## <a name="Copying"></a> Copying Elements and Groups of Related Elements
 Puede copiar y pegar elementos del modelo, y puede copiar y pegar grupos de elementos junto con las relaciones entre ellos.

> [!NOTE]
> The **Paste** and **Paste Reference** commands have different effects. **Paste** creates new elements whose properties are like those of the copied elements. **Paste Reference** creates new views of the same elements.

#### <a name="to-copy-elements-and-their-relationships"></a>Para copiar elementos y sus relaciones

1. En el diagrama con los elementos que desea copiar, seleccione uno o varios elementos.

    > [!NOTE]
    > No puede copiar relaciones, excepto como parte de un grupo de elementos.

2. On the **Edit** menu, click **Copy**.

3. Si desea copiar los elementos en otro diagrama, cree el nuevo diagrama o abra el diagrama existente.

4. On the **Edit** menu, click **Paste**.

    - Aparecerán las copias de los elementos, junto con las copias de las relaciones que se vinculan entre ellos.

    - Cada nuevo elemento tendrá un nombre generado automáticamente.

5. Ajuste las posiciones, los nombres y otras propiedades de los nuevos elementos y relaciones.

> [!NOTE]
> No puede copiar un elemento de modelo de un modelo a otro, por ejemplo, si tiene dos modelos en la misma solución. Pero puede copiar elementos de un diagrama a otro.

#### <a name="to-copy-an-entire-diagram"></a>Para copiar un diagrama completo

1. Cree un nuevo diagrama.

2. Seleccione todos los elementos en un diagrama existente, cópielos y péguelos en el nuevo.

   No se puede replicar un diagrama copiando y pegando en el Explorador de soluciones.

## <a name="Deleting"></a> Deleting a Model Element or its Views
 Algunos tipos de elementos, especialmente los clasificadores, se pueden quitar de un diagrama sin eliminarlos del modelo. Los clasificadores son los elementos principales que se muestran en los diagramas de clases, diagramas de componentes y diagramas de casos de uso. Pueden aparecer en más de un diagrama. For these types of elements, there are two separate commands: **Remove from Diagram** and **Delete from Model**.

 Por el contrario, cuando se elimina una relación de un diagrama, siempre se elimina del modelo.

> [!NOTE]
> Ciertos tipos de elementos en un diagrama UML tienen etiquetas. Al seleccionar estos elementos dibujando un rectángulo en torno a ellos, es posible seleccionar las etiquetas, pero no los elementos que poseen esas etiquetas. No es posible eliminar un subconjunto de los elementos seleccionados de esta manera. To select a subset of these elements, press and hold the **CTRL** key while you click each element.

#### <a name="to-remove-a-classifiers-view-from-a-diagram"></a>Para quitar una vista de clasificador de un diagrama

- Right-click the element on the diagram, and then click **Remove from Diagram**.

  \- o -

- Click the element on the diagram and then press the **DELETE** key.

  - Esta vista del elemento desaparece. However, the element remains in the model, and you can still find it in **UML Model Explorer**. También permanecen las demás vistas del mismo elemento.

  - Todos los conectores que terminan en esta forma se quitan del diagrama, pero la relación que representa se mantiene en el modelo. You can see the relationship in **UML Model Explorer** under **Relationships**, under each element that it connects.

#### <a name="to-delete-an-element-from-the-model"></a>Para eliminar un elemento del modelo

- Right-click the element either in **UML Model Explorer** or on a diagram, and then click **Delete from Model**.

  - El elemento se elimina de todos los diagramas en los que aparece.

  - Todas las relaciones que terminan en este elemento también se eliminan del modelo.

#### <a name="to-delete-a-relationship-from-the-model"></a>Para eliminar una relación del modelo

- Right-click the relationship on a diagram or in **UML Model Explorer**, and then click **Delete from Model**.

    > [!CAUTION]
    > No se puede quitar una relación de un diagrama sin quitarla del modelo.

     La relación se elimina del modelo y se elimina de todos los diagramas en los que aparece.

## <a name="presentation"></a> Preparing a Diagram for Presentation
 Las siguientes características le ayudarán a llamar la atención sobre partes específicas del diagrama, agregar explicaciones o dividir un diagrama en distintas áreas de interés.

- Puede copiar cualquier parte de un diagrama en Word, PowerPoint u otro documento. Select the shapes and connectors you want, right-click and then click **Copy**.

- Se puede cambiar el color de cualquier forma o conector. Select one or more shapes and change the **Color** property. Si no ve la ventana **Propiedades**, presione **F4**.

- On diagrams of some kinds, you can draw lines, rectangles and ellipses from the **Simple Shapes** section of the Toolbox. Estas formas no forman parte del modelo UML.

- To label an area, you can drag a Comment from the Toolbox and then set its **Transparent** property to **True**. Al igual que las formas simples, los comentarios no forman parte del modelo UML y no aparecen en el Explorador de modelos UML.

- Para agregar notas y explicaciones a los elementos del modelo, puede crear comentarios y, a continuación, vincularlos a los elementos.

### <a name="to-export-a-diagram-as-an-image"></a>Para exportar un diagrama como imagen
 For more information, see [Export diagrams as images](../modeling/export-diagrams-as-images.md).

## <a name="extensions"></a> Extending the UML Designers
 Puede agregar nuevas funcionalidades a las herramientas de UML y adaptar la notación del diagrama a sus propias necesidades. For more information, see [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md).

## <a name="see-also"></a>Vea también
 [Create UML modeling projects and diagrams](../modeling/create-uml-modeling-projects-and-diagrams.md) [Analyzing and Modeling Architecture](../modeling/analyze-and-model-your-architecture.md) [Create models for your app](../modeling/create-models-for-your-app.md)
