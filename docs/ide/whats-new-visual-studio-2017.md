---
title: Novedades de Visual Studio 2017
titleSuffix: ''
description: Más información sobre las nuevas características de Visual Studio 2017.
ms.date: 12/18/2018
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 79570fe403c12c89860a67683456a3d6ca3d3f01
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189605"
---
# <a name="whats-new-in-visual-studio-2017"></a>Novedades de Visual Studio 2017

**Actualizado para la [versión 15.9](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)**

¿Quiere actualizar desde una versión anterior de Visual Studio? Esto es lo que Visual Studio 2017 puede ofrecerle: Productividad incomparable para cualquier desarrollador, aplicación y plataforma. Use Visual Studio 2017 para desarrollar aplicaciones para Android, iOS, Windows, Linux, la Web y la nube. Escriba código con rapidez, depure y emita diagnósticos con facilidad, ejecute pruebas con frecuencia y publique con confianza. También puede ampliar y personalizar Visual Studio si crea sus propias extensiones. Use el control de versiones, actúe con agilidad y colabore de manera eficiente con esta versión.

>[!div class="button"]
>[Descarga de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

Este es un resumen general de los cambios que hemos realizado desde la versión anterior, Visual Studio 2015:

* **[Redefinición de los aspectos básicos](#redefined-fundamentals)** . Una nueva experiencia de instalación significa que puede instalar más rápidamente e instalar lo que desee cuando lo necesite.
* **[Rendimiento y productividad](#performance-and-productivity)** . Nos hemos centrado en nuevas y modernas funciones de desarrollo de escritorio, en la nube y móviles. Además, Visual Studio se inicia más rápido, tiene mejor capacidad de respuesta y usa menos memoria que antes.
* **[Desarrollo de aplicaciones en la nube con Azure](#cloud-app-development-with-azure)** . Se trata de un conjunto integrado de herramientas de Azure que le permite crear con facilidad aplicaciones principalmente destinadas a la nube con la tecnología de Microsoft Azure. Visual Studio facilita la configuración, la compilación, la depuración, el empaquetado y la implementación de aplicaciones y servicios en Azure.
* **[Desarrollo de aplicaciones para Windows](#windows-app-development)** . Use las plantillas de UWP en Visual Studio 2017 para crear un proyecto único para todos los dispositivos Windows 10&ndash; PC, tableta, teléfono, Xbox, HoloLens, Surface Hub y mucho más.
* **[Desarrollo de aplicaciones móviles](#mobile-app-development)** . Innove y obtenga resultados rápidamente con Xamarin, que unifica los requisitos móviles multiplataforma en un código base principal y un conjunto de aptitudes.
* **[Desarrollo multiplataforma](#cross-platform-development)** . Distribuya software en cualquier plataforma de destino sin problemas. Extienda los procesos de DevOps a SQL Server por medio de Redgate Data Tools y automatice con seguridad las implementaciones de base de datos desde Visual Studio. O use .NET Core para escribir aplicaciones y bibliotecas que se ejecuten sin modificarse en sistemas operativos Windows, Linux y macOS.
* **[Desarrollo de juegos](#games-development)** . Con Visual Studio Tools para Unity (VSTU), puede usar Visual Studio para escribir scripts de editor y juegos en C# y, a continuación, usar su eficaz depurador para buscar y corregir errores.
* **[Desarrollo de IA](#ai-development)** . Con Visual Studio Tools for AI, puede usar las características de productividad de Visual Studio para acelerar la innovación de IA. Compile, pruebe e implemente las soluciones de aprendizaje profundo e inteligencia artificial que se integran fácilmente con Azure Machine Learning para conseguir capacidades de experimentación sólidas.

> [!NOTE]
> Para una lista completa de las características y funcionalidades nuevas de Visual Studio 2017, consulte las [notas de la versión actual](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017). Para inspeccionar las ofertas de características futuras, consulte las [notas de la versión preliminar](/visualstudio/releasenotes/vs2017-preview-relnotes?context=visualstudio/default&contextView=vs-2017).

Aquí se muestra información más detallada sobre algunas de las mejoras más destacables y las nuevas características de Visual Studio 2017.

## <a name="redefined-fundamentals"></a>Redefinición de los aspectos básicos

### <a name="a-new-setup-experience"></a>Una nueva experiencia de instalación

Visual Studio acelera y facilita la instalación de simplemente las características que necesita, y justo cuando las necesita. Y, además, se desinstala sin errores.

El cambio más importante que verá cuando instale Visual Studio es su nueva experiencia de instalación. En la pestaña **Cargas de trabajo**, verá opciones de instalación que se agrupan para representar marcos, lenguajes y plataformas comunes. Abarca todo, desde el desarrollo de escritorio de .NET hasta el desarrollo de aplicaciones de C++ en Windows, Linux y iOS.

Seleccione las cargas de trabajo que requiere y cámbielas cuando sea necesario.

![Cuadro de diálogo del programa de instalación de Visual Studio 2017](../install/media/install-visual-studio-enterprise.png)

También tiene diferentes opciones para configurar la instalación:

* ¿Quiere seleccionar sus propios componentes en lugar de usar cargas de trabajo? Seleccione la pestaña **Componentes individuales** del instalador.
* ¿Quiere instalar paquetes de idioma sin tener que cambiar la opción de idioma de Windows? Pulse la pestaña **Paquetes de idioma** del instalador.
* **Novedad de la versión 15.7**: ¿Quiere cambiar la ubicación de instalación de Visual Studio? Elija la pestaña **Opciones de instalación** del instalador.

Para más información sobre la nueva experiencia de instalación, incluidas instrucciones paso a paso para guiarle, consulte la página [Instalación de Visual Studio](../install/install-visual-studio.md).

### <a name="a-focus-on-accessibility"></a>Hacer hincapié en la accesibilidad

**Novedad de la versión 15.3**: hemos realizado más de 1700 correcciones de destino para mejorar la compatibilidad entre Visual Studio y las tecnologías de asistencia que muchos clientes usan. Existen docenas de escenarios que son más compatibles que nunca con lectores de pantalla, temas de alto contraste y otras tecnologías de ayuda. El depurador, el editor y el shell también se han mejorado considerablemente.

Para más información, vea la entrada de blog [Accessibility improvements in Visual Studio 2017 version 15.3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) (Mejoras de accesibilidad en Visual Studio 2017 versión 15.3).

## <a name="performance-and-productivity"></a>Rendimiento y productividad

### <a name="sign-in-across-multiple-accounts"></a>Iniciar sesión en varias cuentas

Presentamos un nuevo servicio de identidad en Visual Studio que le permite compartir cuentas de usuario en Team Explorer, Azure Tools, publicar contenido en Microsoft Store y mucho más.

También puede permanecer más tiempo con la sesión abierta. Visual Studio no le pedirá que vuelva a iniciar sesión cada 12 horas. Para obtener más información, vea la publicación del blog [Fewer Visual Studio Sign-in Prompts](https://devblogs.microsoft.com/visualstudio/fewer-visual-studio-sign-in-prompts/) (Menos mensajes emergentes de inicio de sesión en Visual Studio).

### <a name="start-visual-studio-faster"></a>Iniciar Visual Studio más rápido

El nuevo Centro de rendimiento de Visual Studio puede ayudarle a optimizar el tiempo necesario para iniciar el IDE. El Centro de rendimiento muestra todas las extensiones y ventanas de herramientas que pueden estar ralentizando el inicio del IDE. Puede usarlo para mejorar el rendimiento de inicio determinando cuándo se inician las extensiones o si las ventanas de herramientas están abiertas en el inicio.

### <a name="faster-on-demand-loading-of-extensions"></a>Carga de extensiones a petición más rápida

Visual Studio moverá sus extensiones (y también trabajará con extensiones de terceros) para que se carguen bajo demanda, en lugar de en el momento de inicio del IDE. ¿Tiene curiosidad por saber qué extensiones afectan al inicio, la carga de la solución y el rendimiento de escritura? Puede ver esta información en **Ayuda** > **Administrar el rendimiento de Visual Studio**.

  ![Cuadro de diálogo Opciones en Visual Studio 2017](media/vs2017ide-manage-vs-perf.png)

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Administrar las extensiones con Roaming Extension Manager

Ahora es más sencillo configurar cada entorno de desarrollo con sus extensiones favoritas cuando inicie sesión en Visual Studio. El nuevo Roaming Extension Manager mantiene el seguimiento de todas sus extensiones favoritas mediante la creación de una lista sincronizada en la nube.

Para ver una lista de las extensiones de Visual Studio, haga clic en **Herramientas** > **Extensiones y actualizaciones** y, después, haga clic en **Roaming Extension Manager**.

![Visual Studio 2017: Cuadro de diálogo Extensiones y actualizaciones](media/vs2017ide-extensions-and-updates.png)

Roaming Extension Manager realiza un seguimiento de todas las extensiones que instale, pero puede decidir las que quiere agregar a la lista de itinerancia.

![Visual Studio 2017: Cuadro de diálogo Extensiones y actualizaciones](media/vs2017ide-RoamingExtensionManager.png)

Cuando use Roaming Extension Manager, verá tres tipos de icono en la lista:

* ![Icono de extensión en movimiento](media/vs2017ide-roamedicon.png) **_Extensión en movimiento_** : una extensión que forma parte de esta lista de itinerancia, pero que no está instalada en el equipo.
  (Puede instalarlas mediante el botón **Descargar**).
* ![Icono de extensión en movimiento e instalada](media/vs2017ide-roamedinstalledicon.png) **_Extensión en movimiento e instalada_** : todas las extensiones que forman parte de la lista Itinerancia y están instaladas en el entorno de desarrollo.
  (Si decide que no quiere usar un perfil itinerante, puede quitarlas mediante el botón **Detener itinerancia**).
* ![Icono de extensión instalada](media/vs2017ide-installedicon.png) **_Extensión instalada_** : todas las extensiones que están instaladas en este entorno, pero que no forman parte de la lista Itinerancia.
  (Puede agregar extensiones a la lista de itinerancia mediante el botón **Iniciar itinerancia**).

Todas las extensiones que descargue con la sesión iniciada se agregan a la lista como **Extensión con perfil itinerante e instalada**. La extensión pasa a formar parte de la lista Itinerancia, que le proporciona acceso a ella desde cualquier equipo.

### <a name="experience-live-unit-testing"></a>Experiencia con Live Unit Testing

En Visual Studio Enterprise de 2017, Live Unit Testing le ofrece los resultados de las pruebas unitarias y la cobertura de código en el editor al tiempo que codifica. Funciona con proyectos de C# y Visual Basic para .NET Framework y .NET Core, y admite tres marcos de prueba de MSTest, xUnit y NUnit.

![Live Unit Testing](media/lut-codewindow.png)

Para más información, vea [Introducción Live Unit Testing](../test/live-unit-testing-intro.md) (Presentación de Live Unit Testing). Para obtener una lista de las nuevas características agregadas en cada versión de Visual Studio Enterprise 2017, vea [Novedades de Live Unit Testing](../test/live-unit-testing-whats-new.md).

### <a name="set-up-a-cicd-pipeline"></a>Configurar una canalización de CI/CD

#### <a name="automated-testing"></a>Pruebas automatizadas

Las pruebas automatizadas son una parte fundamental de cualquier canalización de DevOps. Le permiten probar y presentar su solución de manera coherente y confiable en ciclos mucho más cortos. Los flujos de CI/CD (integración continua y entrega continua) pueden ayudarle a hacer que el proceso sea más eficaz.

Para más información sobre las pruebas automatizadas, vea la publicación del blog [CI/CD pipeline for automated tests in DevOps](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/) (Canalización de CI/CD para pruebas automatizadas en DevOps).

Para obtener más información sobre las novedades de la extensión de DevLabs de [Herramientas de entrega continua para Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio), vea la entrada de blog [Commit with Confidence: Commit Time Code Quality](https://devblogs.microsoft.com/visualstudio/committing-with-confidence-getting-code-quality-information-at-commit-time/) (Confirmar con confianza: calidad del código en tiempo de confirmación).

### <a name="visual-studio-ide-enhancements"></a>Mejoras del IDE de Visual Studio

#### <a name="multi-caret-editing"></a>Edición de varios símbolos de inserción

**Novedad de la versión 15.8**: ahora es fácil editar varias ubicaciones en un archivo al mismo tiempo. Empiece por crear puntos de inserción y selecciones en varias ubicaciones de un archivo. Después, use la característica de edición de varios símbolos de inserción para realizar la misma edición en dos o más lugares al mismo tiempo.

Para más información, vea la sección [Selección de varios símbolos de inserción](finding-and-replacing-text.md#multi-caret-selection) de la página [Buscar y reemplazar texto](finding-and-replacing-text.md).

#### <a name="keep-keybinding-profiles-consistent"></a>Mantener la coherencia de los perfiles de enlace de teclado

**Novedad de la versión 15.8**: ahora puede mantener los mismos enlaces de teclado entre distintas herramientas mediante dos nuevos perfiles de teclado: Visual Studio Code y ReSharper (Visual Studio). Puede encontrar estos esquemas en **Herramientas** > **Opciones** > **General** > **Teclado** y el menú desplegable superior.

  ![Nuevos perfiles de enlace de teclado para ReSharper y Visual Studio Code](media/vs-keyboard-mappings-code-resharper.png)

#### <a name="use-new-refactorings"></a>Uso de nuevas refactorizaciones

La refactorización es el proceso de mejorar el código una vez escrito. La refactorización cambia la estructura interna del código sin cambiar su comportamiento. Se agregan refactorizaciones nuevas con frecuencia. Estas son solo algunas de ellas:

* Agregar un parámetro (desde CallSite)
* Generar invalidaciones
* Agregar un argumento con nombre
* Agregar comprobación de NULL para los parámetros
* Insertar separadores de dígitos en literales
* Cambiar base de literales numéricos (por ejemplo, hexadecimal a binario)
* Convertir instrucciones if-to-switch
* Quitar variables no usadas

Para más información, consulte [Acciones rápidas](common-quick-actions.md).

#### <a name="interact-with-git"></a>Interacción con GIT

Cuando se trabaja con un proyecto en Visual Studio, puede configurar y rápidamente confirmar y publicar el código en un servicio de GIT. También puede administrar sus repositorios de GIT por medio de clics de menú con los botones de la esquina inferior derecha del IDE.

![Visual Studio 2017 interactúa con el cuadro de diálogo de Git](media/vsIDE-GitInteraction.png)

#### <a name="experience-improved-navigation-controls"></a>Experiencia de controles de navegación mejorada

Se ha actualizado la experiencia de navegación para ayudarle a llegar de A a B con mayor confianza y menos distracciones.

* **Novedad de la versión 15.4**: **Ir a definición** (**Ctrl**+**clic** o **F12**) &ndash; Los usuarios del mouse tienen una manera más fácil de navegar a la definición de un miembro: presionar **Ctrl** y, después, hacer clic en el miembro. Al presionar **Ctrl** y mantener el puntero sobre un símbolo de código lo subrayará y lo convertirá en un vínculo. Vea [Go To Definition and Peek Definition](go-to-and-peek-definition.md) (Ir a definición y Ver la definición) para más información.

* **Ir a implementación** (**CTRL**+**F12**) &ndash; Navegue desde cualquier tipo base o miembro a sus diversas implementaciones.

* **Ir a todo** (**CTRL**+**T** o **CTRL**+ **,** ) &ndash; Navegue directamente a cualquier declaración de archivo/tipo/miembro/símbolo. Puede filtrar la lista de resultados o usar la sintaxis de consulta (por ejemplo, "f searchTerm" para los archivos, "t searchTerm" para los tipos, etc.).

  ![Se ha mejorado la opción "Ir a Todo"](media/vs2017ide-navigation-go-to.png)

* **Buscar todas las referencias** (**Mayús**+**F12**) &ndash; Con la coloración de sintaxis, puede agrupar los resultados de Buscar todas las referencias mediante una combinación de proyecto, definición y ruta de acceso. También puede "bloquear" resultados para seguir encontrando otras referencias sin perder los resultados originales.

  ![Nueva herramienta Buscar todas las referencias](media/vs2017ide-find-all-references.png)

* **Visualizador de estructuras** &ndash; Las líneas verticales grises con puntos sirven como puntos de referencia en el código para proporcionar contexto dentro del marco de vista. Puede reconocerlas de las populares herramientas Productivity Power Tools. Puede usarlas para visualizar y descubrir en qué bloque de código se encuentra en cualquier momento sin tener que desplazarse. Al mantener el puntero sobre las líneas aparece la información sobre herramientas que muestra la apertura de ese bloque y sus elementos primarios. Está disponible para todos los lenguajes admitidos a través de las gramáticas de TextMate, así como C#, Visual Basic y XAML.

  ![Visualizador de estructura de Visual Studio 2017](media/vsIDE-StructureVisualizer.png)

Para más información sobre las nuevas características de productividad, consulte la entrada de blog [Visual Studio 2017: Productividad, rendimiento y socios](https://devblogs.microsoft.com/visualstudio/visual-studio-2017-productivity-performance-and-partners/) (Visual Studio 2017: productividad, rendimiento y asociados).

### <a name="visual-c"></a>Visual C++

Verá varias mejoras en Visual Studio, como la distribución de C++ Core Guidelines con Visual Studio, la actualización del compilador mediante la incorporación de compatibilidad mejorada para características de C++11 y C++ y la adición y actualización de las funciones de las bibliotecas de C++. También hemos mejorado el rendimiento del IDE de C++ y las cargas de trabajo de la instalación, entre otros elementos.

Además, hemos corregido más de 250 errores y problemas notificados en el compilador y las herramientas, muchos de ellos enviados por los usuarios a través de la [Comunidad de desarrolladores de C++](https://developercommunity.visualstudio.com/spaces/62/index.html "Comunidad de desarrolladores de C++").

Para información completa, consulte la página [Novedades de Visual C++ en Visual 2017](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio).

### <a name="debugging-and-diagnostics"></a>Depuración y diagnósticos

#### <a name="run-to-click"></a>Icono para ejecutar hasta la línea

Ahora, puede más continuar más fácilmente con la depuración desde un punto concreto sin tener que establecer un punto de interrupción para detenerse en una línea determinada. Cuando se haya detenido en el depurador, simplemente haga clic en el icono que aparece junto a la línea de código. El código se ejecutará y se detendrá en esa línea la próxima vez que se alcance en la ruta de código.

![Depuración de Visual Studio 2017: Icono para ejecutar hasta la línea](media/vs2017ide-RunToClick.png)

#### <a name="the-new-exception-helper"></a>Nuevo asistente de excepciones

El nuevo asistente de excepciones le ayuda a ver la información de excepciones de un solo vistazo. La información se presenta en un formato compacto con acceso instantáneo a las excepciones internas. Al diagnosticar un caso de NullReferenceException, puede ver rápidamente qué referencias son nulas en el asistente de excepciones.

![Cuadro de diálogo Nuevo asistente de excepciones en Visual Studio](media/vs2017ide-ExceptionHelper.png)

Para obtener más información, vea la publicación del blog [Use the New Exception Helper in Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/) (Usar el nuevo asistente de excepciones en Visual Studio).

#### <a name="snapshots-and-intellitrace-step-back"></a>Instantáneas y step-back de IntelliTrace

**Novedades de la versión 15.5**: La característica step-back (paso atrás) de IntelliTrace toma automáticamente una instantánea de la aplicación en cada punto de interrupción y evento de paso del depurador. Las instantáneas registradas le permiten volver a puntos de interrupción anteriores y ver el estado de la aplicación tal y como estaba en un momento anterior. La característica step-back de IntelliTrace puede permitirle ahorrar tiempo cuando desea ver el estado anterior de la aplicación, pero no desea reiniciar la depuración ni volver a crear el estado de aplicación que se desea.

Para poder navegar y ver las instantáneas, use los botones **Retroceder paso a paso** y **Avanzar paso a paso** en la barra de herramientas de **depuración**. Estos botones permiten navegar por los eventos que aparecen en la pestaña **Eventos** en la ventana **Herramientas de diagnóstico**. Retroceder o avanzar paso a paso a un evento activa de manera automática la depuración histórica del evento seleccionado.

![Cuadro de diálogo Nuevo asistente de excepciones en Visual Studio](../debugger/media/intellitrace-step-back-icons-description.png  "Botones Retroceder paso a paso y Avanzar paso a paso")

Para más información, consulte la página [Visualización de instantáneas mediante step-back de IntelliTrace](../debugger/view-historical-application-state.md).

### <a name="containerization"></a>Inclusión en contenedores

Los contenedores proporcionan mayor densidad de aplicaciones y menores costos de implementación, junto con una mejorada productividad y agilidad de DevOps.

#### <a name="docker-container-tooling"></a>Herramientas de contenedor de Docker

**Novedades de la versión 15.5**:

* Visual Studio incluye herramientas para los contenedores de Docker que ahora admiten Dockerfiles de varias etapas que simplifican la creación de imágenes optimizadas de contenedor.
* De forma predeterminada, Visual Studio extrae, compila y ejecuta automáticamente las imágenes de contenedor necesarias en segundo plano cuando se abre un proyecto que incluye compatibilidad con Docker. Puede deshabilitarlo en la opción **Iniciar automáticamente los contenedores en segundo plano** de Visual Studio.

## <a name="cloud-app-development-with-azure"></a>Desarrollo de aplicaciones en la nube con Azure

### <a name="azure-functions-tools"></a>Herramientas de Azure Functions

Como parte de la carga de trabajo "Desarrollo de Azure", hemos incluido herramientas para ayudarle a desarrollar funciones de Azure con bibliotecas de clases de C# precompiladas. Ahora puede compilar, ejecutar y depurar en su equipo de desarrollo local y, después, publicar directamente en Azure desde Visual Studio.

Para obtener más información, vea la página [Herramientas de Azure Functions para Visual Studio](/azure/azure-functions/functions-develop-vs).

### <a name="debug-live-aspnet-apps-using-snappoints-and-logpoints-in-live-azure-applications"></a>Depuración de aplicaciones ASP.NET activas con puntos de acoplamiento y puntos de registro en aplicaciones Azure activas

**Novedades de la versión 15.5**: Snapshot Debugger toma una instantánea de las aplicaciones en producción cuando se ejecuta el código que le interesa. Para indicar al depurador que tome una instantánea, establezca puntos de acoplamiento y puntos de registro en el código. El depurador le permite ver exactamente qué salió mal, sin afectar el tráfico de la aplicación de producción. El Depurador de instantáneas puede permitirle disminuir considerablemente el tiempo que tarda en resolver los problemas que se producen en los entornos de producción.

La colección de instantáneas está disponible para las siguientes aplicaciones web que se ejecutan en Azure App Service:

* Aplicaciones ASP.NET que se ejecutan en .NET Framework 4.6.1 o versiones posteriores.
* Aplicaciones ASP.NET Core que se ejecutan en .NET Core 2.0 o posteriores en Windows.

Para más información, consulte [Depuración de aplicaciones ASP.NET activas con puntos de acoplamiento y puntos de registro](../debugger/debug-live-azure-applications.md).

## <a name="windows-app-development"></a>Desarrollo de aplicaciones para Windows

### <a name="universal-windows-platform"></a>Plataforma universal de Windows

Plataforma universal de Windows (UWP) es la plataforma de aplicaciones de Windows 10. Puede desarrollar aplicaciones para UWP con solo un conjunto de API, un paquete de la aplicación y un almacén para llegar a todos los dispositivos Windows 10 &ndash; PC, tableta, teléfono, Xbox, HoloLens, Surface Hub y mucho más. UWP admite distintos tamaños de pantalla y una variedad de modelos de interacción, ya sea táctil, mouse y teclado, un dispositivo de juego o un lápiz. La base de las aplicaciones de UWP es la idea de que los usuarios quieren que sus experiencias sean móviles en TODOS sus dispositivos y que quieren usar el dispositivo que sea más conveniente o productivo para la tarea en cuestión.

![Plataforma universal de Windows](../cross-platform/media/uwp_coreextensions.png)

Elija el lenguaje de desarrollo de su preferencia&mdash;desde C#, Visual Basic, C++ o JavaScript&mdash;para crear una aplicación Plataforma universal de Windows para dispositivos con Windows 10. Visual Studio 2017 proporciona una plantilla de aplicaciones de UWP para cada lenguaje que le permite crear un solo proyecto para todos los dispositivos. Una vez que se finaliza el trabajo, puede generar un paquete de la aplicación y enviarlo a Microsoft Store desde Visual Studio para que la aplicación quede a disposición de los clientes en cualquier dispositivo Windows 10.

**Novedades de la versión 15.5**: La versión 15.5 de Visual Studio 2017 proporciona el mejor respaldo para el SDK de Windows 10 Fall Creators Update (10.0.16299.0). Windows 10 Fall Creators Update también ofrece muchas mejoras para los desarrolladores de UWP. A continuación, algunos de los cambios más importantes: 

* **Compatibilidad con .NET Standard 2.0**<br/>Además de una implementación de aplicación optimizada, Windows 10 Fall Creators Update es la primera versión de Windows 10 que ofrece compatibilidad con .NET Standard 2.0. De hecho, [.NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/) es una implementación de referencia de la biblioteca de clases base que cualquier plataforma .NET puede implementar. El objetivo de .NET Standard es que sea lo más sencillo posible que los desarrolladores de .NET compartan el código en cualquier plataforma .NET en la que elijan trabajar.
* **Lo mejor de UWP y Win32**<br/>Mejoramos la plataforma Windows 10 con el [Puente de dispositivo de escritorio](/windows/uwp/porting/desktop-to-uwp-root) para mejorar Windows 10 para todos los desarrolladores de .NET, sin importar si se centran en UWP, WPF, Windows Forms o Xamarin. Con el nuevo tipo de proyecto de paquetes de la implementación de la versión 15.5 de Visual Studio 2017, puede crear paquetes de aplicaciones de Windows para los proyectos de WPF o Windows Forms, exactamente igual que para los proyectos de UWP. Cuando empaqueta la aplicación, obtiene todos los beneficios de la implementación de la aplicación de Windows 10 y tiene la opción de una distribución a través de Microsoft Store (para aplicaciones de consumidor) o Microsoft Store para Empresas y para Educación. Como las aplicaciones empaquetadas tienen acceso tanto a la superficie de API UWP y las API Win32, ahora puede modernizar las aplicaciones de WPF y Windows Forms de manera gradual con las API UWP y las características de Windows 10. Además, puede incluir los componentes Win32 en las aplicaciones de UWP que funcionan en los equipos de escritorio con todas las funcionalidades Win32.

Para más información sobre UWP, consulte la página [Desarrollar aplicaciones para la Plataforma universal de Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md).

## <a name="mobile-app-development"></a>Desarrollo de aplicaciones móviles

### <a name="xamarin"></a>Xamarin

Como parte de la carga de trabajo de "Desarrollo móvil con .NET", los desarrolladores que estén familiarizados con C#, .NET y Visual Studio pueden proporcionar aplicaciones nativas de Android, iOS y Windows con Xamarin. Los desarrolladores pueden disfrutar de la misma eficacia y productividad al trabajar con Xamarin para aplicaciones móviles, incluida la depuración remota en dispositivos Android, iOS y Windows, &mdash;sin tener que aprender lenguajes de programación nativos como Objective-C o Java.

Para obtener más información, vea la página [Visual Studio y Xamarin](/xamarin/).

### <a name="entitlements-editor"></a>Editor de derechos

**Novedad de la versión 15.3**: Para las necesidades de desarrollo de iOS, se ha agregado un editor de derechos independiente. Incluye una interfaz de usuario fácil de usar que puede examinarse fácilmente. Para iniciarlo, haga doble clic en el archivo *entitlements.plist*.

![Editor de derechos para Xamarin](media/xamarin-entitlements-editor.png)

### <a name="visual-studio-tools-for-xamarin"></a>Visual Studio Tools para Xamarin

**Novedad de la versión 15.4**: Xamarin Live permite a los desarrolladores implementar, probar y depurar constantemente sus aplicaciones directamente en dispositivos iOS y Android. Después de descargar Xamarin Live Player (que se encuentra disponible en el App Store o en Google Play), puede emparejar su dispositivo con Visual Studio y revolucionar la forma en que compila aplicaciones móviles. Esta funcionalidad ya está incluida en Visual Studio y puede habilitarse en **Herramientas** > **Opciones** > **Xamarin** > **Otros** > **Habilitar Xamarin Live Player**.

![Animación del modo de edición en vivo, implementación y par de Xamarin Live Player](media/xamarinliveplayer.gif)

### <a name="support-for-google-android-emulator"></a>Compatibilidad con Google Android Emulator

**Novedad de la versión 15.8**: Cuando use Hyper-V, ahora ya puede usar Google Android Emulator en paralelo con otras tecnologías basadas en Hyper-V, como las máquinas virtuales de Hyper-V, el conjunto de herramientas Docker, el emulador HoloLens y mucho más. (Esta característica requiere Windows 10 con la actualización del 10 de abril de 2018 o posterior).

![Google Android Emulator en tecnologías Hyper-V](media/xamarin-hyperv-android-emulator.png)

#### <a name="xamarinandroid-designer-split-view-editor"></a>Editor de vista dividida de Xamarin.Android Designer

Otra **novedad de la versión 15.8**: Se han realizado mejoras importantes en la experiencia del diseñador para Xamarin.Android. Destaca el nuevo editor de vista dividida que le permite crear, editar y obtener una vista previa de los diseños al mismo tiempo.

![Editor de vista dividida de Xamarin.Android Designer](media/android-designer-split-view.png)

Para más información, vea [Aceleración de hardware para el rendimiento del emulador](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin).

### <a name="visual-studio-app-center"></a>Centro de aplicaciones de Visual Studio

**Novedades de la versión 15.5**: Visual Studio App Center (que ahora está disponible con carácter general para aplicaciones Android, iOS, macOS y Windows) tiene todo lo necesario para administrar el ciclo de vida de las aplicaciones, incluidas compilaciones automatizadas, pruebas en dispositivos reales en la nube, distribución a los evaluadores de versiones Beta y las tiendas de aplicaciones, además de la supervisión del uso en tiempo real a través de los datos de bloqueo y análisis. Las aplicaciones escritas en Objective-C, Swift, Java, C#, Xamarin y React Native son compatibles con todas las características.

  ![Entorno de prueba Visual Studio App Center](media/app-center-test-env.png)

Para obtener más información, vea la entrada de blog [Introducing App Center: Build, test, distribute and monitor apps in the cloud](https://blogs.msdn.microsoft.com/vsappcenter/introducing-visual-studio-app-center/) (Introducción a App Center: compilación, pruebas, distribución y monitorización de aplicaciones en la nube).

## <a name="cross-platform-development"></a>Desarrollo multiplataforma

### <a name="redgate-data-tools"></a>Redgate Data Tools

Para ampliar las funcionalidades de DevOps para el desarrollo de bases de datos de SQL Server, Redgate Data Tools ahora está disponible en Visual Studio.

Incluido con Visual Studio 2017 Enterprise:

* [Redgate ReadyRoll Core](https://www.red-gate.com/products/sql-development/sql-change-automation/?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) le ayuda a desarrollar scripts de migración, administrar cambios en la base de datos a través del control de código fuente y automatizar de forma segura implementaciones de cambios en la base de datos de SQL Server junto con cambios en las aplicaciones.
* [Redgate SQL Prompt Core](https://www.red-gate.com/products/sql-development/sql-prompt/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) le ayuda a escribir SQL con más rapidez y exactitud con la ayuda de la finalización de código inteligente. SQL Prompt completa automáticamente los objetos de base de datos y del sistema, así como las palabras clave, y ofrece sugerencias de columna a medida que escribe. Esto da como resultado un código más limpio con menos errores porque no es necesario recordar cada nombre o alias de columna.

Incluido con todas las ediciones de Visual Studio 2017:

* [Búsqueda de SQL de Redgate](https://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) aumenta la productividad al permitir encontrar rápidamente fragmentos y objetos de SQL en varias bases de datos.

Para más información, consulte la entrada de blog [Redgate Data Tools en Visual Studio 2017](https://devblogs.microsoft.com/visualstudio/redgate-data-tools-in-visual-studio-2017/).

### <a name="net-core"></a>Núcleo de .NET

.NET Core es una implementación de .NET Standard para uso general, modular, multiplataforma y de código abierto, y contiene muchas de las mismas API que .NET Framework.

La plataforma .NET Core está formada por varios componentes, entre los que se incluyen los compiladores administrados, el entorno de ejecución, las bibliotecas de clases base y numerosos modelos de aplicaciones, como ASP.NET Core. .NET Core es compatible con los tres sistemas operativos principales: Windows, Linux y macOS. Puede usar .NET Core en escenarios de dispositivos, nube e insertados/IoT.

Ahora también es compatible con Docker.

**Novedad de la versión 15.3**: La versión 15.3 de Visual Studio 2017 admite el desarrollo de .NET Core 2.0. El uso de .NET Core 2.0 requiere descargar e instalar el SDK de .NET Core 2.0 de manera independiente.

Para obtener más información, vea la página [Guía de .NET Core](/dotnet/core/index).

## <a name="games-development"></a>Desarrollo de juegos

### <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools para Unity

Como parte de la carga de trabajo "Desarrollo de juegos para Unity", hemos incluido herramientas para ayudarle a desarrollar una multiplataforma para crear juegos 2D y 3D y contenido interactivo. Cree el contenido una vez y publíquelo en 21 plataformas, incluidas todas las plataformas móviles, WebGL, Mac, PC y escritorio de Linux, web o consolas con Visual Studio 2017 y Unity 5.6.

Para obtener más información, vea la página [Visual Studio Tools para Unity](../cross-platform/visual-studio-tools-for-unity.md).

## <a name="ai-development"></a>Desarrollo de IA

### <a name="visual-studio-tools-for-ai"></a>Visual Studio Tools para IA

**Novedades de la versión 15.5**: Use las características de productividad de Visual Studio para impulsar sin dilación la innovación de AI. Use características de editor de código integradas como el resaltado de sintaxis, IntelliSense y el formato automático de texto. La aplicación de aprendizaje profundo se puede probar de forma interactiva en el entorno local por medio de la depuración paso a paso de los modelos y las variables locales.

  ![IDE de aprendizaje profundo](../ai/media/about/ide.png)

Para más información, consulte la página [Visual Studio Tools para IA](../ai/about-ai-tools.md).

## <a name="whats-next"></a>Pasos adicionales

Actualizamos Visual Studio 2017 a menudo con nuevas características que pueden mejorar aún más su experiencia de desarrollo. Este es un resumen de algunas de nuestras actualizaciones más importantes que se encuentran en versión preliminar experimental:

* **[Live Share](https://visualstudio.microsoft.com/services/live-share/)** , una nueva herramienta que le permite compartir un código base y su contexto con un compañero de equipo, de forma que se establezca una colaboración bidireccional instantánea directamente desde Visual Studio. Con Live Share, un compañero de equipo puede leer, navegar, editar y depurar un proyecto que ha compartido con él de forma segura y sin problemas.<br><br>Para obtener más información, vea [Live Share FAQ](/visualstudio/liveshare/faq) (Preguntas frecuentes sobre Live Share).<br><br>
* **[IntelliCode](https://visualstudio.microsoft.com/services/intellicode/)** , una nueva funcionalidad que mejora el desarrollo de software al usar IA para ofrecer mejores finalizaciones de código relacionadas con el contexto, guiar a los desarrolladores para que escriban código para los patrones y estilos de su equipo, encontrar problemas de código difíciles de captar y centrar las revisiones de código en áreas que importan de verdad. <br><br>Para obtener más información, vea [Preguntas más frecuentes de IntelliCode](/visualstudio/intellicode/faq).

¿Quiere saber más sobre lo que se está preparando de Visual Studio 2017? Vea la página [Guía básica de Visual Studio](/visualstudio/productinfo/vs2018-roadmap).

Y no olvide de revisar la versión más reciente, [Visual Studio 2019](whats-new-visual-studio-2019.md).

## <a name="contact-us"></a>Póngase en contacto con nosotros

¿Por qué enviar comentarios al equipo de Visual Studio? Porque tomamos los comentarios de los clientes muy en serio. Estos impulsan muchas de nuestras acciones.

Si quiere realizar sugerencias sobre cómo podemos mejorar Visual Studio u obtener más información sobre las opciones de soporte técnico de los productos, consulte la página [Envíenos sus comentarios](feedback-options.md).

### <a name="report-a-problem"></a>Notificar un problema

A veces, un mensaje no es suficiente para transmitir el impacto completo de un problema que ha detectado. Si experimenta un bloqueo u otro problema de rendimiento, puede compartir fácilmente los pasos de reproducción y los archivos auxiliares (como capturas de pantalla y archivos de seguimiento y volcado del montón) con nosotros mediante la herramienta **Notificar un problema**. Para obtener más información sobre cómo usar esta herramienta, vea la página [Cómo notificar un problema](how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Vea también

* [Notas de la versión de Visual Studio 2017](/visualstudio/releasenotes/vs2017-relnotes)
* [Novedades de Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)
* [Novedades de Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Novedades de C#](/dotnet/csharp/whats-new)
* [Novedades de Team Foundation Server](/tfs/server/whats-new?view=vsts)
* [Novedades de Visual Studio para Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
* [Novedades de Visual Studio 2019](whats-new-visual-studio-2019.md)
