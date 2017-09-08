---
title: Novedades de Visual Studio 2017 | Microsoft Docs
ms.custom: 
ms.date: 08/22/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 3cd705d703b3d745c502290422e29b3c6da39ee5
ms.openlocfilehash: 5bf00b7e5ed79f8679b837d0dcabf03550d2b849
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

---
# <a name="what39s-new-in-visual-studio-2017"></a>Novedades de Visual Studio 2017
#### <a name="updated-for-the-153-release"></a>Actualizado para la versión 15.3
Productividad incomparable para cualquier desarrollador, aplicación y plataforma. Use Visual Studio 2017 para desarrollar aplicaciones para Android, iOS, Windows, Linux, la Web y la nube. Escriba código con rapidez, depure y emita diagnósticos con facilidad, ejecute pruebas con frecuencia y publique con confianza. También puede ampliar y personalizar Visual Studio si crea sus propias extensiones. Use el control de versiones, actúe con agilidad y colabore de manera eficiente con esta versión.

Aquí se muestra un resumen de alto nivel de los cambios que hemos realizado:

* **Redefinición de los aspectos básicos**. Una nueva experiencia de instalación significa que puede instalar más rápidamente e instalar lo que desee cuando lo necesite. Si quiere cargar grandes proyectos y soluciones o trabajar con carpetas de código, o incluso un solo archivo de código, Visual Studio se inicia más rápido. Y Visual Studio le ayuda a centrarse en el panorama general, especialmente en el caso de los equipos que están adoptando DevOps.
* **Rendimiento y productividad**. Nos hemos centrado en nuevas y modernas funciones de desarrollo de escritorio, en la nube y móviles. Asimismo, también hemos mejorado las experiencias de productividad del desarrollador general, el rendimiento y la adquisición general. Visual Studio se inicia más rápido, tiene mejor capacidad de respuesta y utiliza menos memoria que antes.
* **Desarrollo de aplicaciones en la nube con Azure**. Se trata de un conjunto integrado de herramientas de Azure que le permite crear con facilidad aplicaciones principalmente destinadas a la nube con la tecnología de Microsoft Azure. Visual Studio facilita la configuración, la compilación, la depuración, el empaquetado y la implementación de aplicaciones y servicios en Azure.
* **Desarrollo de aplicaciones móviles**. En Visual Studio de 2017, puede innovar y obtener resultados rápidamente con Xamarin, que unifica los requisitos móviles multiplataforma mediante el uso de un código base principal y un conjunto de aptitudes. Pásese a la tecnología móvil con los equipos existentes, las inversiones en tecnología y el código de C# para proporcionar experiencias de nivel consumidor antes de lo previsto y con un coste menor al esperado. Acelere cada paso del ciclo de vida móvil para ofrecer experiencias de consumidor de primera clase o una cartera de aplicaciones de productividad para capacitar a sus empleados.
* **Desarrollo multiplataforma** Distribuya software en cualquier plataforma de destino sin problemas. Extienda los procesos de DevOps a SQL Server por medio de Redgate Data Tools y automatice con seguridad las implementaciones de base de datos desde Visual Studio. Desarrolle y presente juegos multiplataforma con Visual Studio Tools para Unity. O use .NET Core para escribir aplicaciones y bibliotecas que se ejecuten sin modificarse en sistemas operativos Windows, Linux y macOS. Y, además, una novedad de la versión 15.3: la compatibilidad en paralelo con los SDK de .NET Core 2.0.

> [!NOTE]
> Para obtener una lista completa de las nuevas funciones y características en Visual Studio 2017, vea las [Notas de la versión](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).

Aquí se muestra información más detallada sobre algunas de las mejoras más destacables y las nuevas características de Visual Studio 2017.

## <a name="redefined-fundamentals"></a>Redefinición de los aspectos básicos
### <a name="a-new-setup-experience"></a>Una nueva experiencia de instalación

[Descargue Visual Studio 2017 ](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) o [vea los requisitos de sistema de Visual Studio](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs).

 Visual Studio acelera y facilita la instalación de simplemente las características que necesita, y justo cuando las necesita. Y, además, se desinstala sin errores.

 El cambio más importante que verá cuando instale Visual Studio es su nueva experiencia de instalación. En la pestaña **Cargas de trabajo**, verá opciones de instalación que se agrupan para representar marcos, lenguajes y plataformas comunes. Abarca todo, desde el desarrollo de escritorio de .NET hasta el desarrollo de aplicaciones de C++ en Windows, Linux y iOS.

