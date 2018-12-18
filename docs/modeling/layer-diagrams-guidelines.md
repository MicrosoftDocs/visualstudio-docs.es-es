---
title: 'Diagramas de dependencia: instrucciones'
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: b7e282ed6aa93189ab15e608a5b3abe0c56411b9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863339"
---
# <a name="dependency-diagrams-guidelines"></a>Diagramas de dependencia: instrucciones

Describe la arquitectura de la aplicación en un nivel alto mediante la creación de *diagramas de dependencia* en Visual Studio. Asegúrese de que el código mantiene la coherencia con este diseño, valide el código con un diagrama de dependencia. También puede incluir la validación de capas en el proceso de compilación. Consulte [vídeo de Channel 9: diseño y validar la arquitectura mediante diagramas de dependencia](http://go.microsoft.com/fwlink/?LinkID=252073).

Para ver qué ediciones de Visual Studio admiten esta característica, vea [compatibilidad con la edición de arquitectura y las herramientas de modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Diagramas de dependencia no se admiten para los proyectos de .NET Core en Visual Studio 2017.

## <a name="what-is-a-dependency-diagram"></a>¿Qué es un diagrama de dependencias?

Como un diagrama de arquitectura tradicional, un diagrama de dependencia identifica los componentes primarios o las unidades funcionales del diseño y sus interdependencias. Cada nodo en el diagrama, denominado un *capa*, representa un grupo lógico de espacios de nombres, proyectos u otros artefactos. Puede dibujar las dependencias que debería haber en el diseño. A diferencia de un diagrama de arquitectura tradicional, puede comprobar que las dependencias reales del código fuente se ajustan a las dependencias especificadas que se pretenden. Al incluir la validación en el proceso de compilación normal de [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)], tiene la garantía de que el código de programa seguirá ajustándose a la arquitectura del sistema cuando se realicen cambios. Consulte [diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md).

## <a name="how-to-design-or-update-your-app-with-dependency-diagrams"></a>Cómo diseñar o actualizar la aplicación con diagramas de dependencia

Los pasos siguientes proporcionan una visión general de cómo utilizar los diagramas de dependencia dentro del proceso de desarrollo. Las secciones posteriores de este tema describen cada paso con más detalle. Si está desarrollando un nuevo diseño, omita los pasos en los que se hace referencia al código existente.

> [!NOTE]
> Estos pasos aparecen en un orden aproximado. Es probable que desee superponer las tareas, reorganizarlas para que se adapten a su situación particular y revisarlas al inicio de cada iteración del proyecto.

1.  [Crear un diagrama de dependencia](#Create) para toda la aplicación, o para una capa dentro de él.

2.  [Definir capas para representar las principales áreas o componentes funcionales](#CreateLayers) de la aplicación. Denomine estos niveles según su función, por ejemplo, "Presentación" o "Servicios". Si tiene una solución de Visual Studio, puede asociar cada capa a una colección de *artefactos*, como proyectos, espacios de nombres, archivos y así sucesivamente.

3.  [Detecte las dependencias existentes](#Generate) entre capas.

4.  [Modifique las capas y dependencias](#EditArchitecture) para mostrar la actualización que desea que el código para reflejar el diseño.

5.  [Diseñe nuevas áreas de la aplicación](#NewAreas) mediante la creación de capas que representen los principales bloques arquitectónicos o componentes y definir las dependencias para mostrar cómo cada capa emplea las otras.

6.  [Editar el diseño y la apariencia del diagrama](#EditLayout) que le ayudarán a ponerse en contacto con sus compañeros.

7.  [Valide el código con el diagrama de dependencia](#Validate) para resaltar los conflictos entre el código y la arquitectura necesaria.

8.  [Actualice el código para que se ajuste a la nueva arquitectura](#UpdateCode). Desarrolle y refactorice el código en iteraciones hasta que la validación no muestre ningún conflicto.

9. [Incluir validación de capas en el proceso de compilación](#BuildValidation) para asegurarse de que el código seguirá ajustándose a su diseño.

## <a name="Create"></a> Crear un diagrama de dependencia

Un diagrama de dependencia debe crearse dentro de un proyecto de modelado. Puede agregar un nuevo diagrama de dependencia a un proyecto de modelado existente, cree un nuevo proyecto de modelado para el diagrama de dependencia o copiar un diagrama de dependencia existente dentro del mismo proyecto de modelado.

> [!IMPORTANT]
> No agregue, arrastre ni copie un diagrama de dependencia existente de un proyecto de modelado a otro proyecto de modelado o a otra ubicación en la solución. Un diagrama de dependencia que se copia de esta manera tendrá las mismas referencias que el diagrama original, incluso si modifica el diagrama. Esto impide que la validación de capas se haga correctamente y es posible que cause otros problemas, como la pérdida de elementos u otros errores al intentar abrir el diagrama.

Consulte [crear diagramas de dependencia desde el código](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="CreateLayers"></a> Definir capas para representar áreas o componentes funcionales

Las capas representan grupos lógicos de *artefactos*, como proyectos, archivos de código, espacios de nombres, clases y métodos. Puede crear capas desde artefactos de proyectos de Visual C# y Visual Basic, o puede adjuntar especificaciones o planes a una capa vinculando documentos como archivos de Word o presentaciones de PowerPoint. Cada capa aparece como un rectángulo en el diagrama y muestra el número de artefactos vinculados a ella. Una capa puede contener capas anidadas que describan tareas más específicas.

Como regla general, denomine las capas según su función, por ejemplo, "Presentación" o "Servicios." Si los artefactos tienen una estrecha interdependencia, colóquelos en la misma capa. Si los artefactos se pueden actualizar de forma independiente o usar en aplicaciones diferentes, sitúelos en capas distintas. Para obtener información sobre los patrones de capas, visite el sitio Patterns & Practices en [ http://go.microsoft.com/fwlink/?LinkId=145794 ](http://go.microsoft.com/fwlink/?LinkId=145794).

> [!TIP]
> Existen ciertos tipos de artefactos que se pueden vincular a capas, pero que no admiten la validación con el diagrama de dependencia. Para ver si el artefacto admite la validación, abra **Explorador de capas** para examinar el **Supports Validation** propiedad del vínculo de artefacto. Consulte [detectar las dependencias existentes entre capas](#Generate).

Al actualizar una aplicación desconocida, también puede crear mapas de código. Estos diagramas pueden ayudarle a detectar patrones y dependencias mientras explora el código. También puede usar el Explorador de soluciones para examinar los espacios de nombres y las clases, que suelen corresponderse con las capas existentes. Asigne estos artefactos de código a las capas arrastrándolos desde el Explorador de soluciones a diagramas de dependencia. A continuación, puede usar diagramas de dependencia que le ayudarán a actualizar el código y mantener la coherencia con el diseño.

Vea:

-   [Creación de diagramas de dependencia a partir del código](../modeling/create-layer-diagrams-from-your-code.md)

-   [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)

-   [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)

## <a name="Generate"></a> Detectar las dependencias existentes entre capas

Una dependencia existe cuando un artefacto que está asociado a una capa tiene una referencia a un artefacto que está asociado a otra capa. Por ejemplo, una clase de una capa declara una variable que tiene una clase en otra capa. Puede detectar las dependencias existentes aplicándoles técnicas de ingeniería inversa.

> [!NOTE]
> No se puede realizar ingeniería inversa en las dependencias de ciertos tipos de artefactos. Por ejemplo, no se va a realizar ingeniería inversa en ninguna dependencia que tenga como origen o destino una capa vinculada a un archivo de texto. Para ver qué artefactos tienen dependencias que puede realizar ingeniería inversa, haga clic en una o varias capas y, a continuación, haga clic en **ver vínculos**. En **Explorador de capas**, examine el **admite validación** columna. Las dependencias no será de ingeniería inversa para los artefactos para el que esta columna muestra **False**.

### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Para realizar ingeniería inversa de las dependencias existentes entre capas

Seleccione una o varias capas, haga clic en una capa seleccionada y, a continuación, haga clic en **generar dependencias**.

Normalmente, verá algunas dependencias que no deberían existir. Puede editar estas dependencias para alinearlas con el diseño buscado.

## <a name="EditArchitecture"></a> Editar capas y dependencias para mostrar el diseño previsto

Para describir los cambios que se va a realizar en el sistema o la arquitectura deseada, siga estos pasos para editar el diagrama de dependencia. También podría realizar algunos cambios de refactorización para mejorar la estructura del código antes de extenderlo. Consulte [mejorar la estructura del código](#Improving).

|**En**|**Siga estos pasos**|
|-|-|
|Eliminar una dependencia que no debería existir|Haga clic en la dependencia y, a continuación, presione **eliminar**.|
|Cambiar o restringir la dirección de una dependencia|Establezca su **dirección** propiedad.|
|Crear nuevas dependencias|Use la **dependencia** y **dependencia bidireccional** herramientas.<br /><br /> Para dibujar varias dependencias, haga doble clic en la herramienta. Cuando haya terminado, haga clic en el **puntero** herramientas o presione la **ESC** clave.|
|Especificar qué artefactos asociados a una capa no pueden depender de los espacios de nombres especificados|Escriba los espacios de nombres en la capa **Forbidden Namespace Dependencies** propiedad. Use un punto y coma (**;**) para separar los espacios de nombres.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a los espacios de nombres especificados|Escriba los espacios de nombres en la capa **Forbidden Namespaces** propiedad. Use un punto y coma (**;**) para separar los espacios de nombres.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a uno de los espacios de nombres especificados|Escriba el espacio de nombres en la capa **Required Namespaces** propiedad. Use un punto y coma (**;**) para separar los espacios de nombres.|

### <a name="Improving"></a> Mejorar la estructura del código

Los cambios de refactorización son mejoras que no afectan al comportamiento de la aplicación, pero que facilitan los cambios y las ampliaciones del código en el futuro. Un código bien estructurado tiene un diseño que resulta fácil abstraer en un diagrama de dependencia.

Por ejemplo, si crea una capa para cada espacio de nombres del código y, a continuación, aplica técnicas de ingeniería inversa a las dependencias, debe haber un conjunto mínimo de dependencias unidireccionales entre las capas. Si crea un diagrama más detallado usando clases o métodos como capas, el resultado debería tener también las mismas características.

Si esto no es el caso, el código será más difícil de cambiar a lo largo de su vida útil y será menos apropiado para la validación con diagramas de dependencia.

## <a name="NewAreas"></a> Diseñe nuevas áreas de la aplicación

Cuando comience el desarrollo de un nuevo proyecto, o una nueva área de un nuevo proyecto, puede dibujar capas y dependencias que le ayuden a identificar los componentes primarios antes de empezar a desarrollar el código.

-   **Muestre modelos arquitectónicos identificables** en los diagramas de dependencia, si es posible. Por ejemplo, un diagrama de dependencia que describe una aplicación de escritorio puede incluir capas como presentación, lógica del dominio y Store de datos. Un diagrama de dependencia que abarque una única característica dentro de una aplicación puede tener las capas modelo, vista y controlador. Para obtener más información acerca de estos patrones, consulte [Patterns & Practices: arquitectura de la aplicación](http://go.microsoft.com/fwlink/?LinkId=145794).

-   **Crear un artefacto de código para cada capa** como un espacio de nombres, clase o componente. De este modo, le resultará más fácil hacer un seguimiento del código y vincular los artefactos de código a las capas. Tan pronto como cree cada uno de los artefactos, vincúlelo a la capa apropiada.

-   **No es necesario vincular la mayoría de las clases y otros artefactos a las capas** pues pertenecen a artefactos mayores, como espacios de nombres que ya han vinculado a las capas.

-   **Cree un nuevo diagrama de una nueva característica**. Normalmente, habrá uno o varios diagramas de dependencia que describe toda la aplicación. Si está diseñando una nueva característica de la aplicación, no agregue ni cambie los diagramas existentes. En su lugar, cree un diagrama propio en el que refleje los nuevos elementos del código. Las capas del nuevo diagrama pueden incluir las capas de la presentación, la lógica del dominio y la base de datos de la nueva característica.

     Cuando compile la aplicación, el código se validará con el diagrama general y con el diagrama más detallado de la característica.

## <a name="EditLayout"></a> Editar el diseño para su presentación y explicación

Para que le resulte más fácil identificar las capas y dependencias o para analizarlas con los miembros del equipo, edite el aspecto y el diseño del diagrama de los siguientes modos:

-   Cambiar el tamaño, la forma y la posición de las capas.

-   Cambiar el color de las capas y las dependencias.

    -   Seleccione una o varias capas o dependencias, con el botón secundario y, a continuación, haga clic en **propiedades**. En el **propiedades** ventana, edite el **Color** propiedad.

## <a name="Validate"></a> Valide el código con el diagrama

Cuando se ha editado el diagrama, puede validarlo con el código manualmente en cualquier momento o automáticamente cada vez que se compila.

Vea:

-   [Validación de código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)

-   [Incluir validación de capas en el proceso de compilación](#BuildValidation)

## <a name="UpdateCode"></a> Actualice el código para que se ajuste a la nueva arquitectura

Normalmente, los errores aparecerán la primera vez que valide el código con un diagrama de dependencias actualizado. Estos errores pueden tener varias causas:

-   Un artefacto se ha asignado a la capa equivocada. En este caso, mueva el artefacto.

-   Un artefacto, como por ejemplo una clase, usa otra clase de forma que hay conflictos con su arquitectura. En este caso, tiene que refactorizar el código para quitar la dependencia.

Para resolver estos errores, actualice el código hasta no aparezcan más errores durante la validación. Normalmente, este es un proceso iterativo. Para obtener más información acerca de estos errores, vea [validar código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> Medida que desarrolla o refactoriza el código, es posible que tenga nuevos artefactos para vincular al diagrama de dependencia. Sin embargo, esto podría no ser necesario, por ejemplo, si tiene capas que representan espacios de nombres existentes, y el nuevo código solo agrega más material a estos espacios de nombres.

Durante el proceso de desarrollo, puede que desee suprimir algunos de los conflictos notificados durante la validación. Por ejemplo, es posible que desee suprimir errores de los que ya se ha ocupado o que no son pertinentes para su escenario concreto. Cuando se suprime un error, es una buena práctica para registrar un elemento de trabajo en Team Foundation. Para llevar a cabo esta tarea, vea [validar código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md).

## <a name="BuildValidation"></a> Incluir validación de capas en el proceso de compilación

Para asegurarse de que los cambios futuros en el código se ajustan a los diagramas de dependencia, incluir la validación de capas al proceso de compilación estándar de su solución. Siempre que otros miembros del equipo compilen la solución, las diferencias entre las dependencias en el código y el diagrama de dependencia se notificarán como errores de compilación. Para obtener más información sobre cómo incluir la validación de capas en el proceso de compilación, véase [validar código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Vea también

- [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)
- [Creación de diagramas de dependencia a partir del código](../modeling/create-layer-diagrams-from-your-code.md)