---
title: 'Layer Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 2903bec7-a93b-46a6-aac6-994ac4f3f1a7
caps.latest.revision: 57
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 51cb71d4bc2f66377b677d5be292c4eafa1dbd18
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299463"
---
# <a name="layer-diagrams-guidelines"></a>Diagrama de capas: Instrucciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Describe your app's architecture at a high level by creating *layer diagrams* in Visual Studio. Para asegurarse de que el código mantiene la coherencia con este diseño, valide el código con un diagrama de capas. También puede incluir la validación de capas en el proceso de compilación. See [Channel 9 Video: Design and validate your architecture using layer diagrams](https://go.microsoft.com/fwlink/?LinkID=252073).

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="what-is-a-layer-diagram"></a>¿Qué es un diagrama de capas?
 Al igual que en un diagrama de arquitectura tradicional, en un diagrama de capas se identifican los componentes primarios o las unidades funcionales del diseño y sus interdependencias. Each node on the diagram, called a *layer*, represents a logical group of namespaces, projects, or other artifacts. Puede dibujar las dependencias que debería haber en el diseño. A diferencia de un diagrama de arquitectura tradicional, puede comprobar que las dependencias reales del código fuente se ajustan a las dependencias especificadas que se pretenden. Al incluir la validación en el proceso de compilación normal de [!INCLUDE[esprtfs](../includes/esprtfs-md.md)], tiene la garantía de que el código de programa seguirá ajustándose a la arquitectura del sistema cuando se realicen cambios. See [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md).

## <a name="Update"></a> How to design or update your app with layer diagrams
 Los siguientes pasos proporcionan información general sobre cómo utilizar los diagramas de capas dentro del proceso de desarrollo. Las secciones posteriores de este tema describen cada paso con más detalle. Si está desarrollando un nuevo diseño, omita los pasos en los que se hace referencia al código existente.

> [!NOTE]
> Estos pasos aparecen en un orden aproximado. Es probable que desee superponer las tareas, reorganizarlas para que se adapten a su situación particular y revisarlas al inicio de cada iteración del proyecto.

