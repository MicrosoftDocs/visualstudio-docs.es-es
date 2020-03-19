---
title: Desarrollo móvil multiplataforma en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- multiple
ms.openlocfilehash: c7f40f656b533949748a7eb2ab88ea3d2b1d5923
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "78234987"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Desarrollo móvil multiplataforma en Visual Studio

Puede crear aplicaciones para dispositivos Android, iOS y Windows con Visual Studio.  Al diseñar la aplicación, use las herramientas de Visual Studio para agregar fácilmente servicios conectados, como Office 365, Azure App Service y Application Insights.

Crear aplicaciones mediante C# y .NET Framework, HTML y JavaScript o C++. Comparta código, cadenas, imágenes y, en algunos casos, incluso la interfaz de usuario.

Si quiere compilar un juego o una aplicación gráfica inmersiva, instale Visual Studio Tools para Unity y disfrute de las eficaces características de productividad de Visual Studio con Unity, el popular entorno de desarrollo y motor multiplataforma de juegos y gráficos para aplicaciones que se ejecuta en iOS, Android, Windows y otras plataformas.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Compilación de una aplicación para Android, iOS y Windows (.NET Framework)

![Dispositivos](../cross-platform/media/homedevices.png "HomeDevices")

Con Visual Studio Tools para Xamarin, puede tener como destino Android, iOS y Windows en la misma solución, compartir código e incluso la interfaz de usuario.

