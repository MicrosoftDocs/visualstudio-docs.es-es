---
title: 'Diagramas de capas: instrucciones | Microsoft Docs'
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
ms.openlocfilehash: 21376668eef88d3d8ce42ff73785b972be045cb2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850634"
---
# <a name="layer-diagrams-guidelines"></a>Diagrama de capas: Instrucciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Describa la arquitectura de la aplicación en un nivel alto mediante la creación de *diagramas de capas* en Visual Studio. Para asegurarse de que el código mantiene la coherencia con este diseño, valide el código con un diagrama de capas. También puede incluir la validación de capas en el proceso de compilación. Consulte [vídeo de Channel 9: diseñar y validar la arquitectura mediante diagramas de capas](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="what-is-a-layer-diagram"></a>¿Qué es un diagrama de capas?
 Al igual que en un diagrama de arquitectura tradicional, en un diagrama de capas se identifican los componentes primarios o las unidades funcionales del diseño y sus interdependencias. Cada nodo del diagrama, denominado *capa*, representa un grupo lógico de espacios de nombres, proyectos u otros artefactos. Puede dibujar las dependencias que debería haber en el diseño. A diferencia de un diagrama de arquitectura tradicional, puede comprobar que las dependencias reales del código fuente se ajustan a las dependencias especificadas que se pretenden. Al incluir la validación en el proceso de compilación normal de [!INCLUDE[esprtfs](../includes/esprtfs-md.md)], tiene la garantía de que el código de programa seguirá ajustándose a la arquitectura del sistema cuando se realicen cambios. Vea [diagramas de capas: referencia](../modeling/layer-diagrams-reference.md).

## <a name="how-to-design-or-update-your-app-with-layer-diagrams"></a><a name="Update"></a> Cómo diseñar o actualizar la aplicación con diagramas de capas
 Los siguientes pasos proporcionan información general sobre cómo utilizar los diagramas de capas dentro del proceso de desarrollo. Las secciones posteriores de este tema describen cada paso con más detalle. Si está desarrollando un nuevo diseño, omita los pasos en los que se hace referencia al código existente.

> [!NOTE]
> Estos pasos aparecen en un orden aproximado. Es probable que desee superponer las tareas, reorganizarlas para que se adapten a su situación particular y revisarlas al inicio de cada iteración del proyecto.

