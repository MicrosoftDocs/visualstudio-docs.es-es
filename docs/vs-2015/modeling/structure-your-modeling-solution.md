---
title: Structure your modeling solution | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2ba70ba4-2cea-4e01-93c2-055903d59470
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 83606b56e6509f1db77b590ec44d991ef97cf82e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298163"
---
# <a name="structure-your-modeling-solution"></a>Estructurar la solución de modelado

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para usar eficazmente los modelos en un proyecto de desarrollo, los miembros del equipo deben ser capaces de trabajar en los modelos de diferentes partes del proyecto al mismo tiempo. En este tema, se sugiere un esquema para dividir la aplicación en diferentes partes que corresponden a las capas en un diagrama de capas general.

Para iniciar un proyecto o subproyecto rápidamente, resulta útil disponer de una plantilla de proyecto que siga la estructura del proyecto que ha elegido. En este tema se describe cómo crear y usar este tipo de plantilla.

En este tema se supone que está trabajando en un proyecto que es lo suficientemente grande como para necesitar varios miembros del equipo y que quizás tenga varios equipos. El código y los modelos del proyecto se almacenan en un sistema de control de código fuente como [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]. Al menos algunos miembros del equipo usan Visual Studio para desarrollar modelos, mientras que otros miembros del equipo pueden ver los modelos con otras versiones de Visual Studio.