|**Más información**|
|--------------------|
|[Instalar Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Obtener información acerca de Xamarin en Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Documentación de desarrollo de aplicaciones móviles de Xamarin](/xamarin/) |
|[DevOps con aplicaciones de Xamarin](/xamarin/tools/ci/devops/) |
|[Obtener información acerca de las aplicaciones de Windows universales en Visual Studio](https://visualstudio.microsoft.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Obtener información acerca de las similitudes entre Swift y C#](https://aka.ms/scposter) (download.microsoft.com)|

### <a name="AndroidHTML"></a> Tener como destino Android, iOS y Windows desde una sola base de código

 Puede compilar aplicaciones nativas para Android, iOS y Windows usando C# o F# (Visual Basic no se admite en este momento).  Para empezar, instale Visual Studio y seleccione la opción **Desarrollo para dispositivos móviles con .NET** en el programa de instalación.

 Si ya tiene Visual Studio instalado, vuelva a ejecutar el **Instalador de Visual Studio** y seleccione la misma opción **Desarrollo para dispositivos móviles con .NET** para Xamarin (como anteriormente).

 Cuando termine, las plantillas de proyecto aparecen en el cuadro de diálogo **Nuevo proyecto**. La manera más fácil de encontrar las plantillas de Xamarin es buscar por "Xamarin".

 Xamarin expone la funcionalidad nativa de Android, iOS y Windows como clases y métodos .NET. Esto significa que las aplicaciones tienen acceso total a las API y a los controles nativos, y la misma capacidad de respuesta que las aplicaciones escritas en los lenguajes nativos de la plataforma.

 Después de crear un proyecto, podrá aprovechar todas las características de productividad de Visual Studio. Por ejemplo, podrá usar un diseñador para crear páginas y usar IntelliSense para explorar las API nativas de las plataformas móviles. Cuando esté listo para ejecutar la aplicación y ver su aspecto, puede usar el emulador de Android SDK y ejecutar aplicaciones Windows de forma nativa. También puede usar directamente dispositivos Android y Windows anclados a red. Para los proyectos de iOS, conéctese a un equipo Mac en red e inicie el emulador de iOS desde Visual Studio, o conéctese a un dispositivo anclado a red.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Diseñar un conjunto de páginas que se representan en todos los dispositivos mediante Xamarin.Forms

 Según la complejidad del diseño de las aplicaciones, puede considerar la posibilidad de compilarlas usando plantillas *Xamarin.Forms* en el grupo **Aplicaciones móviles** de plantillas de proyecto. Xamarin.Forms es un kit de herramientas de interfaz de usuario que permite crear una única interfaz de usuario que puede compartir entre Android, iOS y Windows.  Al compilar una solución Xamarin.Forms, obtendrá una aplicación Android, una aplicación iOS y una aplicación Windows. Para obtener más detalles, vea [Más información sobre el desarrollo móvil con Xamarin](/xamarin/cross-platform/get-started/introduction-to-mobile-development/) y la [Documentación de Xamarin.Forms](/xamarin/xamarin-forms/).

#### <a name="ShareHTML"></a> Compartir código entre aplicaciones de Android, iOS y Windows

 Si no está usando Xamarin.Forms y opta por un diseño individual para cada plataforma, puede compartir la mayor parte del código que no sea de interfaz de usuario entre los proyectos de plataforma (Windows, iOS y Android). Esto incluye cualquier lógica de negocios, la integración en la nube, el acceso a bases de datos o cualquier otro código que tenga como destino .NET Framework. El único código que no se puede compartir es el código que tiene como destino una plataforma específica.

 ![Compartir código entre las interfaces de usuario de Windows, iOS y Android](../cross-platform/media/sharecode.png "ShareCode")

 El código se puede compartir mediante un proyecto compartido, un proyecto de Biblioteca de clases portable o ambos. Posiblemente verá que algunos códigos encajan mejor en un proyecto compartido y que otros tienen más sentido dentro de un proyecto de Biblioteca de clases portable.

|**Más información**|
|--------------------|
|[Sharing Code Options (Opciones de uso compartido de código)](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[Opciones de uso compartido de código con .NET](/dotnet/standard/cross-platform/) |

### <a name="WindowsHTML"></a> Tener como destino dispositivos Windows 10

 ![Dispositivos Windows](../cross-platform/media/windowsdevices.png "Dispositivos Windows")

 Si quiere crear una única aplicación que tenga como destino la gran variedad de dispositivos de Windows 10, cree una aplicación de Windows universal. Podrá diseñar la aplicación usando un solo proyecto y las páginas se representarán correctamente en cualquier dispositivo que se use para verlas.

 Comience con una plantilla de proyecto de aplicación para Plataforma universal de Windows (UWP). Diseñe visualmente las páginas y, después, ábralas en una ventana de vista previa para ver cómo se ven en diversos tipos de dispositivos. Si no le gusta cómo se muestra una página en un dispositivo, puede optimizar la página para ajustarla mejor al tamaño de pantalla, la resolución o las distintas orientaciones, como el modo vertical o el horizontal. Puede hacer todo eso con opciones de menú de fácil acceso y ventanas de herramientas intuitivas en Visual Studio. Cuando esté listo para ejecutar la aplicación y recorrer el código, encontrará todos los emuladores de dispositivos y los simuladores de diferentes tipos de dispositivos en una lista desplegable que se encuentra en la barra de herramientas **Estándar**.

|**Más información**|
|--------------------|
|[Introducción a la Plataforma universal de Windows](/windows/uwp/get-started/universal-application-platform-guide)|
|[Crear la primera aplicación](/windows/uwp/get-started/your-first-app)|
|[Desarrollar aplicaciones para la Plataforma universal de Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migrar aplicaciones a la Plataforma universal de Windows (UWP)](https://msdn.microsoft.com/library/mt148501.aspx)|

::: moniker range="vs-2017"

## <a name="HTML"></a> Compilar una aplicación para Android, iOS y Windows (HTML/JavaScript)

 ![Dispositivos Windows, iOS y Android](../cross-platform/media/homedevices.png "Dispositivos Windows, iOS y Android")

 Si es un desarrollador web familiarizado con HTML y JavaScript, puede usar Visual Studio Tools para Apache Cordova para crear una aplicación que tenga como destino iOS, Android y Windows. Estas aplicaciones pueden destinarse a las tres plataformas y puede crearlas con las habilidades y los procesos con los que esté más familiarizado.

 Apache Cordova es un marco que incluye un modelo de complementos. Este modelo de complementos proporciona una única API de JavaScript que puede usar para tener acceso a las características de dispositivo nativas de las tres plataformas (Android, iOS y Windows).

 Como estas API son multiplataforma, puede compartir la mayor parte de lo que escriba entre las tres plataformas. Esto reduce los costos de desarrollo y mantenimiento. Además, no es necesario empezar desde cero. Si creó otros tipos de aplicaciones web, puede compartir esos archivos con la aplicación Cordova sin tener que modificarlas ni rediseñarlas de manera alguna.

 ![Aplicaciones híbridas multidispositivo con JavaScript](../cross-platform/media/multidevicehybridapps.png "Aplicaciones híbridas multidispositivo con JavaScript")

 Para empezar, instale Visual Studio y elija la característica **Desarrollo para dispositivos móviles con JavaScript** durante la instalación. Las herramientas de Cordova instalan automáticamente todo el software de terceros necesario para compilar una aplicación multiplataforma.

 Después de instalar la extensión, abra Visual Studio y cree un proyecto **Aplicación vacía (Apache Cordova)** . Después, desarrolle la aplicación usando JavaScript o TypeScript. También puede agregar complementos para ampliar la funcionalidad de la aplicación; a medida que escriba código, aparecerán las API de los complementos en IntelliSense.

 Cuando esté listo para ejecutar la aplicación y examinar el código, seleccione un emulador, como el emulador Apache Ripple o Android Emulator, un explorador, o bien un dispositivo que esté conectado directamente al equipo. Después, inicie la aplicación. Si está desarrollando su aplicación en un equipo con Windows, puede incluso ejecutarla en él. Todas estas opciones están integradas en Visual Studio como parte de Visual Studio Tools para Apache Cordova.

 Las plantillas de proyecto para crear aplicaciones para Plataforma universal de Windows (UWP) siguen estando disponibles en Visual Studio, así que no dude en usarlas si solo va a tener como destino dispositivos de Windows. Si más adelante decide tener como destino Android e iOS, siempre puede trasladar el código a un proyecto de Cordova.

|**Más información**|
|--------------------|
|[Instalar Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Introducción a Herramientas para Apache Cordova de Visual Studio](/visualstudio/cross-platform/tools-for-cordova/)|
|[Obtener información acerca del emulador de Visual Studio para Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

::: moniker-end

<a name="CPP"></a>

## <a name="build-an-app-for-android-ios-and-windows-c"></a>Compilar una aplicación para Android, iOS y Windows (C++)

![Use C&#43;&#43; para compilar para Android, iOS y Windows](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 Primero, instale Visual Studio y la carga de trabajo **Desarrollo móvil con C++** . Después, puede compilar una aplicación native-activity para Android o una aplicación que tenga como destino Windows o iOS. Puede tener como destino Android, iOS y Windows en la misma solución si quiere y, después, compartir código entre ellos mediante una biblioteca compartida estática o dinámica multiplataforma.

 Si necesita compilar una aplicación para Android que requiere algún tipo de manipulación de gráficos avanzada, como un juego, puede hacerlo con C++. Comience con el proyecto **Aplicación native-activity (Android)** . Este proyecto es totalmente compatible con la cadena de herramientas Clang.

 ![Plantilla de proyecto native-activity](../cross-platform/media/cross-plat_cpp_native.png "Plantilla de proyecto native-activity")

 Cuando esté listo para ejecutar la aplicación y ver su aspecto, use Android Emulator. Es rápido, fiable y fácil de instalar y configurar.

 También puede compilar una aplicación que tenga como destino todos los dispositivos con Windows 10 mediante C++ y una plantilla de proyecto de aplicación para Plataforma universal de Windows (UWP). Obtenga más información sobre este punto en la sección [Tener como destino dispositivos Windows 10](#WindowsHTML), anteriormente en este tema.

 Puede compartir código de C++ entre Android, iOS y Windows mediante la creación de una biblioteca compartida estática o dinámica.

 ![Bibliotecas compartidas estáticas y dinámicas](../cross-platform/media/cross_plat_cpp_libraries.png "Bibliotecas compartidas estáticas y dinámicas")

 Puede usar dicha biblioteca en un proyecto de Windows, iOS o Android, como los descritos anteriormente en esta sección. Puede también usarla en una aplicación compilada con Xamarin, Java o cualquier lenguaje que permite invocar funciones en una DLL no administrada.

 A medida que escribe código en estas bibliotecas, puede usar IntelliSense para explorar las API nativas de las plataformas de Android y Windows. Estos proyectos de biblioteca están totalmente integrados con el depurador de Visual Studio para que pueda establecer puntos de interrupción, recorrer el código y buscar y corregir problemas mediante todas las características avanzadas del depurador.

|**Más información**|
|--------------------|
|[Descarga de Visual Studio](https://visualstudio.microsoft.com/downloads/) (VisualStudio.com)|
|[Instalación del desarrollo móvil multiplataforma con C++](/cpp/cross-platform/install-visual-cpp-for-cross-platform-mobile-development)|
|[Obtener información acerca de cómo usar C++ para varias plataformas de destino](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Instalar lo necesario y crear una aplicación de actividad nativa para Android](/cpp/cross-platform/create-an-android-native-activity-app)|
|[Obtener información acerca de cómo compartir código de C++ con aplicaciones Android y Windows](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Ejemplos de desarrollo móvil multiplataforma para C++](/cpp/cross-platform/cross-platform-mobile-development-examples)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Compilar un juego multiplataforma para Android, iOS y Windows con Visual Studio Tools para Unity

 Visual Studio Tools para Unity es una extensión gratuita para Visual Studio que integra las eficaces herramientas de edición de código, productividad y depuración de Visual Studio con *Unity*, el popular motor y entorno de desarrollo multiplataforma de juegos y gráficos para aplicaciones inmersivas destinadas a Windows, iOS, Android y otras plataformas, incluida la Web.

 ![Entorno de desarrollo de VSTU](../cross-platform/media/vstu_overview.png "Información general de Visual Studio Tools para Unity")

 Con Visual Studio Tools para Unity (VSTU), puede usar Visual Studio para escribir scripts de editor y juegos en C# y, a continuación, usar su eficaz depurador para buscar y corregir errores. La versión más reciente de VSTU aporta compatibilidad con Unity 2018.1 e incluye colores de sintaxis del lenguaje de sombreado ShaderLab de Unity, una mejor sincronización con Unity, una depuración más completa y una generación de código mejorada para el asistente de MonoBehavior. VSTU también integra los archivos de proyecto de Unity, los mensajes de la consola y la capacidad de iniciar el juego en Visual Studio, de modo que pueda dedicar menos tiempo a conmutar con el editor de Unity al escribir código.

|**Más información**|
|--------------------|
|[Obtener información acerca de la compilación de juegos Unity con Visual Studio](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[Más información sobre Visual Studio Tools para Unity](../cross-platform/visual-studio-tools-for-unity.md) |
|[Empezar a usar Visual Studio Tools para Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) |
|[Obtener más información acerca de las mejoras más recientes de Visual Studio Tools para Unity 2.0 Preview](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (blog de Visual Studio)|
|[Ver un vídeo de introducción a Visual Studio Tools para Unity 2.0 Preview](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (vídeo)|
|[Obtener información acerca de Unity](https://unity.com/) (sitio web de Unity)|

## <a name="see-also"></a>Vea también

- [Agregar las API de Office 365 a un proyecto de Visual Studio](/office/developer-program/office-365-developer-program)
- [Azure App Services: aplicaciones móviles](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](/appcenter)
