---
title: Administración del ciclo de vida de las aplicaciones (ALM) con aplicaciones de Unity | Microsoft Docs
ms.date: 08/21/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 5a1c449a77e3000205ee81f5414949743b6035c4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "77272266"
---
# <a name="devops-with-unity-apps"></a>DevOps con aplicaciones de Unity

El desarrollo de aplicaciones para plataformas modernas implica muchas otras actividades, además de escribir código. Estas actividades, denominadas DevOps (desarrollo + operaciones), abarcan el ciclo de vida completo de la aplicación e incluyen la planeación y el seguimiento del trabajo, el diseño y la implementación del código, la administración de un repositorio de código fuente, las compilaciones, la administración de integraciones e implementaciones continuas, las pruebas (incluidas las pruebas unitarias y las pruebas de la interfaz de usuario), la ejecución de diversas maneras de diagnóstico tanto en entornos de desarrollo como de producción y la supervisión del rendimiento de la aplicación y del comportamiento de los usuarios en tiempo real mediante telemetría y análisis.

Visual Studio, Azure DevOps Services y Team Foundation Server ofrecen una variedad de funcionalidades de DevOps. Muchas de ellas son aplicables a proyectos de varias plataformas, incluidos los juegos y las aplicaciones gráficas inmersivas creados con Unity, especialmente cuando se usa C# como un lenguaje de scripting. Sin embargo, dado que Unity tiene su propio entorno de desarrollo y motor en tiempo de ejecución, hay una serie de características de DevOps que no se aplican como lo harían en otros tipos de proyectos generados en Visual Studio.

En estas tablas se recogen cómo las características de DevOps en Visual Studio se aplican o no cuando se trabaja con Unity. Consulte la documentación vinculada para obtener más información acerca de cada característica.

## <a name="agile-tools"></a>Herramientas de Agile

Vínculo de referencia: [About Agile tools and Agile project management](/azure/devops/boards/backlogs/backlogs-overview?view=vsts) (Información sobre las herramientas y la administración de proyectos en Agile) con Azure Boards o TFS, incluido Team Explorer Everywhere

Comentario general: todas las características de planeación y seguimiento son independientes del tipo de proyecto y de los lenguajes de codificación.

|Característica|Compatible con Unity|Comentarios adicionales|
|-------------|--------------------------|-------------------------|
|Administrar trabajos pendientes y sprints|Sí||
|Seguimiento del trabajo|Sí||
|Colaboración en la sala de reuniones del equipo|Sí||
|Paneles Kanban|Sí||
|Notificar y visualizar el progreso|Sí||

## <a name="modeling"></a>Modelado

Vínculo de referencia: **[Analizar y modelar la arquitectura](../modeling/analyze-and-model-your-architecture.md)**

Comentario general: aunque estas características de diseño son independientes del lenguaje de codificación o funcionan con lenguajes .NET como C#, operan en un paradigma de aplicaciones tradicional con jerarquías de objetos y relaciones de clases. Diseñar un juego en Unity implica todo un paradigma diferente, como por ejemplo, relaciones de objetos gráficos, sonidos, sombreadores y scripts. Por este motivo, las herramientas del diagrama de modelado de Visual Studio no son especialmente relevantes para la totalidad de un proyecto de Unity. Posiblemente se podrían usar para administrar las relaciones entre scripts C#, pero eso es solo una parte del conjunto.

|Característica|Compatible con Unity|Comentarios adicionales|
|-------------|--------------------------|-------------------------|
|Diagramas de secuencia|No||
|Gráficos de dependencia|No||
|Jerarquía de llamadas|No||
|Diseñador de clases|No||
|Explorador de arquitectura|No||
|Diagramas UML (caso de uso, actividad, clase, componente, secuencia y DSL)|No||
|Diagramas de capas|No||
|Validación de capas|No||

## <a name="code"></a>Código

|Característica|Compatible con Unity|Comentarios adicionales|
|-------------|--------------------------|-------------------------|
|[Uso del control de versiones de Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts) o Azure Repos.|Sí|Los proyectos de Unity son simplemente una colección de archivos que se pueden colocar en sistemas de control de versiones como cualquier otro proyecto, pero después de esta tabla se describen algunas consideraciones especiales.|
|[Introducción a Git en Azure Repos](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio)|Sí|Vea las notas después de la tabla.|
|[Mejorar la calidad del código](../test/improve-code-quality.md)|Sí||
|[Buscar cambios en el código y otro historial](../ide/find-code-changes-and-other-history-with-codelens.md)|Sí||
|[Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)|Sí||

