---
title: Administración del ciclo de vida de las aplicaciones (ALM) con aplicaciones de Xamarin | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: b711c6c67eb7466d642048f2546c532b9b2e2926
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231861"
---
# <a name="application-lifecycle-management-alm-with-xamarin-apps"></a>Administración del ciclo de vida de las aplicaciones (ALM) con aplicaciones de Xamarin

Xamarin le permite crear aplicaciones móviles multiplataforma destinadas a Android, iOS y Windows con C#, .NET y Visual Studio. Xamarin permite compartir entre plataformas gran parte del código. Solo es necesario que un pequeño porcentaje sea específico de la plataforma. Para más información sobre Xamarin, vea [Visual Studio y Xamarin](../cross-platform/visual-studio-and-xamarin.md).

El desarrollo de aplicaciones para plataformas modernas implica muchas otras actividades, además de escribir código. Estas actividades, denominadas DevOps (desarrollo + operaciones), abarcan el ciclo de vida completo de la aplicación e incluyen la planeación y el seguimiento del trabajo, el diseño y la implementación del código, la administración de un repositorio de código fuente, las compilaciones, la administración de integraciones e implementaciones continuas, las pruebas (incluidas las pruebas unitarias y las pruebas de la interfaz de usuario), la ejecución de diversas maneras de diagnóstico tanto en entornos de desarrollo como de producción y la supervisión del rendimiento de la aplicación y del comportamiento de los usuarios en tiempo real mediante telemetría y análisis.

Visual Studio, Visual Studio Team Services y Team Foundation Server ofrecen una variedad de capacidades de DevOps, también llamada administración del ciclo de vida de las aplicaciones o ALM. Muchas de ellas son aplicables por completo a proyectos multiplataforma.

Esto es especialmente cierto con las aplicaciones de Xamarin, ya que se compilan con C# y. NET, sobre los que se compilan algunas herramientas de ALM. Otras herramientas requieren una estrecha integración con los entornos de compilación y de tiempo de ejecución. Dado que las aplicaciones Xamarin se ejecutan en plataformas que no son de Windows y usan la implementación Mono de. NET, Xamarin ofrece herramientas especializadas para ciertas necesidades.

Las siguientes tablas identifican qué características ALM de Visual Studio puede esperar que funcionen bien con un proyecto de Xamarin y cuáles tienen limitaciones. Consulte la documentación vinculada para obtener más información acerca de cada característica.

## <a name="agile-tools"></a>Herramientas de Agile

Vínculo de referencia: **[About Agile tools and Agile project management](/vsts/work/backlogs/overview?view=vsts)** (Sobre herramientas y gestión de proyectos de Agile)

Comentario general: todas las características de planeación y seguimiento son independientes del tipo de proyecto y de los lenguajes de codificación.

|Característica|Compatible con Xamarin|Comentarios adicionales|
|-------------|----------------------------|-------------------------|
|Administrar trabajos pendientes y sprints|Sí||
|Seguimiento del trabajo|Sí||
|Colaboración en la sala de reuniones del equipo|Sí||
|Paneles Kanban|Sí||
|Notificar y visualizar el progreso|Sí||

## <a name="modeling"></a>Modelado

Vínculo de referencia: **[Analizar y modelar la arquitectura](../modeling/analyze-and-model-your-architecture.md)**

Las características de diseño son independientes del lenguaje de codificación o funcionan con lenguajes .NET como C#. Vea [Roles de arquitectura y diagramas de modelado en el desarrollo de software](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools) para obtener información sobre los aspectos relacionados con el código.

|Característica|Compatible con Xamarin|Comentarios adicionales|
|-------------|----------------------------|-------------------------|
|Diagramas de secuencia|Sí||
|Gráficos de dependencia|Sí||
|Jerarquía de llamadas|Sí||
|Diseñador de clases|Sí||
|Explorador de arquitectura|Sí||
|Diagramas UML (caso de uso, actividad, clase, componente, secuencia y DSL)|Sí||
|Diagramas de capas|Sí||
|Validación de capas|Sí||

## <a name="code"></a>Código

|Característica|Compatible con Xamarin|Comentarios adicionales|
|-------------|----------------------------|-------------------------|
|[Use Team Foundation Version Control (Usar el control de versiones de Team Foundation)](/vsts/tfvc/overview?view=vsts) o Visual Studio Team Services|Sí||
|[Getting started with Git in Team Services (Introducción a Git en Team Services)](/vsts/git/gitquickstart?view=vsts&tabs=visual-studio)|Sí||
|[Mejorar la calidad del código](../test/improve-code-quality.md)|Sí||
|[Buscar cambios en el código y otro historial](../ide/find-code-changes-and-other-history-with-codelens.md)|Sí|Excepto en los límites específicos de la plataforma donde la implementación no se resuelve hasta el tiempo de ejecución.|
|[Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)|Sí||