1. [Create a layer diagram](#Create) for the whole application, or for a layer within it.

2. [Define layers to represent primary functional areas or components](#CreateLayers) of your application. Denomine estos niveles según su función, por ejemplo, "Presentación" o "Servicios". If you have a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] solution, you can associate each layer with a collection of *artifacts*, such as projects, namespaces, files, and so on.

3. [Discover the existing dependencies](#Generate) between layers.

4. [Edit the layers and dependencies](#EditArchitecture) to show the updated design that you want the code to reflect.

5. [Design new areas of your application](#NewAreas) by creating layers to represent the principal architectural blocks or components and defining dependencies to show how each layer uses the others.

6. [Edit the layout and appearance of the diagram](#EditLayout) to help you discuss it with colleagues.

7. [Validate the code against the layer diagram](#Validate) to highlight the conflicts between the code and the architecture you require.

8. [Update the code to conform to your new architecture](#UpdateCode). Desarrolle y refactorice el código en iteraciones hasta que la validación no muestre ningún conflicto.

9. [Include layer validation in the build process](#BuildValidation) to ensure that the code continues to adhere to your design.

## <a name="Create"></a> Create a layer diagram
 Los diagramas de capas deben crearse dentro de un proyecto de modelado. Se puede agregar un nuevo diagrama de capas a un proyecto de modelado ya existente, crear un nuevo proyecto de modelado para el diagrama de capas o bien copiar un diagrama de capas ya existente en el mismo proyecto de modelado.

> [!IMPORTANT]
> No agregue, arrastre ni copie un diagrama de capas de un proyecto de modelado a otro, ni a otra ubicación de la solución. Un diagrama de capas que se copia de esta manera tendrá las mismas referencias que el diagrama original, incluso si se modifica. Esto impide que la validación de capas se haga correctamente y es posible que cause otros problemas, como la pérdida de elementos u otros errores al intentar abrir el diagrama.

 See [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="CreateLayers"></a> Define layers to represent functional areas or components
 Layers represent logical groups of *artifacts*, such as projects, code files, namespaces, classes, and methods. Se pueden crear capas a partir de artefactos de proyectos de Visual C# .NET y Visual Basic .NET, o bien se pueden adjuntar especificaciones o planes a una capa vinculando documentos, como archivos de Word o presentaciones de PowerPoint. Cada capa aparece como un rectángulo en el diagrama y muestra el número de artefactos vinculados a ella. Una capa puede contener capas anidadas que describan tareas más específicas.

 Como regla general, denomine las capas según su función, por ejemplo, "Presentación" o "Servicios." Si los artefactos tienen una estrecha interdependencia, colóquelos en la misma capa. Si los artefactos se pueden actualizar de forma independiente o usar en aplicaciones diferentes, sitúelos en capas distintas. To learn about layering patterns, visit the Patterns & Practices site at [http://go.microsoft.com/fwlink/?LinkId=145794](https://go.microsoft.com/fwlink/?LinkId=145794).

> [!TIP]
> Existen ciertos tipos de artefactos que se pueden vincular a capas, pero que no admiten la validación con el diagrama de capas. To see whether the artifact supports validation, open **Layer Explorer** to examine the **Supports Validation** property of the artifact link. See [Discover existing dependencies between layers](#Generate).

 Al actualizar una aplicación desconocida, también puede crear mapas de código. Estos diagramas pueden ayudarle a detectar patrones y dependencias mientras explora el código. También puede usar el Explorador de soluciones para examinar los espacios de nombres y las clases, que suelen corresponderse con las capas existentes. Asigne estos artefactos de código a las capas arrastrándolos desde el Explorador de soluciones hasta los diagramas de capas. Después, puede usar diagramas de capas, que le ayudarán a actualizar el código y mantener la coherencia con el diseño.

 Vea:

- [Crear diagramas de capas a partir del código](../modeling/create-layer-diagrams-from-your-code.md)

- [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)

- [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)

## <a name="Generate"></a> Discover existing dependencies between layers
 Una dependencia existe cuando un artefacto que está asociado a una capa tiene una referencia a un artefacto que está asociado a otra capa. Por ejemplo, una clase de una capa declara una variable que tiene una clase en otra capa. Puede detectar las dependencias existentes aplicándoles técnicas de ingeniería inversa.

> [!NOTE]
> No se puede realizar ingeniería inversa en las dependencias de ciertos tipos de artefactos. Por ejemplo, no se va a realizar ingeniería inversa en ninguna dependencia que tenga como origen o destino una capa vinculada a un archivo de texto. To see which artifacts have dependencies that you can reverse-engineer, right-click one or multiple layers, and then click **View Links**. In **Layer Explorer**, examine the **Supports Validation** column. Dependencies will not be reverse-engineered for artifacts for which this column shows **False**.

#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Para realizar ingeniería inversa de las dependencias existentes entre capas

- Select one layer or multiple layers, right-click a selected layer, and then click **Generate Dependencies**.

  Normalmente, verá algunas dependencias que no deberían existir. Puede editar estas dependencias para alinearlas con el diseño buscado.

## <a name="EditArchitecture"></a> Edit layers and dependencies to show the intended design
 Para describir los cambios que piensa realizar en el sistema o la arquitectura deseada, use los pasos siguientes para editar el diagrama de capas. También podría realizar algunos cambios de refactorización para mejorar la estructura del código antes de extenderlo. See [Improving the structure of the code](#Improving).

|**En**|**Perform these steps**|
|------------|-----------------------------|
|Eliminar una dependencia que no debería existir|Click the dependency, and then press **DELETE**.|
|Cambiar o restringir la dirección de una dependencia|Set its **Direction** property.|
|Crear nuevas dependencias|Use the **Dependency** and **Bidirectional Dependency** tools.<br /><br /> Para dibujar varias dependencias, haga doble clic en la herramienta. When you are finished, click the **Pointer** tool or press the **ESC** key.|
|Especificar qué artefactos asociados a una capa no pueden depender de los espacios de nombres especificados|Type the namespaces in the layer's **Forbidden Namespace Dependencies** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a los espacios de nombres especificados|Type the namespaces in the layer's **Forbidden Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a uno de los espacios de nombres especificados|Type the namespace in the layer's **Required Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|

### <a name="Improving"></a> Improving the structure of the code
 Los cambios de refactorización son mejoras que no afectan al comportamiento de la aplicación, pero que facilitan los cambios y las ampliaciones del código en el futuro. Un código bien estructurado tiene un diseño que resulta fácil abstraer en un diagrama de capas.

 Por ejemplo, si crea una capa para cada espacio de nombres del código y, a continuación, aplica técnicas de ingeniería inversa a las dependencias, debe haber un conjunto mínimo de dependencias unidireccionales entre las capas. Si crea un diagrama más detallado usando clases o métodos como capas, el resultado debería tener también las mismas características.

 De lo contrario, el código resultará más difícil de modificar a lo largo de su vida útil y será menos apropiado para llevar a cabo la validación con diagramas de capas.

## <a name="NewAreas"></a> Design new areas of your application
 Cuando comience el desarrollo de un nuevo proyecto, o una nueva área de un nuevo proyecto, puede dibujar capas y dependencias que le ayuden a identificar los componentes primarios antes de empezar a desarrollar el código.

- **Show identifiable architectural patterns** in your layer diagrams, if possible. Por ejemplo, un diagrama de capas en el que se describa una aplicación de escritorio puede incluir capas como Presentación, Lógica del dominio y Almacén de datos. Un diagrama de capas que abarque una única característica de una aplicación puede tener las capas Modelo, Ver y Controlador. For more information about such patterns, see [Patterns & Practices: Application Architecture](https://go.microsoft.com/fwlink/?LinkId=145794).

     Si genera a menudo modelos similares, cree una herramienta personalizada. See [Define a custom modeling toolbox item](../modeling/define-a-custom-modeling-toolbox-item.md).

- **Create a code artifact for each layer** such as a namespace, class, or component. De este modo, le resultará más fácil hacer un seguimiento del código y vincular los artefactos de código a las capas. Tan pronto como cree cada uno de los artefactos, vincúlelo a la capa apropiada.

- **You do not have to link most classes and other artifacts to layers** because they fall within larger artifacts such as namespaces that you have already linked to layers.

- **Create a new diagram for a new feature**. Normalmente, habrá uno o varios diagramas de capas en los que se describa toda la aplicación. Si está diseñando una nueva característica de la aplicación, no agregue ni cambie los diagramas existentes. En su lugar, cree un diagrama propio en el que refleje los nuevos elementos del código. Las capas del nuevo diagrama pueden incluir las capas de la presentación, la lógica del dominio y la base de datos de la nueva característica.

     Cuando compile la aplicación, el código se validará con el diagrama general y con el diagrama más detallado de la característica.

## <a name="EditLayout"></a> Edit the layout for presentation and discussion
 Para que le resulte más fácil identificar las capas y dependencias o para analizarlas con los miembros del equipo, edite el aspecto y el diseño del diagrama de los siguientes modos:

- Cambiar el tamaño, la forma y la posición de las capas.

- Cambiar el color de las capas y las dependencias.

  - Select one or more layers or dependencies, right-click, and then click **Properties**. In the **Properties** window, edit the **Color** property.

## <a name="Validate"></a> Validate the code against the diagram
 Una vez editado el diagrama, puede validarlo con el código manualmente en cualquier momento o automáticamente cada vez que se ejecute una compilación local o [!INCLUDE[esprbuild](../includes/esprbuild-md.md)].

 Vea:

- [Validar código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md)

- [Include Layer Validation in the Build Process](#BuildValidation)

## <a name="UpdateCode"></a> Update the code to conform to the new architecture
 Normalmente, los errores aparecerán la primera vez que valide el código contra un diagrama de capas actualizado. Estos errores pueden tener varias causas:

- Un artefacto se ha asignado a la capa equivocada. En este caso, mueva el artefacto.

- Un artefacto, como por ejemplo una clase, usa otra clase de forma que hay conflictos con su arquitectura. En este caso, tiene que refactorizar el código para quitar la dependencia.

  Para resolver estos errores, actualice el código hasta no aparezcan más errores durante la validación. Normalmente, este es un proceso iterativo. For more information about these errors, see [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> A medida que desarrolla o refactoriza el código, es posible que tenga nuevos artefactos que deba vincular al diagrama de capas. Sin embargo, esto podría no ser necesario, por ejemplo, si tiene capas que representan espacios de nombres existentes, y el nuevo código solo agrega más material a estos espacios de nombres.

 Durante el proceso de desarrollo, puede que desee suprimir algunos de los conflictos notificados durante la validación. Por ejemplo, es posible que desee suprimir errores de los que ya se ha ocupado o que no son pertinentes para su escenario concreto. Cuando se suprime un error, conviene registrar un elemento de trabajo en [!INCLUDE[esprfound](../includes/esprfound-md.md)]. To perform this task, see [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md).

## <a name="BuildValidation"></a> Include layer validation in the build process
 Para asegurarse de que los futuros cambios que se hagan en el código cumplen los requisitos de los diagramas de capas, incluya la validación de capas en el proceso de compilación estándar de la solución. Cuando otros miembros del equipo compilen la solución, cualquier diferencia entre las dependencias del código y el diagrama de capas se notificará como un error de compilación. For more information about including layer validation in the build process, see [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Vea también
 [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md) [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md)