1. [Cree un diagrama de capas](#Create) para toda la aplicación o para una capa dentro de ella.

2. [Definir capas para representar las áreas funcionales principales o los componentes](#CreateLayers) de la aplicación. Denomine estos niveles según su función, por ejemplo, "Presentación" o "Servicios". Si tiene una [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] solución, puede asociar cada capa a una colección de *artefactos*, como proyectos, espacios de nombres, archivos, etc.

3. [Detecta las dependencias existentes entre las](#Generate) capas.

4. [Edite las capas y las dependencias](#EditArchitecture) para mostrar el diseño actualizado que desea que refleje el código.

5. [Diseñe nuevas áreas de la aplicación](#NewAreas) mediante la creación de capas para representar los componentes o bloques arquitectónicos principales y la definición de dependencias para mostrar cómo cada capa usa las otras.

6. [Edite el diseño y la apariencia del diagrama](#EditLayout) para ayudarle a analizarlo con sus compañeros.

7. [Valide el código con el diagrama de capas](#Validate) para resaltar los conflictos entre el código y la arquitectura que necesite.

8. [Actualice el código para que se ajuste a la nueva arquitectura](#UpdateCode). Desarrolle y refactorice el código en iteraciones hasta que la validación no muestre ningún conflicto.

9. [Incluya la validación de capas en el proceso de compilación](#BuildValidation) para asegurarse de que el código sigue cumpliendo con el diseño.

## <a name="create-a-layer-diagram"></a><a name="Create"></a> Crear un diagrama de capas
 Los diagramas de capas deben crearse dentro de un proyecto de modelado. Se puede agregar un nuevo diagrama de capas a un proyecto de modelado ya existente, crear un nuevo proyecto de modelado para el diagrama de capas o bien copiar un diagrama de capas ya existente en el mismo proyecto de modelado.

> [!IMPORTANT]
> No agregue, arrastre ni copie un diagrama de capas de un proyecto de modelado a otro, ni a otra ubicación de la solución. Un diagrama de capas que se copia de esta manera tendrá las mismas referencias que el diagrama original, incluso si se modifica. Esto impide que la validación de capas se haga correctamente y es posible que cause otros problemas, como la pérdida de elementos u otros errores al intentar abrir el diagrama.

 Vea [crear diagramas de capas desde el código](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="define-layers-to-represent-functional-areas-or-components"></a><a name="CreateLayers"></a> Definir capas para representar áreas funcionales o componentes
 Las capas representan grupos lógicos de *artefactos*, como proyectos, archivos de código, espacios de nombres, clases y métodos. Se pueden crear capas a partir de artefactos de proyectos de Visual C# .NET y Visual Basic .NET, o bien se pueden adjuntar especificaciones o planes a una capa vinculando documentos, como archivos de Word o presentaciones de PowerPoint. Cada capa aparece como un rectángulo en el diagrama y muestra el número de artefactos vinculados a ella. Una capa puede contener capas anidadas que describan tareas más específicas.

 Como regla general, denomine las capas según su función, por ejemplo, "Presentación" o "Servicios." Si los artefactos tienen una estrecha interdependencia, colóquelos en la misma capa. Si los artefactos se pueden actualizar de forma independiente o usar en aplicaciones diferentes, sitúelos en capas distintas. Para obtener información sobre los patrones de capas, visite el sitio Patterns & Practices en [http://go.microsoft.com/fwlink/?LinkId=145794](https://apparch.codeplex.com/Wiki/View.aspx?title=Application Patterns&referringTitle=Home) .

> [!TIP]
> Existen ciertos tipos de artefactos que se pueden vincular a capas, pero que no admiten la validación con el diagrama de capas. Para ver si el artefacto admite la validación, abra el **Explorador de capas** para examinar la propiedad **Supports Validation** del vínculo de artefacto. Consulte [detectar dependencias existentes entre capas](#Generate).

 Al actualizar una aplicación desconocida, también puede crear mapas de código. Estos diagramas pueden ayudarle a detectar patrones y dependencias mientras explora el código. También puede usar el Explorador de soluciones para examinar los espacios de nombres y las clases, que suelen corresponderse con las capas existentes. Asigne estos artefactos de código a las capas arrastrándolos desde el Explorador de soluciones hasta los diagramas de capas. Después, puede usar diagramas de capas, que le ayudarán a actualizar el código y mantener la coherencia con el diseño.

 Consulte:

- [Crear diagramas de capas a partir del código](../modeling/create-layer-diagrams-from-your-code.md)

- [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)

- [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)

## <a name="discover-existing-dependencies-between-layers"></a><a name="Generate"></a> Detección de dependencias existentes entre capas
 Una dependencia existe cuando un artefacto que está asociado a una capa tiene una referencia a un artefacto que está asociado a otra capa. Por ejemplo, una clase de una capa declara una variable que tiene una clase en otra capa. Puede detectar las dependencias existentes aplicándoles técnicas de ingeniería inversa.

> [!NOTE]
> No se puede realizar ingeniería inversa en las dependencias de ciertos tipos de artefactos. Por ejemplo, no se va a realizar ingeniería inversa en ninguna dependencia que tenga como origen o destino una capa vinculada a un archivo de texto. Para ver qué artefactos tienen dependencias a las que puede aplicar ingeniería inversa, haga clic con el botón secundario en una o varias capas y, a continuación, haga clic en **ver vínculos**. En el **Explorador de capas**, examine la columna **admite validación** . No se aplicará ingeniería inversa a las dependencias para los artefactos para los que esta columna muestra **false**.

#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Para realizar ingeniería inversa de las dependencias existentes entre capas

- Seleccione una o varias capas, haga clic con el botón secundario en una capa seleccionada y, a continuación, haga clic en **generar dependencias**.

  Normalmente, verá algunas dependencias que no deberían existir. Puede editar estas dependencias para alinearlas con el diseño buscado.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditArchitecture"></a> Editar capas y dependencias para mostrar el diseño previsto
 Para describir los cambios que piensa realizar en el sistema o la arquitectura deseada, use los pasos siguientes para editar el diagrama de capas. También podría realizar algunos cambios de refactorización para mejorar la estructura del código antes de extenderlo. Vea [mejorar la estructura del código](#Improving).

|**To**|**Siga estos pasos**|
|------------|-----------------------------|
|Eliminar una dependencia que no debería existir|Haga clic en la dependencia y, a continuación, presione **Supr**.|
|Cambiar o restringir la dirección de una dependencia|Establezca su propiedad **Direction** .|
|Crear nuevas dependencias|Use las herramientas **de dependencia de dependencia y** **bidireccional** .<br /><br /> Para dibujar varias dependencias, haga doble clic en la herramienta. Cuando haya terminado, haga clic en la herramienta **puntero** o presione la tecla **ESC** .|
|Especificar qué artefactos asociados a una capa no pueden depender de los espacios de nombres especificados|Escriba los espacios de nombres en la propiedad **Forbidden namespace dependencies** de la capa. Use un punto y coma (**;**) para separar los espacios de nombres.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a los espacios de nombres especificados|Escriba los espacios de nombres en la propiedad **Forbidden namespaces** de la capa. Use un punto y coma (**;**) para separar los espacios de nombres.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a uno de los espacios de nombres especificados|Escriba el espacio de nombres en la propiedad **espacios de nombres necesarios** de la capa. Use un punto y coma (**;**) para separar los espacios de nombres.|

### <a name="improving-the-structure-of-the-code"></a><a name="Improving"></a> Mejorar la estructura del código
 Los cambios de refactorización son mejoras que no afectan al comportamiento de la aplicación, pero que facilitan los cambios y las ampliaciones del código en el futuro. Un código bien estructurado tiene un diseño que resulta fácil abstraer en un diagrama de capas.

 Por ejemplo, si crea una capa para cada espacio de nombres del código y, a continuación, aplica técnicas de ingeniería inversa a las dependencias, debe haber un conjunto mínimo de dependencias unidireccionales entre las capas. Si crea un diagrama más detallado usando clases o métodos como capas, el resultado debería tener también las mismas características.

 De lo contrario, el código resultará más difícil de modificar a lo largo de su vida útil y será menos apropiado para llevar a cabo la validación con diagramas de capas.

## <a name="design-new-areas-of-your-application"></a><a name="NewAreas"></a> Diseñar nuevas áreas de la aplicación
 Cuando comience el desarrollo de un nuevo proyecto, o una nueva área de un nuevo proyecto, puede dibujar capas y dependencias que le ayuden a identificar los componentes primarios antes de empezar a desarrollar el código.

- Si es posible, **muestre patrones arquitectónicos identificables** en los diagramas de capas. Por ejemplo, un diagrama de capas en el que se describa una aplicación de escritorio puede incluir capas como Presentación, Lógica del dominio y Almacén de datos. Un diagrama de capas que abarque una única característica de una aplicación puede tener las capas Modelo, Ver y Controlador. Para obtener más información sobre estos patrones, consulte [patterns & Practices: arquitectura](https://apparch.codeplex.com/Wiki/View.aspx?title=Application Patterns&referringTitle=Home)de la aplicación.

     Si genera a menudo modelos similares, cree una herramienta personalizada. Vea [definir un elemento personalizado del cuadro de herramientas de modelado](../modeling/define-a-custom-modeling-toolbox-item.md).

- **Cree un artefacto de código para cada capa** , como un espacio de nombres, una clase o un componente. De este modo, le resultará más fácil hacer un seguimiento del código y vincular los artefactos de código a las capas. Tan pronto como cree cada uno de los artefactos, vincúlelo a la capa apropiada.

- **No es necesario vincular la mayoría de las clases y otros artefactos a capas** porque se encuentran en artefactos más grandes, como los espacios de nombres que ya se han vinculado a las capas.

- **Cree un nuevo diagrama para una nueva característica**. Normalmente, habrá uno o varios diagramas de capas en los que se describa toda la aplicación. Si está diseñando una nueva característica de la aplicación, no agregue ni cambie los diagramas existentes. En su lugar, cree un diagrama propio en el que refleje los nuevos elementos del código. Las capas del nuevo diagrama pueden incluir las capas de la presentación, la lógica del dominio y la base de datos de la nueva característica.

     Cuando compile la aplicación, el código se validará con el diagrama general y con el diagrama más detallado de la característica.

## <a name="edit-the-layout-for-presentation-and-discussion"></a><a name="EditLayout"></a> Editar el diseño de presentación y debate
 Para que le resulte más fácil identificar las capas y dependencias o para analizarlas con los miembros del equipo, edite el aspecto y el diseño del diagrama de los siguientes modos:

- Cambiar el tamaño, la forma y la posición de las capas.

- Cambiar el color de las capas y las dependencias.

  - Seleccione una o varias capas o dependencias, haga clic con el botón secundario y, a continuación, haga clic en **propiedades**. En la ventana **propiedades** , edite la propiedad **color** .

## <a name="validate-the-code-against-the-diagram"></a><a name="Validate"></a> Validar el código con el diagrama
 Una vez editado el diagrama, puede validarlo con el código manualmente en cualquier momento o automáticamente cada vez que se ejecute una compilación local o [!INCLUDE[esprbuild](../includes/esprbuild-md.md)].

 Consulte:

- [Validar código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md)

- [Incluir la validación de capas en el proceso de compilación](#BuildValidation)

## <a name="update-the-code-to-conform-to-the-new-architecture"></a><a name="UpdateCode"></a> Actualización del código para que se ajuste a la nueva arquitectura
 Normalmente, los errores aparecerán la primera vez que valide el código contra un diagrama de capas actualizado. Estos errores pueden tener varias causas:

- Un artefacto se ha asignado a la capa equivocada. En este caso, mueva el artefacto.

- Un artefacto, como por ejemplo una clase, usa otra clase de forma que hay conflictos con su arquitectura. En este caso, tiene que refactorizar el código para quitar la dependencia.

  Para resolver estos errores, actualice el código hasta no aparezcan más errores durante la validación. Normalmente, este es un proceso iterativo. Para obtener más información sobre estos errores, vea [validar el código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> A medida que desarrolla o refactoriza el código, es posible que tenga nuevos artefactos que deba vincular al diagrama de capas. Sin embargo, esto podría no ser necesario, por ejemplo, si tiene capas que representan espacios de nombres existentes, y el nuevo código solo agrega más material a estos espacios de nombres.

 Durante el proceso de desarrollo, puede que desee suprimir algunos de los conflictos notificados durante la validación. Por ejemplo, es posible que desee suprimir errores de los que ya se ha ocupado o que no son pertinentes para su escenario concreto. Cuando se suprime un error, conviene registrar un elemento de trabajo en [!INCLUDE[esprfound](../includes/esprfound-md.md)]. Para realizar esta tarea, vea [validar el código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md).

## <a name="include-layer-validation-in-the-build-process"></a><a name="BuildValidation"></a> Incluir la validación de capas en el proceso de compilación
 Para asegurarse de que los futuros cambios que se hagan en el código cumplen los requisitos de los diagramas de capas, incluya la validación de capas en el proceso de compilación estándar de la solución. Cuando otros miembros del equipo compilen la solución, cualquier diferencia entre las dependencias del código y el diagrama de capas se notificará como un error de compilación. Para obtener más información sobre cómo incluir la validación de capas en el proceso de compilación, vea [validar el código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Consulte también
 [Diagramas de capas: referencia](../modeling/layer-diagrams-reference.md) [crear diagramas de capas desde el código](../modeling/create-layer-diagrams-from-your-code.md)
