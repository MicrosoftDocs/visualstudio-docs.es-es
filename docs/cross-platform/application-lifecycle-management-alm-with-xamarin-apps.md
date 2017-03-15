---
title: "Administración del ciclo de vida de las aplicaciones (ALM) con aplicaciones de Xamarin | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
caps.latest.revision: 14
author: ghogen
ms.author: ghogen
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: f78e2b713e75c5601a07907e7f717db92571568b
ms.openlocfilehash: 37155aa4767b54a8ff057e96a405c8670a66367e
ms.lasthandoff: 02/22/2017

---
# <a name="application-lifecycle-management-alm-with-xamarin-apps"></a>Administración del ciclo de vida de las aplicaciones (ALM) con aplicaciones de Xamarin
Xamarin le permite crear aplicaciones móviles multiplataforma destinadas a Android, iOS y Windows con C#, .NET y Visual Studio. Xamarin permite compartir entre plataformas gran parte del código. Solo es necesario que un pequeño porcentaje sea específico de la plataforma. Para más información sobre Xamarin, vea [Visual Studio y Xamarin](../cross-platform/visual-studio-and-xamarin.md).  
  
 El desarrollo de aplicaciones para plataformas modernas implica muchas otras actividades, además de escribir código. Estas actividades, denominadas DevOps (desarrollo + operaciones), abarcan el ciclo de vida completo de la aplicación e incluyen la planeación y el seguimiento del trabajo, el diseño y la implementación del código, la administración de un repositorio de código fuente, las compilaciones, la administración de integraciones e implementaciones continuas, las pruebas (incluidas las pruebas unitarias y las pruebas de la interfaz de usuario), la ejecución de diversas formas de diagnóstico tanto en entornos de desarrollo como de producción y la supervisión del rendimiento de la aplicación y del comportamiento de los usuarios en tiempo real mediante telemetría y análisis.  
  
 Visual Studio, Visual Studio Team Services y Team Foundation Server ofrecen una variedad de capacidades de DevOps, también llamada administración del ciclo de vida de las aplicaciones o ALM. Muchas de ellas son aplicables por completo a proyectos multiplataforma.  
  
 Esto es especialmente cierto con las aplicaciones de Xamarin, ya que se compilan con C# y. NET, sobre los que se compilan algunas herramientas de ALM. Otras herramientas requieren una estrecha integración con los entornos de compilación y de tiempo de ejecución. Dado que las aplicaciones Xamarin se ejecutan en plataformas que no son de Windows y usan la implementación Mono de. NET, Xamarin ofrece herramientas especializadas para ciertas necesidades.  
  
 Las siguientes tablas identifican qué características ALM de Visual Studio puede esperar que funcionen bien con un proyecto de Xamarin y cuáles tienen limitaciones. Consulte la documentación vinculada para obtener más información acerca de cada característica.  
  
