---
title: 'Diagramas de dependencia: instrucciones'
description: Aprenda a describir la arquitectura de la aplicación en un nivel alto mediante la creación de diagramas de dependencia en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f46e2b774cd4da2ef9cdb9ddef7efd19f731ade7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391028"
---
# <a name="dependency-diagrams-guidelines"></a>Diagramas de dependencias: directrices

Describa la arquitectura de la aplicación en un nivel alto mediante la creación de *diagramas de* dependencia en Visual Studio. Asegúrese de que el código sigue siendo coherente con este diseño validando el código con un diagrama de dependencias. También puede incluir la validación de capas en el proceso de compilación. Vea [Vídeo de Channel 9: Diseño y validación de la arquitectura mediante diagramas de dependencias.](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)

Para ver qué ediciones de Visual Studio admiten esta característica, consulte [Compatibilidad de ediciones con las herramientas de arquitectura y modelado](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

> [!NOTE]
> Los diagramas de dependencias para proyectos de .NET Core se admiten a partir Visual Studio versión 16.2 de 2019.

## <a name="what-is-a-dependency-diagram"></a>¿Qué es un diagrama de dependencias?

Al igual que un diagrama de arquitectura tradicional, un diagrama de dependencias identifica los componentes principales o las unidades funcionales del diseño y sus interdependencias. Cada nodo del diagrama, denominado *capa*, representa un grupo lógico de espacios de nombres, proyectos u otros artefactos. Puede dibujar las dependencias que debería haber en el diseño. A diferencia de un diagrama de arquitectura tradicional, puede comprobar que las dependencias reales del código fuente se ajustan a las dependencias especificadas que se pretenden. Al incluir la validación en el proceso de compilación normal de [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)], tiene la garantía de que el código de programa seguirá ajustándose a la arquitectura del sistema cuando se realicen cambios. Vea [Diagramas de dependencias: Referencia.](../modeling/layer-diagrams-reference.md)

## <a name="how-to-design-or-update-your-app-with-dependency-diagrams"></a>Diseño o actualización de la aplicación con diagramas de dependencias

Los pasos siguientes proporcionan información general sobre cómo usar diagramas de dependencias dentro del proceso de desarrollo. Las secciones posteriores de este tema describen cada paso con más detalle. Si está desarrollando un nuevo diseño, omita los pasos en los que se hace referencia al código existente.

> [!NOTE]
> Estos pasos aparecen en un orden aproximado. Es probable que desee superponer las tareas, reorganizarlas para que se adapten a su situación particular y revisarlas al inicio de cada iteración del proyecto.