Consideraciones especiales para el control de versiones con Unity:

1. Unity hace un seguimiento de los metadatos sobre los activos de juego en una única biblioteca opaca que está oculta de forma predeterminada. Para mantener sincronizados los archivos y metadatos, es necesario hacer visibles los metadatos y almacenarlos en fragmentos más fáciles de manejar. Para más detalles, vea [Using External Version Control Systems with Unity](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (Uso de sistemas externos de control de versiones con Unity, documentación de Unity).

2. No todos los archivos y carpetas de un proyecto de Unity son adecuados para el control de código fuente, tal y como se describe también en el tema anterior. Deben agregarse las carpetas Assets y ProjectSettings, pero no las carpetas Library y Temp. Para obtener una lista adicional de archivos generados que no sean adecuados para el control de código fuente, vea la explicación sobre [cómo usar Git para el control de código fuente en Unity3D](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) de StackOverflow. Muchos desarrolladores también han escrito sobre este tema de forma independiente.

3. Los activos binarios de un proyecto de Unity, como las texturas o los archivos de audio, pueden ocupar una gran cantidad de almacenamiento. Varios sistemas de control de código fuente como Git almacenan una única copia de un archivo por cada cambio realizado, incluso si el cambio afecta solo a una pequeña parte del archivo. Esto puede hacer que el repositorio Git se infle. Para solucionar este problema, los desarrolladores de Unity a menudo optan por agregar solo los activos finales al repositorio y usar varios métodos para mantener un historial de trabajo de sus activos, como OneDrive, DropBox o git-annex. Este enfoque funciona porque normalmente no es necesario crear versiones de dichos activos conforme se realizan cambios en el código fuente. Los desarrolladores también suelen establecer el modo de serialización de activos del editor del proyecto en Forzar texto para almacenar archivos de escenas como texto en lugar de hacerlo en formato binario, lo que permite hacer combinaciones en el control de código fuente. Para más detalles, vea [Editor Settings](https://docs.unity3d.com/Manual/class-EditorManager.html) (Configuración del editor, documentación de Unity).

## <a name="build"></a>Compilar

Vínculo de referencia: **[Azure Pipelines](/azure/devops/pipelines/index?view=vsts)**

|Característica|Compatible con Unity|Comentarios adicionales|
|-------------|--------------------------|-------------------------|
|Team Foundation Server (TFS) local|Posibilidad|Los proyectos de Unity se compilan a través del entorno de Unity y no a través del sistema de compilación de Visual Studio (la compilación de Visual Studio Tools para Unity compilará los scripts, pero no generará un archivo ejecutable). Es posible [compilar proyectos de Unity desde la línea de comandos](https://docs.unity3d.com/Manual/CommandLineArguments.html) (documentación de Unity), por lo que se puede configurar un proceso de MSBuild en un servidor TFS para ejecutar los comandos de Unity correspondientes siempre que Unity esté instalado en el equipo.<br /><br /> Unity también ofrece [Unity Cloud Build (Compilación en la nube de Unity)](https://build.cloud.unity3d.com/landing/), que supervisa un repositorio Git o SVN, y ejecuta compilaciones de forma periódica. Actualmente, no funciona con TFVC ni Azure DevOps Services.|
|Servidor de compilación local vinculado a Azure DevOps Services|Posibilidad|En las mismas condiciones anteriores, también es posible dirigir compilaciones desencadenadas a través de Azure DevOps Services para usar un equipo TFS local. Vea [Build and release agents](/azure/devops/pipelines/agents/agents?view=vsts) (Agentes de compilación y versiones) para obtener instrucciones.|
|Servicio de controlador hospedado de Azure DevOps Services|No|Actualmente no se admiten las compilaciones de Unity.|
|Compilar definiciones con scripts anteriores y posteriores|Sí|También se puede configurar una definición de compilación personalizada que use la línea de comandos de Unity para ejecutar una compilación en el caso de los scripts previos y posteriores a la compilación.|
|Integración continua, incluidas entradas validadas|Sí|Entradas validadas para TFVC solo cuando GIT funciona en un modelo de solicitud de extracción en lugar de entradas.|

## <a name="test"></a>Prueba

|Característica|Compatible con Unity|Comentarios adicionales|
|-------------|--------------------------|-------------------------|
|Planear pruebas, crear casos de prueba y organizar conjuntos de pruebas|Sí||
|Pruebas manuales|Sí||
|Administrador de pruebas (grabar y reproducir pruebas)|Dispositivos Windows y emuladores de Android únicamente||
|Cobertura de código|no disponible|No aplicable, ya que las pruebas unitarias tienen lugar en Unity y no en Visual Studio, vea más adelante.|
|[Haga una prueba unitaria de su código](../test/unit-test-your-code.md)|En Unity, pero no en Visual Studio|Unity proporciona su propio marco de pruebas unitarias como parte de [Unity Test Tools](https://www.assetstore.unity3d.com/en/#!/content/13802) (Tienda de recursos de Unity). Los resultados de las pruebas unitarias se notifican en Unity y no aparecen en Visual Studio.|
|[Usar la automatización de la interfaz de usuario para probar el código](../test/use-ui-automation-to-test-your-code.md)|No|Las pruebas de interfaz de usuario codificadas se basan en controles legibles de la interfaz de usuario de la aplicación; las aplicaciones de Unity son gráficas por naturaleza y, por tanto, las herramientas de pruebas de interfaz de usuario codificadas no pueden leer el contenido.|

## <a name="improve-code-quality"></a>Mejorar la calidad del código

Vínculo de referencia: **[Mejorar la calidad del código](../test/improve-code-quality.md)**

|Característica|Compatible con Unity|Comentarios adicionales|
|-------------|--------------------------|-------------------------|
|[Analizar la calidad del código administrado](../code-quality/code-analysis-for-managed-code-overview.md)|Sí|Se puede analizar el código de script de C# en Visual Studio.|
|[Buscar código duplicado mediante la detección de clones de código](https://msdn.microsoft.com/library/hh205279.aspx)|Sí|Se puede analizar el código de script de C# en Visual Studio.|
|[Medir la complejidad y el mantenimiento del código administrado](../code-quality/code-metrics-values.md)|Sí|Se puede analizar el código de script de C# en Visual Studio.|
|[Herramientas de rendimiento](../profiling/performance-explorer.md)|No|Use el [generador de perfiles de Unity](https://docs.unity3d.com/Manual/Profiler.html) (sitio web de Unity).|
|[Analizar problemas de memoria de .NET Framework](https://msdn.microsoft.com/library/dn342825.aspx)|No|Las herramientas de Visual Studio no tienen enlaces al marco de trabajo de Mono (usado por Unity) para la generación de perfiles. Use el [generador de perfiles de Unity](http://docs.unity3d.com/Manual/Profiler.html) (documentación de Unity).|

## <a name="release-management"></a>Administración de versiones

Vínculo de referencia: [Compilación y versiones en Azure Pipelines y TFS](/azure/devops/pipelines/overview?view=vsts)

|Característica|Compatible con Unity|Comentarios adicionales|
|-------------|--------------------------|-------------------------|
|Administrar procesos de versión|Sí||
|Implementar en servidores para la instalación de prueba mediante scripts|Sí||
|Cargar a la tienda de aplicaciones|Partial|Hay extensiones disponibles que pueden automatizar este proceso para algunas tiendas de aplicaciones. Vea [Extensions for Azure DevOps Services](https://marketplace.visualstudio.com/VSTS) (Extensiones para Azure DevOps Services); por ejemplo, la [extensión para Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>Supervisión con HockeyApp

Vínculo de referencia: **[Supervisión con HockeyApp](https://www.hockeyapp.net/features/)**

|Característica|Compatible con Unity|Comentarios adicionales|
|-------------|--------------------------|-------------------------|
|Análisis de bloqueo, telemetría y distribución beta|Sí|HockeyApp es principalmente útil para controlar la distribución beta y la obtención de informes de bloqueo.<br /><br /> Para la telemetría de scripts de C#, se puede usar cualquier marco de análisis siempre que se ejecute en la versión de .NET que usa Unity. Sin embargo, esto permite la realización de análisis solo para scripts de juegos, pero no con mayor profundidad en el motor de Unity. En este momento no hay ningún complemento para Application Insights, pero hay complementos disponibles para otras soluciones de análisis como [Unity Analytics](https://www.assetstore.unity3d.com/en/#!/content/28120) y [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity). Los servicios como Analytics Unity, que entiende la naturaleza de un proyecto de Unity, podrán, por supuesto, proporcionar análisis mucho más significativos que los marcos de trabajo genéricos.|