## <a name="agile-tools"></a>Herramientas de Agile  
 Vínculo de referencia: **[Trabajar](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (con Visual Studio Team Services o TFS, incluido Team Explorer Everywhere)  
  
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
  
 Las características de diseño son independientes del lenguaje de codificación o funcionan con lenguajes .NET como C#. Vea [Roles of Architecture and Modeling Diagrams in Software Development](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools) (Roles de arquitectura y diagramas de modelado en el desarrollo de software) para obtener información sobre los aspectos relacionados con el código.  
  
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
|[Use Team Foundation Version Control (Usar el control de versiones de Team Foundation)](http://msdn.microsoft.com/Library/1d629052-c65d-4c5d-81eb-eaa4413fe285) o Visual Studio Team Services|Sí||  
|[Getting started with Git in Team Services (Introducción a Git en Team Services)](http://msdn.microsoft.com/Library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Sí||  
|[Análisis de código y mejorar la calidad del código (referencias, cambios sugeridos, etc.)](http://msdn.microsoft.com/Library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Sí||  
|[Buscar cambios en el código y otro historial](../ide/find-code-changes-and-other-history-with-codelens.md)|Sí|Excepto en los límites específicos de la plataforma donde la implementación no se resuelve hasta el tiempo de ejecución.|  
|[Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)|Sí||  
  
## <a name="build"></a>Compilar  
 Vínculo de referencia: **[Compilar](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)**  
  
|Característica|Compatible con Xamarin|Comentarios adicionales|  
|-------------|----------------------------|-------------------------|  
|Servidor TFS local|Sí|Los equipos de compilación deben tener instalado Xamarin y se pueden vincular a un equipo OSX para compilar para iOS. Vea [Configuring TFS for Xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (sitio web de Xamarin).|  
|Servidor de compilación local vinculado a Visual Studio Team Services|Sí|Vea [Build server (Servidor de compilación)](http://msdn.microsoft.com/Library/2d258a0a-f178-4e93-9da1-eba61151af3c) para obtener instrucciones.|  
|Servicio de controlador hospedado de Visual Studio Team Services|Sí|Vea [Build your Xamarin app](https://www.visualstudio.com/en-us/docs/build/apps/mobile/xamarin) (Crear su aplicación de Xamarin).|  
|Compilar definiciones con scripts anteriores y posteriores|Sí||  
|Integración continua, incluidas entradas validadas|Sí|Entradas validadas para TFVC solo cuando GIT funciona en un modelo de solicitud de extracción en lugar de entradas.|  
  
## <a name="testing"></a>Pruebas  
 Vínculo de referencia: **[Testing the application (Probar la aplicación)](/devops-test-docs/test/test-apps-early-and-often)**  
  
|Característica|Compatible con Xamarin|Comentarios adicionales|  
|-------------|----------------------------|-------------------------|  
|Planear pruebas, crear casos de prueba y organizar conjuntos de pruebas|Sí||  
|Pruebas manuales|Sí||  
|Administrador de pruebas (grabar y reproducir pruebas)|Sí|Dispositivos Windows y emuladores de Android únicamente de Visual Studio. Con la [Grabadora de pruebas de Xamarin](https://www.xamarin.com/test-cloud/recorder) es posible grabar en todos los dispositivos.|  
|Cobertura de código|no disponible||  
|[Haga una prueba unitaria de su código](../test/unit-test-your-code.md)|Sí|Para destinos Windows y Android, pueden usarse las herramientas integradas de MSTest. Xamarin recomienda NUnit para ejecutar pruebas unitarias en Windows, Android e iOS. Vea [Configuring TFS for Xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (sitio web de Xamarin).|  
|[Usar Automatización de la interfaz de usuario para probar el código](../test/use-ui-automation-to-test-your-code.md)|Solo Windows|La grabadora de pruebas de interfaz de usuario de Visual Studio es solo para Windows. Para todas las plataformas, vea [Grabadora de pruebas de Xamarin](https://www.xamarin.com/test-cloud/recorder).|  
  
## <a name="improve-code-quality"></a>Mejorar la calidad del código  
 Vínculo de referencia: **[Mejorar la calidad del código](http://msdn.microsoft.com/Library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Característica|Compatible con Xamarin|Comentarios adicionales|  
|-------------|----------------------------|-------------------------|  
|[Analizar la calidad del código administrado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Sí||  
|[Buscar código duplicado mediante la detección de clones de código](http://msdn.microsoft.com/Library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Sí||  
|[Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Sí||  
|[Explorador de rendimiento](../profiling/performance-explorer.md)|No|Use [Xamarin Profiler](http://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/) a través de Xamarin Studio en su lugar. Tenga en cuenta que el generador de perfiles de Xamarin está actualmente en vista previa y aún no funciona para destinos de Windows.|  
|[Analizar problemas de memoria de .NET Framework](https://msdn.microsoft.com/en-us/library/dn342825.aspx)|No|Las herramientas de Visual Studio no tienen enlaces al marco de trabajo de Mono para la generación de perfiles.|  
  
## <a name="release-management"></a>Administración de versiones  
 Vínculo de referencia: **[Automate deployments with Release Management (Automatizar implementaciones con Release Management)](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
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