Seleccione las cargas de trabajo que requiere y cámbielas cuando sea necesario.

 ![Cuadro de diálogo de instalación de Visual Studio 2017](../install/media/install-visual-studio-enterprise.png "Pantalla del programa de instalación de Visual Studio de 2017")

¿Quiere seleccionar sus propios componentes en lugar de usar cargas de trabajo? Seleccione la pestaña **Componentes individuales** del instalador. ¿Quiere instalar paquetes de idioma sin tener que cambiar la opción de idioma de Windows? Pulse la pestaña **Paquetes de idioma** del instalador.  

Para obtener más información sobre la nueva experiencia de instalación, incluidas instrucciones paso a paso para guiarle, vea nuestra página [Instalación de Visual Studio](../install/install-visual-studio.md).

## <a name="performance-and-productivity"></a>Rendimiento y productividad
### <a name="sign-in-across-multiple-accounts"></a>Iniciar sesión en varias cuentas  
Presentamos un nuevo servicio de identidad en Visual Studio que le permite compartir cuentas de usuario en Team Explorer, Azure Tools, publicar contenido en la Tienda Windows y mucho más.

También puede permanecer más tiempo con la sesión abierta. Visual Studio no le pedirá que vuelva a iniciar sesión cada 12 horas. Para obtener más información, vea la publicación del blog [Fewer Visual Studio Sign-in Prompts](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/) (Menos mensajes emergentes de inicio de sesión en Visual Studio).

### <a name="start-visual-studio-faster"></a>Iniciar Visual Studio más rápido
El nuevo Centro de rendimiento de Visual Studio puede ayudarle a optimizar el tiempo necesario para iniciar el IDE. El Centro de rendimiento muestra todas las extensiones y ventanas de herramientas que pueden estar ralentizando el inicio del IDE. Puede usarlo para mejorar el rendimiento de inicio determinando cuándo se inician las extensiones o si las ventanas de herramientas están abiertas en el inicio.

### <a name="decrease-solution-load-time"></a>Disminuir el tiempo de carga de la solución
El hecho de trabajar en soluciones que contienen un gran número de proyectos no significa que necesite hacerlo en todos los archivos o proyectos a la vez. Ahora, puede editar y depurar sin esperar a que Visual Studio cargue cada proyecto. Para probar esto en proyectos administrados, active la **Carga de solución ligera** desde Herramientas > Opciones > Proyectos y soluciones.

  ![Cuadro de diálogo Opciones en Visual Studio 2017](../ide/media/vs2017ide-lightweight-solution-load.png "Visual Studio 2017 - Cuadro de diálogo Opciones - Carga de solución ligera para todas las soluciones")

### <a name="faster-on-demand-loading-of-extensions"></a>Carga de extensiones a petición más rápida
Visual Studio moverá sus extensiones (y también trabajará con extensiones de terceros) para que se carguen bajo demanda, en lugar de en el momento de inicio del IDE. ¿Tiene curiosidad por saber qué extensiones afectan al inicio, la carga de la solución y el rendimiento de escritura? Puede ver esta información en Ayuda -> Administrar el rendimiento de Visual Studio.

  ![Cuadro de diálogo Opciones en Visual Studio 2017](../ide/media/vs2017ide-manage-vs-perf.png "Cuadro de diálogo Ayuda de Visual Studio- Administración del rendimiento")

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Administrar las extensiones con Roaming Extension Manager
Ahora es más sencillo configurar cada entorno de desarrollo con sus extensiones favoritas cuando inicie sesión en Visual Studio. El nuevo Roaming Extension Manager mantiene el seguimiento de todas sus extensiones favoritas mediante la creación de una lista sincronizada en la nube.  

Para ver una lista de las extensiones de Visual Studio, haga clic en Herramientas > Extensiones y actualizaciones y, después, haga clic en Roaming Extension Manager.

![Visual Studio 2017 - Cuadro de diálogo Extensiones y actualizaciones](../ide/media/vs2017ide-extensions-and-updates.png "Visual Studio 2017 - Herramientas > Cuadro de diálogo Extensiones y actualizaciones")

Roaming Extension Manager realiza un seguimiento de todas las extensiones que instale, pero puede decidir las que quiere agregar a la lista de itinerancia.

