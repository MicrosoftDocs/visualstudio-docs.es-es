---
title: Estructurar la solución de modelado
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cc4eba7dc4d185cbd8eb4f1b073fce8b0c9fb07e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545046"
---
# <a name="structure-your-modeling-solution"></a>Estructurar la solución de modelado

Para usar eficazmente los modelos en un proyecto de desarrollo, los miembros del equipo deben ser capaces de trabajar en los modelos de diferentes partes del proyecto al mismo tiempo. En este tema, se sugiere un esquema para dividir la aplicación en diferentes partes que corresponden a las capas en un diagrama de capas general.

Para iniciar un proyecto o subproyecto rápidamente, resulta útil disponer de una plantilla de proyecto que siga la estructura del proyecto que ha elegido. En este tema se describe cómo crear y usar este tipo de plantilla.

En este tema se supone que está trabajando en un proyecto que es lo suficientemente grande como para necesitar varios miembros del equipo y que quizás tenga varios equipos. El código y los modelos del proyecto se almacenan en un sistema de control de código fuente como [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Al menos algunos miembros del equipo usan Visual Studio para desarrollar modelos, mientras que otros miembros del equipo pueden ver los modelos con otras versiones de Visual Studio.

Para ver qué versiones de Visual Studio son compatibles con cada herramienta y característica de modelado, vea [compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="solution-structure"></a>Estructura de solución

En un proyecto grande o mediano, la estructura del equipo se basa en la estructura de la aplicación. Cada equipo usa una solución de Visual Studio.

### <a name="to-divide-an-application-into-layers"></a>Para dividir una aplicación en capas

1. Base la estructura de las soluciones en la estructura de la aplicación, como la aplicación web, aplicación de servicio o aplicación de escritorio. En la guía de arquitectura de aplicaciones de Microsoft se describe una variedad de arquitecturas comunes en [la aplicación arquetipos](/previous-versions/msp-n-p/ee658107(v=pandp.10)).

2. Cree una solución de Visual Studio, a la que llamaremos la solución de arquitectura. Esta solución se usará para crear el diseño general del sistema. Contendrá modelos, pero ningún código.

   Agregue un diagrama de dependencia a esta solución. En el diagrama de dependencia, dibuje la arquitectura que ha elegido para la aplicación. Por ejemplo, el diagrama puede mostrar estas capas y las dependencias entre ellas: presentación, lógica de negocios y datos.

4. Cree una solución de Visual Studio independiente para cada capa en el diagrama de dependencias de la arquitectura.

   Estas soluciones se usarán para desarrollar el código de las capas.

5. Cree modelos que representen los diseños de las capas y los conceptos que son comunes a todas las capas. Organice los modelos para que se puedan ver todos desde la solución de arquitectura y para que se puedan ver los modelos relevantes en cada capa.

   Puede conseguirlo mediante cualquiera de los procedimientos siguientes. La primera alternativa crea un proyecto de modelado independiente para cada capa, mientras que la segunda crea un proyecto de modelado que se comparte entre las capas.

#### <a name="use-a-separate-modeling-project-for-each-layer"></a>Usar un proyecto de modelado independiente para cada capa

1. Cree un proyecto de modelado en la solución de cada capa.

   Este modelo contendrá diagramas que describen los requisitos y el diseño de esa capa. También puede contener diagramas de dependencia que muestren capas anidadas.

   Ahora dispone de un modelo para cada capa, además de un modelo para la arquitectura de la aplicación. Cada modelo se encuentra en su propia solución. Esto permite a los miembros del equipo trabajar en las capas al mismo tiempo.

2. Para la solución de arquitectura, agregue el proyecto de modelado de la solución de cada capa. Para ello, abra la solución de arquitectura. En **Explorador de soluciones**, haga clic con el botón secundario en el nodo de la solución, seleccione Agregar y, a continuación, haga clic en **proyecto existente**. Navegue hasta el proyecto de modelado (.modelproj) de una solución de capa.

   Ahora, cada modelo es visible en dos soluciones: la solución "principal" y la solución de arquitectura.

3. Agregue un diagrama de dependencia al proyecto de modelado de cada capa. Comience con una copia del diagrama de dependencias de la arquitectura. Puede eliminar partes que no son dependencias del diagrama de dependencia.

   También puede Agregar diagramas de dependencia que representen la estructura detallada de esta capa.

   Estos diagramas se usan para validar el código que se desarrolla en esta capa.

4. En la solución de arquitectura, edite los requisitos y los modelos de diseño de todas las capas con Visual Studio.

   En cada solución de capa, desarrolle el código para esa capa, con referencia al modelo. Si está satisfecho con realizar el desarrollo sin usar el mismo equipo para actualizar el modelo, puede leer el modelo y desarrollar el código con las versiones de Visual Studio con las que no se puede crear modelos. También puede generar código a partir del modelo en estas versiones.

   Este método garantiza que no se produzca ninguna interferencia por parte de los desarrolladores que editen los modelos de capas al mismo tiempo.

   Sin embargo, dado que los modelos son independientes, es difícil hacer referencia a los conceptos comunes. Cada modelo debe tener su propia copia de los elementos en la que sea dependiente de la arquitectura y otras capas. El diagrama de dependencia de cada capa debe mantenerse sincronizado con el diagrama de dependencia de la arquitectura. Es difícil mantener la sincronización cuando cambian estos elementos, aunque puede desarrollar herramientas para lograrlo.

#### <a name="use-a-separate-package-for-each-layer"></a>Usar un paquete independiente para cada capa

1. En la solución para cada capa, agregue el proyecto de modelado de arquitectura. En **Explorador de soluciones**, haga clic con el botón secundario en el nodo de la solución, seleccione **Agregar**y, a continuación, haga clic en **proyecto existente**. Ahora, se puede acceder al proyecto de modelado desde cada solución: el proyecto de la arquitectura y el proyecto de desarrollo de cada capa.

2. En el modelo compartido, cree un paquete para cada capa: en **Explorador de soluciones**, seleccione el proyecto de modelado. En el **Explorador de modelos UML**, haga clic con el botón secundario en el nodo raíz del modelo, seleccione **Agregar**y, a continuación, haga clic en **paquete**.

   Cada paquete contendrá diagramas que describen los requisitos y el diseño de la capa correspondiente.

3. Si es necesario, agregue diagramas de dependencia locales para la estructura interna de cada capa.

   Este método permite que los elementos de diseño de cada capa hagan referencia directamente a los de las capas y la arquitectura común de las que dependen.

   Aunque trabajar simultáneamente en distintos paquetes puede producir algunos conflictos, son bastante fáciles de administrar, ya que los paquetes se almacenan en archivos independientes.

## <a name="create-architecture-templates"></a>Crear plantillas de arquitectura

En la práctica, no se crean todas las soluciones de Visual Studio al mismo tiempo, sino que se agregan a medida que progresa el proyecto. Probablemente también usará la misma estructura de solución en proyectos futuros. Para ayudarle a crear rápidamente nuevas soluciones, puede crear una plantilla de proyecto o solución. Puede capturar la plantilla en una extensión de integración de Visual Studio (VSIX) para que sea fácil distribuir e instalar en otros equipos.

Por ejemplo, si usa soluciones que tienen capas de presentación, negocio y datos con frecuencia, puede configurar una plantilla que cree nuevas soluciones con esa estructura.

### <a name="to-create-a-solution-template"></a>Para crear una plantilla de solución

1. [Descargue e instale el Asistente para exportar plantillas](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ExportTemplateWizard).

2. Cree la estructura de solución que quiere usar como punto de partida para proyectos futuros.

3. En el menú **Archivo** , haga clic en **Exportar plantilla como VSIX**.

   Se abre el **Asistente para exportar plantillas como VSIX** .

4. Siga las instrucciones del asistente, seleccione los proyectos que quiere incluir en la plantilla, proporcione un nombre y una descripción para la plantilla y especifique una ubicación de salida.

## <a name="watch-a-video"></a>Ver un vídeo

[Organice y administre sus modelos](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models)

## <a name="see-also"></a>Consulte también

- [Usar modelos en el proceso de desarrollo](../modeling/use-models-in-your-development-process.md)
- [Visual Studio Architecture Tooling Guidance](../modeling/visual-studio-architecture-tooling-guidance.md)