To see which versions of Visual Studio support each tool and modeling feature, see [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="solution-structure"></a>Estructura de solución

En un proyecto grande o mediano, la estructura del equipo se basa en la estructura de la aplicación. Cada equipo usa una solución de Visual Studio.

#### <a name="to-divide-an-application-into-layers"></a>Para dividir una aplicación en capas

1. Base la estructura de las soluciones en la estructura de la aplicación, como la aplicación web, aplicación de servicio o aplicación de escritorio. A variety of common architectures is discussed in [Application Archetypes in the Microsoft Application Architecture Guide](https://go.microsoft.com/fwlink/?LinkId=196681).

2. Cree una solución [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], a la que llamaremos solución de arquitectura. Esta solución se usará para crear el diseño general del sistema. Contendrá modelos, pero ningún código.

    Agregue un diagrama de capas a esta solución. En el diagrama de capas, dibuje la arquitectura que ha elegido para la aplicación. Por ejemplo, el diagrama puede mostrar estas capas y las dependencias entre ellas: presentación, lógica de negocios y datos.

    You can create the layer diagram and a new Visual Studio solution at the same time by using the **New UML or Layer Diagram** command on the **Architecture** menu.

3. Agregue al modelo de arquitectura diagramas UML que representen los conceptos importantes del negocio, así como casos de uso a los que se haga referencia en el diseño de todas las capas.

4. Cree una solución de Visual Studio independiente para cada capa en la capa de arquitectura.

    Estas soluciones se usarán para desarrollar el código de las capas.

5. Cree modelos UML que representen los diseños de las capas y los conceptos que son comunes para todas las capas. Organice los modelos para que se puedan ver todos desde la solución de arquitectura y para que se puedan ver los modelos relevantes en cada capa.

    Puede conseguirlo mediante cualquiera de los procedimientos siguientes. La primera alternativa crea un proyecto de modelado independiente para cada capa, mientras que la segunda crea un proyecto de modelado que se comparte entre las capas.

###### <a name="to-use-a-separate-modeling-project-for-each-layer"></a>Para usar un proyecto de modelado independiente para cada capa

1. Cree un proyecto de modelado en la solución de cada capa.

    Este modelo incluirá diagramas UML que describen los requisitos y el diseño de dicha capa. También puede incluir los diagramas de capas que muestran capas anidadas.

    Ahora dispone de un modelo para cada capa, además de un modelo para la arquitectura de la aplicación. Cada modelo se encuentra en su propia solución. Esto permite a los miembros del equipo trabajar en las capas al mismo tiempo.

2. Para la solución de arquitectura, agregue el proyecto de modelado de la solución de cada capa. Para ello, abra la solución de arquitectura. In Solution Explorer, right-click the solution node, point to Add, and then click **Existing Project**. Navegue hasta el proyecto de modelado (.modelproj) de una solución de capa.

    Ahora, cada modelo es visible en dos soluciones: la solución "principal" y la solución de arquitectura.

3. En el proyecto de modelado de cada capa, agregue un nuevo diagrama de capas. Empiece con una copia del diagrama de capas de la arquitectura. Puede eliminar los elementos que no sean dependencias del diagrama de capas.

    También puede agregar diagramas de capas que representen la estructura detallada de esta capa.

    Estos diagramas se usan para validar el código que se desarrolla en esta capa.

4. En la solución de arquitectura, edite los requisitos y los modelos de diseño de todas las capas con Visual Studio.

    En cada solución de capa, desarrolle el código para esa capa, con referencia al modelo. Si está satisfecho con realizar el desarrollo sin usar el mismo equipo para actualizar el modelo, puede leer el modelo y desarrollar el código con las versiones de Visual Studio con las que no se puede crear modelos. También puede generar código a partir del modelo en estas versiones.

    Este método garantiza que no se produzca ninguna interferencia por parte de los desarrolladores que editen los modelos de capas al mismo tiempo.

    Sin embargo, dado que los modelos son independientes, es difícil hacer referencia a los conceptos comunes. Cada modelo debe tener su propia copia de los elementos en la que sea dependiente de la arquitectura y otras capas. El diagrama de capas de cada capa debe estar sincronizado con el diagrama de capas de la arquitectura. Es difícil mantener la sincronización cuando cambian estos elementos, aunque puede desarrollar herramientas para lograrlo.

###### <a name="to-use-a-separate-package-for-each-layer"></a>Para usar un paquete independiente para cada capa

1. En la solución para cada capa, agregue el proyecto de modelado de arquitectura. In Solution Explorer, right-click the solution node, point to **Add**, and then click **Existing Project**. Ahora, se puede acceder al proyecto de modelado desde cada solución: el proyecto de la arquitectura y el proyecto de desarrollo de cada capa.

2. En el modelo UML compartido, cree un paquete para cada capa: en el Explorador de soluciones, seleccione el proyecto de modelado. In UML Model Explorer, right-click the model root node, point to **Add**, and then click **Package**.

    Cada paquete incluirá diagramas UML que describen los requisitos y el diseño de la capa correspondiente.

3. Si es necesario, agregue los diagramas de capas locales para la estructura interna de cada capa.

    Este método permite que los elementos de diseño de cada capa hagan referencia directamente a los de las capas y la arquitectura común de las que dependen.

    Aunque trabajar simultáneamente en distintos paquetes puede producir algunos conflictos, son bastante fáciles de administrar, ya que los paquetes se almacenan en archivos independientes. La dificultad principal se debe a la eliminación de un elemento al que se hace referencia desde un paquete dependiente. For more information, see [Manage models and diagrams under version control](../modeling/manage-models-and-diagrams-under-version-control.md).

## <a name="creating-architecture-templates"></a>Crear plantillas de arquitectura

En la práctica, no creará todas las soluciones de Visual Studio al mismo tiempo, si no que las agregará conforme avanza el proyecto. Probablemente también use la misma estructura de solución en futuros proyectos.  Para ayudarle a crear rápidamente nuevas soluciones, puede crear una plantilla de proyecto o solución. Puede capturar la plantilla en una extensión de integración de Visual Studio (VSIX) para que sea fácil distribuir e instalar en otros equipos.

Por ejemplo, si usa soluciones que tienen capas de presentación, negocio y datos con frecuencia, puede configurar una plantilla que cree nuevas soluciones con esa estructura.

#### <a name="to-create-a-solution-template"></a>Para crear una plantilla de solución

1. [Download and install the Export Template Wizard](https://go.microsoft.com/fwlink/?LinkId=196686), if you have not already done this.

2. Cree la estructura de solución que quiere usar como punto de partida para proyectos futuros.

3. En el menú **Archivo** , haga clic en **Exportar plantilla como VSIX**. The **Export Template as VSIX Wizard** opens.

4. Siga las instrucciones del asistente, seleccione los proyectos que quiere incluir en la plantilla, proporcione un nombre y una descripción para la plantilla y especifique una ubicación de salida.

> [!NOTE]
> El material de este tema se ha extraído y parafraseado a partir de la guía para las herramientas de arquitectura de Visual Studio, escrita por Visual Studio ALM Rangers, una colaboración entre los profesionales más valorados (MVP), los Servicios de Microsoft y el equipo de producto y los escritores de Visual Studio. [Click here to download the complete Guidance package.](https://go.microsoft.com/fwlink/?LinkID=191984)

## <a name="related-materials"></a>Material relacionado

[Organizing and Managing Your Models](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models) - video by Clint Edmondson.

[Visual Studio Architecture Tooling Guidance](../modeling/visual-studio-architecture-tooling-guidance.md) – Further guidance on managing models in a team

## <a name="see-also"></a>Vea también

[Manage models and diagrams under version control](../modeling/manage-models-and-diagrams-under-version-control.md)
[Use models in your development process](../modeling/use-models-in-your-development-process.md)