![Visual Studio 2017 - Cuadro de diálogo Extensiones y actualizaciones](../ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 - Roaming Extension Manager")

Cuando use Roaming Extension Manager, verá tres tipos de icono en la lista:
* ![Icono de extensión con perfil itinerante](../ide/media/vs2017ide-roamedicon.png "Icono de extensión con perfil itinerante") ***Extensión con perfil itinerante***: una extensión que forma parte de esta lista de itinerancia, pero que no está instalada en el equipo.
  (Puede instalarlas mediante el botón **Descargar**).
* ![Icono de extensión con perfil itinerante e instalada](../ide/media/vs2017ide-roamedinstalledicon.png "Icono de extensión con perfil itinerante e instalada") ***Extensión con perfil itinerante e instalada***: todas las extensiones que forman parte de la lista de itinerancia y que están instaladas en su entorno de desarrollo.
  (Si decide que no quiere usar un perfil itinerante, puede quitarlas mediante el botón **Detener itinerancia**).
* ![Icono de extensión instalada](../ide/media/vs2017ide-installedicon.png "Icono de extensión instalada") ***Extensión instalada***: todas las extensiones que están instaladas en este entorno pero no forman parte de la lista Itinerancia.
  (Puede agregar extensiones a la lista de itinerancia mediante el botón **Iniciar itinerancia**).

Cualquier extensión que descargue mientras tenga la sesión iniciada se agrega a la lista como **Extensión con perfil itinerante e instalada** y forma parte de la lista de itinerancia, con lo cual puede acceder a ella desde cualquier equipo.

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>Experimentar la validación en tiempo real de dependencias de arquitectura y Live Unit Testing
A medida que escriba código en el Editor de código, Visual Studio le notificará en tiempo real las infracciones de reglas de dependencias de arquitectura mediante los diagramas de Validación de dependencia (conocidos también como Diagramas de capas).

Los errores aparecen en la Lista de errores, y los subrayados ondulados aparecen en el editor de texto. Esto le permitirá conocer la ubicación exacta de la infracción. Ahora es menos probable introducir dependencias no deseadas.

![Validación dinámica de arquitectura](../ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "Validación dinámica de arquitectura")

#### <a name="live-unit-testing"></a>Live Unit Testing
En Visual Studio Enterprise de 2017, Live Unit Testing le ofrece los resultados de las pruebas unitarias y la cobertura de código en el editor al tiempo que codifica. Funciona con proyectos de C# y Visual Basic para .NET Framework y .NET Core, y admite tres marcos de prueba de MSTest, xUnit y NUnit.

![Live Unit Testing](../ide/media/lut-codewindow.png "Ejemplo de nuestra nueva característica Live Unit Testing en la edición Enterprise de Visual Studio")

Para más información, vea la entrada de blog [Live Unit Testing in Visual Studio 2017 Enterprise](https://blogs.msdn.microsoft.com/visualstudio/2017/03/09/live-unit-testing-in-visual-studio-2017-enterprise/) (Live Unit Testing en Visual Studio 2017 Enterprise).

#### <a name="set-up-a-cicd-pipeline-to-run-automated-tests-efficiently"></a>Configuración de canalizaciones CI/CD para ejecutar pruebas automatizadas de manera eficaz
Las pruebas automatizadas son una parte fundamental de cualquier canalización de DevOps. Le permiten probar y presentar su solución de manera coherente y confiable en ciclos mucho más cortos. Los flujos de CI/CD (integración continua y entrega continua) pueden ayudarle a hacer que el proceso sea más eficaz.

Para más información sobre las pruebas automatizadas, vea la publicación del blog [CI/CD pipeline for automated tests in DevOps](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/) (Canalización de CI/CD para pruebas automatizadas en DevOps).

Para más información sobre las novedades de la extensión de DevLabs de [Continuous Delivery Tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) (Herramientas de entrega continua para Visual Studio), vea la entrada de blog [Committing with Confidence: Commit Time Code Quality](https://blogs.msdn.microsoft.com/visualstudio/2017/08/21/committing-with-confidence-commit-time-code-quality-information-updated/) (Confirmar con confianza: calidad del código de tiempo de confirmación).

### <a name="a-focus-on-accessibility"></a>Hacer hincapié en la accesibilidad
En la versión 15.3, hemos realizado más de 1700 correcciones de destino para mejorar la compatibilidad entre Visual Studio y las tecnologías de asistencia que muchos de nuestros clientes usan. Existen docenas de escenarios que son más compatibles que nunca con lectores de pantalla, temas de alto contraste y otras tecnologías de ayuda. El depurador, el editor y el shell también se han mejorado considerablemente.

Para más información, vea la entrada de blog [Accessibility improvements in Visual Studio 2017 version 15.3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) (Mejoras de accesibilidad en Visual Studio 2017 versión 15.3).

### <a name="visual-studio-ide-enhancements"></a>Mejoras del IDE de Visual Studio
#### <a name="use-new-refactorings"></a>Uso de nuevas refactorizaciones
En la versión 15.3, hemos agregado una serie de nuevas refactorizaciones:
*   Resolver conflictos de combinación
*   Agregar un parámetro (desde CallSite)
*   Generar invalidaciones
*   Agregar un argumento con nombre
*   Agregar comprobación de NULL para los parámetros
*   Insertar separadores de dígitos en literales
*   Cambiar base de literales numéricos (por ejemplo, hexadecimal a binario)
*   Convertir instrucciones if-to-switch
*   Quitar variables no usadas

Para obtener más información, vea la página [Refactorización, generación de código y acciones rápidas en Visual Studio](refactoring-code-generation-quick-actions.md).


#### <a name="interact-with-git"></a>Interacción con GIT
Cuando se trabaja con un proyecto en Visual Studio, puede configurar y rápidamente confirmar y publicar el código en un servicio de GIT. También puede administrar sus repositorios de GIT por medio de clics de menú con los botones de la esquina inferior derecha del IDE.

![Visual Studio 2017 interactúa con el cuadro de diálogo de GIT](../ide/media/vsIDE-GitInteraction.png "Herramientas de GIT en el IDE de Visual Studio")

#### <a name="view-and-navigate-code-with-structure-visualizer"></a>Visualización del código y navegación con el Visualizador de estructura
El Visualizador de estructura dibuja líneas de guía de estructura (también conocidas como guías de sangría) en el código. Puede usarlas para visualizar y descubrir en qué bloque de código se encuentra en cualquier momento sin tener que desplazarse. Al mantener el mouse en las líneas aparece la información sobre herramientas que le permite ver la apertura de ese bloque y sus elementos primarios. Está disponible para todos los lenguajes admitidos a través de las gramáticas de TextMate, así como C#, Visual Basic y XAML.

![Visualizador de estructura de Visual Studio 2017](../ide/media/vsIDE-StructureVisualizer.png "Visualizador de estructura en Visual Studio")

#### <a name="experience-improved-navigation-controls"></a>Experiencia de controles de navegación mejorada
Se ha actualizado la experiencia de navegación para ayudarle a llegar de A a B con mayor confianza y menos distracciones.

* **Ir a** (Ctrl + F12) &ndash; navegue desde cualquier tipo base o miembro a sus diversas implementaciones.

* **Ir a todo** (Ctrl + T o Ctrl +,) &ndash; navegue directamente a cualquier declaración de archivo/tipo/miembro/símbolo. Puede filtrar la lista de resultados o usar la sintaxis de consulta (por ejemplo, "f searchTerm" para los archivos, "t searchTerm" para los tipos, etc.).

 ![Ir a todo mejorado](../ide/media/vs2017ide-navigation-go-to.png "Ejemplo de la función mejorada de Ir a todo")

* **Buscar todas las referencias (Mayús+F12)** &ndash; con la coloración de sintaxis, puede agrupar los resultados de Buscar todas las referencias mediante una combinación de proyecto, definición y ruta de acceso. También puede "bloquear" resultados para seguir encontrando otras referencias sin perder los resultados originales.

 ![Nueva herramienta Buscar todas las referencias](../ide/media/vs2017ide-find-all-references.png "Ejemplo de la nueva herramienta Buscar todas las referencias")

* **Guías de sangría** &ndash; las líneas verticales grises con puntos sirven como puntos de referencia en el código para proporcionar contexto dentro del marco de vista. Puede reconocerlas de las populares herramientas Productivity Power Tools.

Para obtener más información acerca de nuestras nuevas características de productividad, consulte el blog [Productivity in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/productivity-in-visual-studio-2017-rc/) (Productividad en Visual Studio 2017) de Mark Wilson-Thomas.

### <a name="visual-c"></a>Visual C++
Verá varias mejoras en Visual Studio, como la distribución de C++ Core Guidelines con Visual Studio, la actualización del compilador mediante la incorporación de compatibilidad mejorada para características de C++11 y C++ y la adición y actualización de las funciones de las bibliotecas de C++. También hemos mejorado el rendimiento del IDE de C++ y las cargas de trabajo de la instalación, entre otros elementos.

Además, hemos corregido más de 250 errores y problemas notificados en el compilador y las herramientas, muchos enviados por los usuarios a través de [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect").

Para obtener información completa, vea nuestra página [What's New for Visual C++ in Visual 2017 RC](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio) (Novedades de Visual C++ en Visual 2017 RC).  

### <a name="debugging-and-diagnostics"></a>Depuración y diagnósticos
#### <a name="run-to-click"></a>Hacer clic y ejecutar:
Ahora, puede más continuar más fácilmente con la depuración desde un punto concreto sin tener que establecer un punto de interrupción para detenerse en una línea determinada. Cuando se haya detenido en el depurador, simplemente haga clic en el icono que aparece junto a la línea de código. El código se ejecutará y se detendrá en esa línea la próxima vez que se alcance en la ruta de código.

![Depuración de Visual Studio 2017 RC - Hacer clic y ejecutar](../ide/media/vs2017ide-RunToClick.png "Hacer clic y ejecutar en depuración y diagnóstico de Visual Studio 2017")

#### <a name="the-new-exception-helper"></a>La nueva aplicación auxiliar de excepciones:
La nueva aplicación auxiliar de excepciones le ayuda a ver la información de excepciones de un solo vistazo. La información se presenta en un formato compacto con acceso instantáneo a las excepciones internas. Al diagnosticar un caso de NullReferenceException, puede ver rápidamente qué referencias son nulas en la aplicación auxiliar de excepciones.

![Cuadro de diálogo de la nueva aplicación auxiliar de excepciones en Visual Studio](../ide/media/vs2017ide-ExceptionHelper.png "Cuadro de diálogo de la nueva aplicación auxiliar de excepciones")

Para obtener más información, vea la publicación del blog [Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) (Usar la nueva aplicación auxiliar de excepciones en Visual Studio).

## <a name="cloud-app-development-with-azure"></a>Desarrollo de aplicaciones en la nube con Azure
### <a name="azure-functions-tools"></a>Herramientas de Azure Functions
Como parte de la carga de trabajo "Desarrollo de Azure", hemos incluido herramientas para ayudarle a desarrollar funciones de Azure con bibliotecas de clases de C# precompiladas. Ahora puede compilar, ejecutar y depurar en su equipo de desarrollo local y, después, publicar directamente en Azure desde Visual Studio.

Para obtener más información, vea la página [Herramientas de Azure Functions para Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-develop-vs).

## <a name="mobile-app-development"></a>Desarrollo de aplicaciones móviles
### <a name="xamarin"></a>Xamarin
Como parte de la carga de trabajo de "Desarrollo móvil con .NET", los desarrolladores que estén familiarizados con C#, .NET y Visual Studio pueden proporcionar aplicaciones nativas de Android, iOS y Windows con Xamarin. Los desarrolladores pueden disfrutar de la misma eficacia y productividad al trabajar con Xamarin para aplicaciones móviles, incluida la depuración remota en dispositivos Android, iOS y Windows, &mdash;sin tener que aprender lenguajes de programación nativos como Objective-C o Java.

Para obtener más información, vea la página [Visual Studio y Xamarin](../cross-platform/visual-studio-and-xamarin.md).

### <a name="entitlements-editor"></a>Editor de derechos
**Novedades de la versión 15.3**: Para sus necesidades de desarrollo de iOS, hemos agregado un editor de derechos independiente. Incluye una interfaz de usuario fácil de usar que puede examinarse fácilmente. Para iniciarlo, haga doble clic en el archivo entitlements.plist.

![Editor de derechos para Xamarin](../ide/media/xamarin-entitlements-editor.png "Editor de derechos para Xamarin")

## <a name="cross-platform-development"></a>Desarrollo multiplataforma
### <a name="redgate-data-tools"></a>Redgate Data Tools
Para ampliar las funcionalidades de DevOps para el desarrollo de bases de datos de SQL Server, Redgate Data Tools ahora está disponible en las siguientes ediciones de Visual Studio 2017.

Incluido con Visual Studio 2017 Enterprise:
- [Redgate ReadyRoll Core](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) le ayuda a desarrollar scripts de migración, administrar cambios en la base de datos a través del control de código fuente y automatizar de forma segura implementaciones de cambios en la base de datos de SQL Server junto con cambios en las aplicaciones.
- [Redgate SQL Prompt Core](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) le ayuda a escribir SQL con más rapidez y exactitud con la ayuda de la finalización de código inteligente. SQL Prompt completa automáticamente los objetos de base de datos y del sistema, así como las palabras clave, y ofrece sugerencias de columna a medida que escribe. Esto da como resultado un código más limpio con menos errores porque no es necesario recordar cada nombre o alias de columna.

Incluido con todas las ediciones de Visual Studio 2017:
- [Búsqueda de SQL de Redgate](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) aumenta la productividad al permitir encontrar rápidamente fragmentos y objetos de SQL en varias bases de datos.

Para obtener más información, vea la entrada de blog [Redgate Data Tools in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2017/03/07/redgate-data-tools-in-visual-studio-2017/) (Redgate Data Tools en Visual Studio 2017).

### <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools para Unity
Como parte de la carga de trabajo "Desarrollo de juegos para Unity", hemos incluido herramientas para ayudarle a desarrollar una multiplataforma para crear juegos 2D y 3D y contenido interactivo. Cree el contenido una vez y publíquelo en 21 plataformas, incluidas todas las plataformas móviles, WebGL, Mac, PC y escritorio de Linux, web o consolas con Visual Studio 2017 y Unity 5.6.

Para obtener más información, vea la página [Visual Studio Tools para Unity](../cross-platform/visual-studio-tools-for-unity.md).

### <a name="net-core"></a>Núcleo de .NET
.NET Core es una implementación de .NET Standard para uso general, modular, multiplataforma y de código abierto, y contiene muchas de las mismas API que .NET Framework.

La plataforma .NET Core está formada por varios componentes, entre los que se incluyen los compiladores administrados, el entorno de ejecución, las bibliotecas de clases base y numerosos modelos de aplicaciones, como ASP.NET Core. .NET Core es compatible con los tres principales sistemas operativos: Windows, Linux y macOS. Puede usar .NET Core en escenarios de dispositivos, nube e insertados/IoT.

Ahora también es compatible con Docker.

**Novedades de la versión 15.3**: La versión 15.3 de Visual Studio 2017 admite el desarrollo de .NET Core 2.0. (En la versión 15.3, el uso de .NET Core 2.0 requiere descargar e instalar el SDK de .NET Core 2.0 de manera independiente).

Para obtener más información, vea la página [Guía de .NET Core](https://docs.microsoft.com/dotnet/core/index).

## <a name="talk-to-us"></a>Hable con nosotros  
 ¿Por qué enviar comentarios al equipo de Visual Studio? Nos tomamos los comentarios de los clientes muy en serio, ya que son la base de nuestro trabajo.

Si quiere realizar sugerencias sobre cómo podemos mejorar Visual Studio o notificar un problema, vea la página [Hable con nosotros](../ide/talk-to-us.md) para obtener más información.

### <a name="report-a-problem"></a>Notificar un problema  
 A veces, un mensaje no es suficiente para transmitir el impacto completo de un problema que ha detectado. Si experimenta un bloqueo u otro problema de rendimiento, puede compartir fácilmente los pasos de reproducción y los archivos auxiliares (como capturas de pantalla y archivos de seguimiento y volcado del montón) con nosotros mediante la herramienta **Notificar un problema**. Para obtener más información sobre cómo usar esta herramienta, vea la página [Cómo notificar un problema](how-to-report-a-problem-with-visual-studio-2017.md).

### <a name="track-your-issue-in-connect"></a>Realice un seguimiento de su problema en Connect  
 Si quiere realizar un seguimiento del estado de su comentario sobre Visual Studio, vaya a [Connect](http://connect.microsoft.com/) y notifique el error allí. Después de notificarlo, puede volver a Connect para realizar un seguimiento de su estado.

## <a name="see-also"></a>Vea también
* [Notas de la versión de Visual Studio 2017](https://www.visualstudio.com/news/vs2015-vs)
* [What's New in Visual C++ (Novedades de Visual C++)](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [What's New in C# (Novedades de C#)](https://docs.microsoft.com/dotnet/csharp/csharp-7)  
* [What's New for Team Foundation Server (Novedades de Team Foundation Server)](https://www.visualstudio.com/docs/whats-new)
* [Novedades de Visual Studio para Mac](https://www.visualstudio.com/vs/visual-studio-mac/)