## <a name="build"></a>Compilar

Vínculo de referencia: **[Compilación y versión](/vsts/pipelines/index?view=vsts)**

|Característica|Compatible con Xamarin|Comentarios adicionales|
|-------------|----------------------------|-------------------------|
|Servidor TFS local|Sí|Los equipos de compilación deben tener instalado Xamarin y se pueden vincular a un equipo OSX para compilar para iOS. Vea [Usar TFVC](/vsts/tfvc/overview?view=vsts).|
|Servidor de compilación local vinculado a Visual Studio Team Services|Sí|Vea [Build and release agents](/vsts/pipelines/agents/agents?view=vsts) (Agentes de compilación y versiones) para obtener instrucciones.|
|Servicio de controlador hospedado de Visual Studio Team Services|Sí|Vea [Build your Xamarin app](/vsts/pipelines/apps/mobile/xamarin?view=vsts&tabs=vsts) (Crear su aplicación de Xamarin).|
|Compilar definiciones con scripts anteriores y posteriores|Sí||
|Integración continua, incluidas entradas validadas|Sí|Entradas validadas para TFVC solo cuando GIT funciona en un modelo de solicitud de extracción en lugar de entradas.|

## <a name="test"></a>Prueba

|Característica|Compatible con Xamarin|Comentarios adicionales|
|-------------|----------------------------|-------------------------|
|Planear pruebas, crear casos de prueba y organizar conjuntos de pruebas|Sí||
|Pruebas manuales|Sí||
|Administrador de pruebas (grabar y reproducir pruebas)|Sí|Dispositivos Windows y emuladores de Android únicamente de Visual Studio. Con la [Grabadora de pruebas de Xamarin](/appcenter/test-cloud/uitest/) es posible grabar en todos los dispositivos.|
|Cobertura de código|N/D||
|[Haga una prueba unitaria de su código](../test/unit-test-your-code.md)|Sí|Para destinos Windows y Android, pueden usarse las herramientas integradas de MSTest. Xamarin recomienda NUnit para ejecutar pruebas unitarias en Windows, Android e iOS. Vea [Usar TFVC](/vsts/tfvc/overview?view=vsts).|
|[Usar la automatización de la interfaz de usuario para probar el código](../test/use-ui-automation-to-test-your-code.md)|Solo Windows|La grabadora de pruebas de interfaz de usuario de Visual Studio es solo para Windows. Para todas las plataformas, vea [Xamarin.UITest](/appcenter/test-cloud/uitest/).|

## <a name="improve-code-quality"></a>Mejorar la calidad del código

Vínculo de referencia: **[Mejorar la calidad del código](../test/improve-code-quality.md)**

|Característica|Compatible con Xamarin|Comentarios adicionales|
|-------------|----------------------------|-------------------------|
|[Analizar la calidad del código administrado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Sí||
|[Buscar código duplicado mediante la detección de clones de código](http://msdn.microsoft.com/Library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Sí||
|[Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Sí||
|[Explorador de rendimiento](../profiling/performance-explorer.md)|No|Use [Xamarin Profiler](/xamarin/cross-platform/deploy-test/) a través de Xamarin Studio en su lugar. Tenga en cuenta que el generador de perfiles de Xamarin está actualmente en vista previa y aún no funciona para destinos de Windows.|
|[Analizar problemas de memoria de .NET Framework](https://msdn.microsoft.com/en-us/library/dn342825.aspx)|No|Las herramientas de Visual Studio no tienen enlaces al marco de trabajo de Mono para la generación de perfiles.|

## <a name="release-management"></a>Administración de versiones

Vínculo de referencia: **[Build and Release in VSTS and TFS](/vsts/pipelines/overview?view=vsts)** (Compilación y versiones en VSTS y TFS)

|Característica|Compatible con Xamarin|Comentarios adicionales|
|-------------|----------------------------|-------------------------|
|Administrar procesos de versión|Sí||
|Implementar en servidores para la instalación de prueba mediante scripts|Sí||
|Cargar a la tienda de aplicaciones|Parcial|Hay extensiones disponibles que pueden automatizar este proceso para algunas tiendas de aplicaciones.  Vea [Extensions for Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS) (Extensiones para Visual Studio Team Services); por ejemplo, la [extensión para Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>Supervisión con HockeyApp

Vínculo de referencia: **[Supervisión con HockeyApp](https://www.hockeyapp.net/features/)**

|Característica|Compatible con Xamarin|Comentarios adicionales|
|-------------|----------------------------|-------------------------|
|Análisis de bloqueo, telemetría y distribución beta|Sí||