1. [Cree un diagrama de dependencias](#Create) para toda la aplicación o para una capa dentro de ella.

2. [Defina capas para representar las áreas funcionales principales o los componentes](#CreateLayers) de la aplicación. Denomine estos niveles según su función, por ejemplo, "Presentación" o "Servicios". Si tiene una solución Visual Studio, puede asociar cada capa a una colección de *artefactos,* como proyectos, espacios de nombres, archivos, entre otros.

3. [Detectar las dependencias existentes](#Generate) entre capas.

4. [Edite las capas y las dependencias](#EditArchitecture) para mostrar el diseño actualizado que desea que refleje el código.

5. [Diseñe nuevas áreas de la aplicación mediante](#NewAreas) la creación de capas para representar los componentes o bloques de arquitectura principales y la definición de dependencias para mostrar cómo cada capa usa los demás.

6. [Edite el diseño y la apariencia del diagrama para](#EditLayout) ayudarle a analizarlo con sus compañeros.

7. [Valide el código con el diagrama de dependencias](#Validate) para resaltar los conflictos entre el código y la arquitectura que necesita.

8. [Actualice el código para que se ajuste a la nueva arquitectura](#UpdateCode). Desarrolle y refactorice el código en iteraciones hasta que la validación no muestre ningún conflicto.

9. [Incluya la validación de capas en el proceso de compilación](#BuildValidation) para asegurarse de que el código sigue apeando el diseño.

## <a name="create-a-dependency-diagram"></a><a name="Create"></a> Creación de un diagrama de dependencias

Se debe crear un diagrama de dependencias dentro de un proyecto de modelado. Puede agregar un nuevo diagrama de dependencias a un proyecto de modelado existente, crear un nuevo proyecto de modelado para el diagrama de dependencias o copiar un diagrama de dependencias existente dentro del mismo proyecto de modelado.

> [!IMPORTANT]
> No agregue, arrastre ni copie un diagrama de dependencias existente de un proyecto de modelado a otro proyecto de modelado o a otra ubicación de la solución. Un diagrama de dependencias que se copie de esta manera tendrá las mismas referencias que el diagrama original, incluso si modifica el diagrama. Esto impide que la validación de capas se haga correctamente y es posible que cause otros problemas, como la pérdida de elementos u otros errores al intentar abrir el diagrama.

Consulte [Creación de diagramas de dependencias a partir del código.](../modeling/create-layer-diagrams-from-your-code.md)

## <a name="define-layers-to-represent-functional-areas-or-components"></a><a name="CreateLayers"></a> Definición de capas para representar áreas o componentes funcionales

Las capas representan grupos *lógicos de artefactos,* como proyectos, archivos de código, espacios de nombres, clases y métodos. Puede crear capas a partir de artefactos de proyectos de Visual C# y Visual Basic, o puede adjuntar especificaciones o planes a una capa mediante la vinculación de documentos, como archivos de Word o presentaciones de PowerPoint. Cada capa aparece como un rectángulo en el diagrama y muestra el número de artefactos vinculados a ella. Una capa puede contener capas anidadas que describan tareas más específicas.

Como regla general, denomine las capas según su función, por ejemplo, "Presentación" o "Servicios." Si los artefactos tienen una estrecha interdependencia, colóquelos en la misma capa. Si los artefactos se pueden actualizar de forma independiente o usar en aplicaciones diferentes, sitúelos en capas distintas. Para obtener información sobre los patrones de capas, visite el sitio patterns & Practices en [http://go.microsoft.com/fwlink/?LinkId=145794](https://archive.codeplex.com/?p=apparch) .

> [!TIP]
> Hay ciertos tipos de artefactos que se pueden vincular a capas, pero que no admiten la validación en el diagrama de dependencias. Para ver si el artefacto admite la validación, abra **el Explorador de capas** para examinar la propiedad Supports **Validation** del vínculo del artefacto. Consulte [Detectar dependencias existentes entre capas.](#Generate)

Al actualizar una aplicación desconocida, también puede crear mapas de código. Estos diagramas pueden ayudarle a detectar patrones y dependencias mientras explora el código. También puede usar el Explorador de soluciones para examinar los espacios de nombres y las clases, que suelen corresponderse con las capas existentes. Asigne estos artefactos de código a las capas arrastrándolos desde Explorador de soluciones a diagramas de dependencias. A continuación, puede usar diagramas de dependencias para ayudarle a actualizar el código y mantener su coherencia con el diseño.

Consulte:

- [Crear diagramas de dependencia a partir del código](../modeling/create-layer-diagrams-from-your-code.md)

- [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)

- [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)

## <a name="discover-existing-dependencies-between-layers"></a><a name="Generate"></a> Detectar dependencias existentes entre capas

Una dependencia existe cuando un artefacto que está asociado a una capa tiene una referencia a un artefacto que está asociado a otra capa. Por ejemplo, una clase de una capa declara una variable que tiene una clase en otra capa. Puede detectar las dependencias existentes aplicándoles técnicas de ingeniería inversa.

> [!NOTE]
> No se puede realizar ingeniería inversa en las dependencias de ciertos tipos de artefactos. Por ejemplo, no se va a realizar ingeniería inversa en ninguna dependencia que tenga como origen o destino una capa vinculada a un archivo de texto. Para ver qué artefactos tienen dependencias que puede realizar en ingeniería inversa, haga clic con el botón derecho en una o varias capas y, a continuación, haga clic **en Ver vínculos.** En **el Explorador de capas,** examine la columna Supports Validation **(Admite** validación). Las dependencias no se diseñarán de forma inversa para los artefactos para los que esta columna muestra **False**.

### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Para realizar ingeniería inversa de las dependencias existentes entre capas

Seleccione una o varias capas, haga clic con el botón derecho en una capa seleccionada y, a continuación, haga clic **en Generar dependencias.**

Normalmente, verá algunas dependencias que no deberían existir. Puede editar estas dependencias para alinearlas con el diseño buscado.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditArchitecture"></a> Edición de capas y dependencias para mostrar el diseño previsto

Para describir los cambios que planea realizar en el sistema o en la arquitectura prevista, siga estos pasos para editar el diagrama de dependencias. También podría realizar algunos cambios de refactorización para mejorar la estructura del código antes de extenderlo. Vea [Improving the structure of the code](#Improving)(Mejora de la estructura del código).

|**To**|**Siga estos pasos**|
|-|-|
|Eliminar una dependencia que no debería existir|Haga clic en la dependencia y, a continuación, **presione DELETE**.|
|Cambiar o restringir la dirección de una dependencia|Establezca su **propiedad Direction.**|
|Crear nuevas dependencias|Use las **herramientas Dependencia** y **Dependencia bidireccional.**<br /><br /> Para dibujar varias dependencias, haga doble clic en la herramienta. Cuando haya terminado, haga clic en la **herramienta Puntero** o presione la **tecla ESC.**|
|Especificar qué artefactos asociados a una capa no pueden depender de los espacios de nombres especificados|Escriba los espacios de nombres en la propiedad **Dependencias** de espacio de nombres prohibido de la capa. Use un punto y coma (**;**) para separar los espacios de nombres.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a los espacios de nombres especificados|Escriba los espacios de nombres en la propiedad Espacios de nombres **prohibidos de la** capa. Use un punto y coma (**;**) para separar los espacios de nombres.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a uno de los espacios de nombres especificados|Escriba el espacio de nombres en la propiedad **Espacios de nombres necesarios de la** capa. Use un punto y coma (**;**) para separar los espacios de nombres.|

### <a name="improving-the-structure-of-the-code"></a><a name="Improving"></a> Mejora de la estructura del código

Los cambios de refactorización son mejoras que no afectan al comportamiento de la aplicación, pero que facilitan los cambios y las ampliaciones del código en el futuro. El código bien estructurado tiene un diseño que es fácil de abstraer en un diagrama de dependencias.

Por ejemplo, si crea una capa para cada espacio de nombres del código y, a continuación, aplica técnicas de ingeniería inversa a las dependencias, debe haber un conjunto mínimo de dependencias unidireccionales entre las capas. Si crea un diagrama más detallado usando clases o métodos como capas, el resultado debería tener también las mismas características.

Si este no es el caso, el código será más difícil de cambiar a lo largo de su vida y será menos adecuado para la validación mediante diagramas de dependencias.

## <a name="design-new-areas-of-your-application"></a><a name="NewAreas"></a> Diseño de nuevas áreas de la aplicación

Cuando comience el desarrollo de un nuevo proyecto, o una nueva área de un nuevo proyecto, puede dibujar capas y dependencias que le ayuden a identificar los componentes primarios antes de empezar a desarrollar el código.

- **Mostrar patrones arquitectónicos identificables en** los diagramas de dependencias, si es posible. Por ejemplo, un diagrama de dependencias que describe una aplicación de escritorio podría incluir capas como Presentación, Lógica de dominio y Almacén de datos. Un diagrama de dependencias que cubre una sola característica dentro de una aplicación podría tener capas como Modelo, Vista y Controlador. Para obtener más información sobre estos patrones, vea [Patterns & Practices: Application Architecture](https://archive.codeplex.com/?p=apparch).

- **Cree un artefacto de código para cada capa,** como un espacio de nombres, una clase o un componente. De este modo, le resultará más fácil hacer un seguimiento del código y vincular los artefactos de código a las capas. Tan pronto como cree cada uno de los artefactos, vincúlelo a la capa apropiada.

- **No es necesario vincular la** mayoría de las clases y otros artefactos a capas porque se encuentran dentro de artefactos más grandes, como espacios de nombres que ya se han vinculado a capas.

- **Cree un nuevo diagrama para una nueva característica**. Normalmente, habrá uno o varios diagramas de dependencia que describan toda la aplicación. Si está diseñando una nueva característica de la aplicación, no agregue ni cambie los diagramas existentes. En su lugar, cree un diagrama propio en el que refleje los nuevos elementos del código. Las capas del nuevo diagrama pueden incluir las capas de la presentación, la lógica del dominio y la base de datos de la nueva característica.

     Cuando compile la aplicación, el código se validará con el diagrama general y con el diagrama más detallado de la característica.

## <a name="edit-the-layout-for-presentation-and-discussion"></a><a name="EditLayout"></a> Edición del diseño para presentación y discusión

Para que le resulte más fácil identificar las capas y dependencias o para analizarlas con los miembros del equipo, edite el aspecto y el diseño del diagrama de los siguientes modos:

- Cambiar el tamaño, la forma y la posición de las capas.

- Cambiar el color de las capas y las dependencias.

  - Seleccione una o varias capas o dependencias, haga clic con el botón derecho y, a continuación, haga clic en **Propiedades.** En la **ventana** Propiedades, edite la **propiedad** Color.

## <a name="validate-the-code-against-the-diagram"></a><a name="Validate"></a> Validación del código en el diagrama

Cuando haya editado el diagrama, puede validarlo con el código manualmente en cualquier momento o automáticamente cada vez que compile.

Vea:

- [Validación código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)

- [Incluir la validación de capas en el proceso de compilación](#BuildValidation)

## <a name="update-the-code-to-conform-to-the-new-architecture"></a><a name="UpdateCode"></a> Actualización del código para que se ajuste a la nueva arquitectura

Normalmente, los errores aparecerán la primera vez que valide el código en un diagrama de dependencias actualizado. Estos errores pueden tener varias causas:

- Un artefacto se ha asignado a la capa equivocada. En este caso, mueva el artefacto.

- Un artefacto, como por ejemplo una clase, usa otra clase de forma que hay conflictos con su arquitectura. En este caso, tiene que refactorizar el código para quitar la dependencia.

Para resolver estos errores, actualice el código hasta no aparezcan más errores durante la validación. Normalmente, este es un proceso iterativo. Para obtener más información sobre estos errores, vea [Validar código con diagramas de dependencias.](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> A medida que desarrolla o refactoriza el código, es posible que tenga nuevos artefactos para vincular al diagrama de dependencias. Sin embargo, esto podría no ser necesario, por ejemplo, si tiene capas que representan espacios de nombres existentes, y el nuevo código solo agrega más material a estos espacios de nombres.

Durante el proceso de desarrollo, puede que desee suprimir algunos de los conflictos notificados durante la validación. Por ejemplo, es posible que desee suprimir errores de los que ya se ha ocupado o que no son pertinentes para su escenario concreto. Cuando se suprime un error, es una buena práctica registrar un elemento de trabajo en Team Foundation. Para realizar esta tarea, vea [Validar código con diagramas de dependencia.](../modeling/validate-code-with-layer-diagrams.md)

## <a name="include-layer-validation-in-the-build-process"></a><a name="BuildValidation"></a> Incluir validación de capas en el proceso de compilación

Para asegurarse de que los cambios futuros en el código se ajustan a los diagramas de dependencias, incluya la validación de capas en el proceso de compilación estándar de la solución. Cada vez que otros miembros del equipo compilen la solución, las diferencias entre las dependencias del código y el diagrama de dependencias se notifican como errores de compilación. Para obtener más información sobre cómo incluir la validación de capas en el proceso de compilación, vea [Validar código con diagramas de dependencia.](../modeling/validate-code-with-layer-diagrams.md)

## <a name="see-also"></a>Vea también

- [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)
- [Crear diagramas de dependencia a partir del código](../modeling/create-layer-diagrams-from-your-code.md)
