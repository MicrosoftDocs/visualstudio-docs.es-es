---
title: Novedades de Visual Studio 2017 RC | Microsoft Docs
ms.custom: 
ms.date: 12/13/2016
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
ms.sourcegitcommit: 4fb097ab0ee0d45fd5727e3170db3393392abf23
ms.openlocfilehash: dc1941fd755c28039560b608733067b1da365c3a

---
# <a name="what39s-new-in-visual-studio-2017"></a>Novedades de Visual Studio 2017
Le damos la bienvenida a Visual Studio 2017 RC, un conjunto integrado de herramientas de productividad de desarrolladores, servicios en la nube y extensiones que permiten que usted y su equipo puedan crear fantásticas aplicaciones y juegos para Internet, la Tienda Windows, el escritorio, Android e iOS.  

En esta versión candidata para lanzamiento (RC) de nuestra última versión de Visual Studio, nos hemos centrado en las mejoras del rendimiento y la productividad. En cuanto al rendimiento, hemos conseguido que Visual Studio se inicie más rápido, tenga mayor capacidad de respuesta y use menos memoria que antes. Y en cuanto a la productividad, hemos agregado o actualizado características que pueden ayudarle a ser más eficaz mientras use Visual Studio.

> [!TIP]
> Para ver nuestra nueva RC en funcionamiento, vea el vídeo [Novedades de Visual Studio](https://channel9.msdn.com/events/connect/2016/159) en Channel 9.   

Aquí se muestra un resumen de alto nivel de los cambios que hemos realizado:

* **Aumento de la productividad**. Las mejoras realizadas en la navegación de código, IntelliSense, la refactorización, las correcciones de código y la depuración permiten ahorrarle tiempo y esfuerzo en las tareas cotidianas independientemente del lenguaje o la plataforma. Además, para aquellos equipos que adoptan DevOps, Visual Studio 2017 simplifica el bucle interior de desarrollo y agiliza el flujo de código con características en tiempo real totalmente nuevas, por ejemplo, Live Unit Testing y la validación de dependencias de arquitectura en tiempo real.
* **Redefinición de los aspectos básicos**.  Hay un enfoque renovado para mejorar la eficacia de las tareas esenciales que los desarrolladores deben abordar diariamente. Esto incluye una instalación ligera y modular totalmente nueva adaptada a las necesidades del desarrollador, un IDE más rápido desde el inicio hasta el apagado y una nueva manera de ver, editar y depurar cualquier código sin proyectos ni soluciones. Visual Studio 2017 ayuda a los desarrolladores a centrarse en el panorama general.
* **Desarrollo de Azure simplificado**. Un conjunto integrado de herramientas de Azure que permite a los desarrolladores crear con facilidad aplicaciones principalmente destinadas a la nube con tecnología de Microsoft Azure. Visual Studio facilita la configuración, la compilación, la depuración, el empaquetado y la implementación de aplicaciones y servicios en Microsoft Azure directamente desde el IDE.
* **Desarrollo móvil de cinco estrellas**. Con herramientas avanzadas de depuración y generación de perfiles y características de generación de pruebas unitarias, Visual Studio 2017 con Xamarin agiliza y simplifica más que nunca a los desarrolladores los procesos de compilación, conexión y ajuste de las aplicaciones móviles para Android, iOS y Windows. Los desarrolladores también pueden optar por desarrollar aplicaciones móviles mediante Apache Cordova o con el desarrollo de bibliotecas multiplataforma de Visual C++, todo en Visual Studio.  

A continuación se incluye más información sobre los cambios más destacados.

> [!NOTE]
> Para obtener una lista completa de las nuevas funciones y características en Visual Studio 2017 RC y su actualización de RC posterior, vea las [Notas de la versión](https://www.visualstudio.com/news/vs2015-vs). Y para obtener una lista de problemas y soluciones, vea la sección [Problemas conocidos](https://www.visualstudio.com/news/vs2015-vs#knownissues) de las notas de la versión.   

## <a name="performance-improvements"></a>Mejoras en el rendimiento

### <a name="a-new-setup-experience"></a>Una nueva experiencia de instalación  
[Descargue Visual Studio Enterprise 2017 RC](https://aka.ms/vs/15/preview/vs_enterprise) o [vea los requisitos de sistema de Visual Studio](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 Hemos rediseñado la experiencia de instalación de Visual Studio para que sea incluso más sencillo instalar solo las características que necesita, cuando las necesita. También hemos reducido el espacio al mínimo, de manera que Visual Studio se instale más rápidamente con menos impacto del sistema. Y, además, se desinstala sin errores.

 El cambio más importante que verá cuando instale Visual Studio es su nueva experiencia de instalación. En la pestaña **Cargas de trabajo**, verá opciones de instalación que están agrupadas para representar marcos, lenguajes y plataformas comunes, que abarcan todo, desde el desarrollo de escritorio de .NET hasta ciencia de datos con R, Python y F#.  

 ![Cuadro de diálogo de instalación de Visual Studio 2017 RC](../ide/media/willow1.png "VS2017RC_Setup_screen")

Seleccione las cargas de trabajo que necesita y cámbielas cuando sea necesario. La instalación más pequeña es de solo unos pocos cientos de megabytes, aunque todavía contiene soporte para la edición de código básico para más de veinte idiomas junto control de código fuente.

También hemos agregado diferentes maneras de instalar Visual Studio. ¿Quiere seleccionar sus propios componentes en lugar de usar cargas de trabajo? Simplemente seleccione la pestaña **Componentes individuales** del instalador. ¿Quiere instalar paquetes de idioma sin tener que cambiar la opción de idioma de Windows? Pulse la pestaña **Paquetes de idioma** del instalador.  

Para obtener más información sobre la nueva experiencia de instalación, incluidas instrucciones paso a paso para guiarle, vea nuestra página [Instalar Visual Studio](../install/install-visual-studio.md).


### <a name="start-visual-studio-faster"></a>Iniciar Visual Studio más rápido
Si Visual Studio detecta que el tiempo de inicio del IDE es lento, proporciona un nuevo Centro de rendimiento de Visual Studio para ayudarle a acelerar las cosas. El Centro de rendimiento muestra todas las extensiones y ventanas de herramientas que están ralentizando el inicio del IDE. Puede usarlo para mejorar el rendimiento de inicio determinando cuándo se inician las extensiones o si las ventanas de herramientas están abiertas en el inicio.

### <a name="decrease-solution-load-time"></a>Disminuir el tiempo de carga de la solución
Trabajar en soluciones que contienen más de 100 proyectos no significa que necesite trabajar en todos los archivos o proyectos a la vez. Ahora, puede editar y depurar sin esperar a que Visual Studio cargue cada proyecto. Para probar esto en proyectos administrados, active la **Carga de solución ligera** desde Herramientas > Opciones > Proyectos y soluciones.

  ![Cuadro de diálogo Opciones en Visual Studio 2017 RC](../ide/media/vs2017ide-LightweightSolutionLoad.PNG "VS2017RC Cuadro de diálogo Opciones - Carga de solución ligera")

### <a name="faster-on-demand-loading-of-extensions"></a>Carga de extensiones a petición más rápida
La idea es sencilla: cargar extensiones cuando sea necesario en lugar de cuando Visual Studio se inicie. En primer lugar, hemos movido nuestras extensiones de Python y Xamarin para cargarlas a petición y, en segundo lugar, estamos trabajando para mover todas las extensiones que se envían con Visual Studio &#151;y las extensiones que envían proveedores de terceros&#151; para este modelo. ¿Tiene curiosidad por saber qué extensiones afectan al inicio, la carga de la solución y el rendimiento de escritura? Puede ver esta información en Ayuda -> Administrar el rendimiento de Visual Studio.

  ![Cuadro de diálogo Opciones en Visual Studio 2017 RC](../ide/media/vs2017ide-ManageVSperf.png "VS2017RC Cuadro de diálogo Ayuda - Administración del rendimiento")

## <a name="productivity-improvements"></a>Mejoras de productividad

### <a name="sign-in-across-multiple-accounts"></a>Iniciar sesión en varias cuentas  
Hemos presentado un nuevo servicio de identidad en Visual Studio 2017 RC que le permite compartir cuentas de usuario en las herramientas de desarrollo de Microsoft, como Team Explorer, Azure Tools, publicación de la Tienda Windows, etc.

Además, puede mantener la sesión iniciada más tiempo; no le pediremos que inicie sesión de nuevo cada 12 horas. Para obtener más información, vea la publicación del blog [Fewer Visual Studio Sign-in Prompts](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/) (Menos mensajes emergentes de inicio de sesión en Visual Studio).

### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Administrar las extensiones con Roaming Extension Manager
Ahora es incluso más sencillo configurar cada entorno de desarrollo con sus extensiones favoritas cuando inicie sesión en Visual Studio. Nuestro nuevo Roaming Extension Manager mantiene el seguimiento de todas sus extensiones favoritas mediante la creación de una lista sincronizada en la nube.  

Para ver una lista de las extensiones de Visual Studio, haga clic en Herramientas > Extensiones y actualizaciones y, después, haga clic en Roaming Extension Manager.

![Visual Studio 2017 - Cuadro de diálogo Extensiones y actualizaciones](../ide/media/vs2017ide-ExtensionsAndUpdates.png "Visual Studio 2017 - Herramientas > Cuadro de diálogo Extensiones y actualizaciones")

Roaming Extension Manager realiza un seguimiento de todas las extensiones que instale, pero puede decidir las que quiere agregar a la lista de itinerancia.

![Visual Studio 2017 - Cuadro de diálogo Extensiones y actualizaciones](../ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 - Roaming Extension Manager")

Cuando use Roaming Extension Manager, verá 3 tipos de icono en la lista:
* ![Icono de extensión con perfil itinerante](../ide/media/vs2017ide-roamedicon.png "Icono de extensión con perfil itinerante") ***Icono de extensión con perfil itinerante***: una extensión que forma parte de esta lista de itinerancia, pero que no está instalada en el equipo.
  (Puede instalarlas mediante el botón **Descargar**).
* ![Icono de extensión con perfil itinerante e instalada](../ide/media/vs2017ide-roamedinstalledicon.png "Icono de extensión con perfil itinerante e instalada") ***Icono de extensión con perfil itinerante e instalada***: todas las extensiones que forman parte de la lista de itinerancia y que están instaladas en su entorno de desarrollo.
  (Si decide que no quiere usar un perfil itinerante, puede quitarlas mediante el botón **Detener itinerancia**).
* ![Icono de extensión instalada](../ide/media/vs2017ide-installedicon.png "Icono de extensión instalada") ***Icono de extensión instalada***: todas las extensiones que están instaladas en este entorno, pero no forman parte de la lista Itinerancia.
  (Puede agregar extensiones a la lista de itinerancia mediante el botón **Iniciar itinerancia**).

Estos iconos le muestran el estado actual de la lista. Puede tener extensiones en cualquier estado y personalizarlas tanto como quiera. Aunque también puede dejar que lo hagamos por usted. Cualquier extensión que descargue mientras tenga la sesión iniciada se agrega a la lista como **Extensión con perfil itinerante e instalada** y forma parte de la lista de itinerancia, con lo cual puede acceder a ella desde cualquier equipo.

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>Experimentar la validación en tiempo real de dependencias de arquitectura y Live Unit Testing

En Visual Studio Enterprise 2017 RC, si ha configurado los diagramas de validación de dependencias (también conocidos como  diagramas de capas), ahora puede recibir notificaciones en tiempo real de infracciones de reglas de dependencias de arquitectura a medida que escribe código en el Editor de código.

Los errores aparecen en la Lista de errores y los subrayados ondulados del editor de texto le muestran la ubicación exacta de la infracción. Ahora es menos probable introducir dependencias no deseadas.

![Validación dinámica de arquitectura](../ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "Validación dinámica de arquitectura")

#### <a name="live-unit-testing"></a>Live Unit Testing:

Live Unit Testing es una característica nueva que estamos presentando y que solo está presente en la edición Enterprise de Visual Studio. Esta característica visualiza los resultados de las pruebas unitarias y la cobertura de código en vivo en el editor, mientras codifica. Funciona con proyectos de C#/VB para .NET Framework y admite tres marcos de prueba de MSTest, xUnit y NUnit.

### <a name="visual-studio-ide-enhancements"></a>Mejoras del IDE de Visual Studio
#### <a name="interact-with-git"></a>Interactuar con Git:
Los controles de la esquina inferior del IDE de Visual Studio le permiten confirmar y publicar rápidamente sus proyectos en Git y administrar sus repositorios de Git.

![Cuadro de diálogo de instalación de Visual Studio 2017 RC](../ide/media/vsIDE-GitInteraction.png "Git-tools-in-the-VS2017RC-IDE")

#### <a name="view-and-navigate-code-with-structure-visualizer"></a>Ver y navegar por el código con Structure Visualizer:
Una nueva característica denominada Structure Visualizer está disponible en el editor de código de Visual Studio. Esta característica muestra pautas verticales entre áreas anidadas de código, lo que facilita la visión y navegación por el código. Esta característica está disponible para todos los lenguajes respaldados por TextMate así como para Visual C#, Visual Basic y XAML.

![Cuadro de diálogo de instalación de Visual Studio 2017 RC](../ide/media/vsIDE-StructureVisualizer.png "Structure-Visualizer-in-VS2017RC")

#### <a name="experience-an-improved-navigate-to"></a>Experiencia mejorada de Navegar a:
Hemos mejorado la función Navegar a: se ha simplificado la ventana Navegar a y se ha agregado compatibilidad para caracteres de filtro adicionales que le permiten restringir las búsquedas de código.

#### <a name="create-apps-in-even-more-programming-languages"></a>Crear aplicaciones en más lenguajes de programación:
Puede crear aplicaciones en Visual Studio con un número mayor de lenguajes de programación que en las versiones anteriores, y las soluciones y los proyectos ya no son necesarios. Su código obtiene coloración de sintaxis, finalización de instrucciones básica y, en algunos casos, la función Navegar a y compatibilidad adicional. Si su lenguaje favorito no se admite, puede crear compatibilidad para este con TextMate Grammars.

### <a name="visual-c"></a>Visual C++
Visual Studio 2017 RC incluye muchas actualizaciones y revisiones del entorno de Visual C++. Hemos corregido más de 250 errores y problemas notificados en el compilador y las herramientas, muchos enviados por los usuarios a través de [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect").

También hemos realizado varias mejoras para incluir la distribución de C++ Core Guidelines con Visual Studio, la actualización del compilador mediante la adición de compatibilidad mejorada para características de C++11 y C++, la adición y actualización de las funciones de las bibliotecas de C++, y la mejora del rendimiento del IDE de C++ y las cargas de trabajo de instalación entre otros.

Para obtener información completa, vea nuestra página [What's New for Visual C++ in Visual 2017 RC](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio) (Novedades de Visual C++ en Visual 2017 RC).  


### <a name="debugging-and-diagnostics"></a>Depuración y diagnósticos
La depuración es más rápida ahora y no provoca retrasos mientras está editando.

Por ejemplo: en una versión anterior de Visual Studio, presentamos lo que se conoce como el proceso de hospedaje para proyectos de consola administrada, Windows Forms y WPF a fin de que la depuración fuera más rápida mediante el desarrollo de un proceso en segundo plano que se usase en la siguiente sesión de depuración. Esta característica bienintencionada estaba provocando que Visual Studio no respondiera temporalmente durante unos segundos cuando detenía la depuración o usaba Visual Studio después de que finalizara la sesión de depuración.

En Visual Studio 2017, hemos desactivado el proceso de hospedaje y hemos optimizado la depuración, de manera que sea igual de rápida sin el proceso de hospedaje, e incluso más rápida para proyectos que nunca han usado el proceso de hospedaje (como proyectos de ASP.NET, Windows universal y C++).

#### <a name="run-to-click"></a>Hacer clic y ejecutar:
Ahora, mientras está realizando la depuración, puede hacer clic en el icono junto a una línea de código para ejecutar esa línea. Ya no tiene que establecer puntos de interrupción temporales ni realizar varios pasos para ejecutar el código y detenerse en la línea que quiere.

![Depuración de Visual Studio 2017 RC - Hacer clic y ejecutar](../ide/media/vs2017ide-RunToClick.png "Hacer clic y ejecutar en Visual Studio 2017, depuración y diagnóstico")

#### <a name="the-new-exception-helper"></a>La nueva aplicación auxiliar de excepciones:

Puede usar la nueva aplicación auxiliar de excepciones para ver la información de excepción de un vistazo en un cuadro de diálogo no modal compacto con acceso instantáneo a las excepciones internas.

Vea rápidamente qué referencias son nulas en la aplicación auxiliar de excepciones al diagnosticar una excepción NullReferenceException.

También puede excluir tipos de excepciones de interrupción producidas desde módulos específicos al hacer clic en la casilla para agregar una condición mientras se detiene en la excepción producida.

![Cuadro de diálogo de la nueva aplicación auxiliar de excepciones](../ide/media/vs2017ide-ExceptionHelper.png "Cuadro de diálogo de la nueva aplicación auxiliar de excepciones")

Para obtener más información, vea la publicación del blog [Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) (Usar la nueva aplicación auxiliar de excepciones en Visual Studio).

## <a name="talk-to-us"></a>Hable con nosotros  
 ¿Por qué enviar comentarios al equipo de Visual Studio? Porque tomamos los comentarios de los clientes muy en serio. Estos impulsan muchas de nuestras acciones.  

Si quiere realizar sugerencias sobre cómo podemos mejorar Visual Studio o notificar un problema, vea la página [Hable con nosotros](../ide/talk-to-us.md) para obtener más información.  

### <a name="report-a-problem"></a>Notificar un problema  
 A veces, un mensaje no es suficiente para transmitir el impacto completo de un problema que ha detectado. Si experimenta un bloqueo u otro problema de rendimiento, puede compartir fácilmente los pasos de reproducción y los archivos auxiliares (como capturas de pantalla y archivos de seguimiento y volcado del montón) con nosotros mediante la herramienta **Notificar un problema**. Para obtener más información sobre cómo usar esta herramienta, vea la página [Cómo notificar un problema](how-to-report-a-problem-with-visual-studio-2017.md).  

### <a name="track-your-issue-in-connect"></a>Realice un seguimiento de su problema en Connect  
 Si quiere realizar un seguimiento del estado de su comentario sobre Visual Studio, simplemente vaya a [Connect](http://connect.microsoft.com/) y notifique el error allí. Después de notificarlo, puede volver a Connect para realizar un seguimiento de su estado.  

## <a name="see-also"></a>Vea también  
* [What's New in Visual C++ (Novedades de Visual C++)](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [What's New in C# (Novedades de C#)](https://docs.microsoft.com/en-us/dotnet/articles/csharp/csharp-7)  
* [What's New for Team Foundation Server (Novedades de Team Foundation Server)](https://www.visualstudio.com/en-us/docs/whats-new)
* [Notas de la versión de Visual Studio](https://www.visualstudio.com/news/vs2015-vs)



<!--HONumber=Feb17_HO4-->


