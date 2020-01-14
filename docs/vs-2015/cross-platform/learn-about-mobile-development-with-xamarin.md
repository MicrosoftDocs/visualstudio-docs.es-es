---
title: Más información sobre el desarrollo móvil con Xamarin | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: a362bd4eef2a48667c67c03e940e213fc960418b
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919002"
---
# <a name="learn-about-mobile-development-with-xamarin"></a>Más información sobre el desarrollo móvil con Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tema le dirige a material de información general que le ayudará a comprender el desarrollo aplicaciones móviles multiplataforma con Xamarin. Si aún no tiene instalado Visual Studio y Xamarin, inicie primero el proceso [Configuración e instalación](../cross-platform/setup-and-install.md) y, después, regrese aquí para trabajar con estos recursos mientras se ejecutan los instaladores.  
  
> [!NOTE]
> A menos que se indique lo contrario, se recomienda leer inicialmente solo aquellas páginas vinculadas directamente aquí y no página subsidiarias. Si el proceso de instalación sigue ejecutándose después de completar esta lista, puede volver atrás y explorar otros temas.  
>   
> También puede consultar los temas marcados como "Conceptos básicos" y volver a los temas "En profundidad" más adelante.  
  
## <a name="essentials-introduction-to-xamarin"></a>Conceptos básicos: introducción a Xamarin  
 *10-20 minutos*  
  
1. [Aplicaciones móviles en Visual Studio con Xamarin](https://www.visualstudio.com/explore/xamarin-vs) (visualstudio.com) ofrece un breve resumen de las características principales de Xamarin.  
  
2. [Building Cross-Platform Mobile Apps using C# and Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (Compilación de aplicaciones móviles multiplataforma con C# y Visual Studio) en Channel 9, 15 m 16 s, con el predicador de Xamarin, James Montemagno. Los primeros tres minutos son una introducción a Xamarin, seguida de demostraciones de código.  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Conceptos básicos: información general del entorno de Visual Studio y Xamarin  
 *5-15 minutos*  
  
- El equipo Windows con Visual Studio y Xamarin es donde realizará la mayor parte de su trabajo. En este equipo se compilan directamente las aplicaciones de Windows y Android, que se ejecutan y depuran en un dispositivo o un emulador. Las aplicaciones de iOS también se compilan, ejecutan y depuran de forma remota a través del Mac. Visual Studio en el equipo Windows también se puede conectar al diseñador de guiones gráficos de iOS y al simulador de iOS.  
  
- El Mac con Xcode y Xamarin actúa como el host de compilación/firma y el entorno en tiempo de ejecución para las aplicaciones de iOS. Las compilaciones para iOS desde Visual Studio en el equipo Windows se delegan a este Mac. Cuando se depura una aplicación de iOS desde Visual Studio, se ejecuta en el simulador de iOS en el Mac o directamente en un dispositivo anclado a red conectado al Mac. En este caso, deberá interactuar con la aplicación en el Mac (o cerca de este) y realizar la depuración en Visual Studio.  
  
  A continuación se ilustran estas relaciones y puede obtener información sobre el uso de aplicaciones de iOS en [Introduction to Xamarin.iOS for Visual Studio](/xamarin/ios/get-started/installation/windows/introduction-to-xamarin-ios-for-visual-studio) (Introducción a Xamarin.iOS con Visual Studio) en xamarin.com.  
  
  ![La relación entre los equipos de desarrollo de Windows y Mac en un entorno de Xamarin](../cross-platform/media/crossplat-xamarin-learn-1.png "CrossPlat Xamarin Learn 1")  
  
## <a name="essentials-how-projects-are-structured"></a>Conceptos básicos: cómo se estructuran los proyectos  
 *10-30 minutos*  
  
1. [Sharing Code Options](/xamarin/cross-platform/app-fundamentals/code-sharing) (Opciones de uso compartido de código) en xamarin.com Se recomienda mediante la opción de bibliotecas de clases portables, en las que resulta más fácil usar solo las API de .NET compatibles con todas las plataformas de destino. La mayoría del código de lógica de negocios residirá en la PCL, incluidos el acceso a las bases de datos, las llamadas a las API de REST y las llamadas a componentes de Xamarin portables (vea [Deeper Dive: Xamarin Components](#components) al final de este tema). El código de interfaz de usuario común escrito con Xamarin.Forms también puede residir en una PCL.  
  
2. (Opcional) [Case Study: Tasky](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky) (Caso práctico: Tasky) en xamarin.com. Se describen algunos procedimientos recomendados para el diseño y la estructura de una aplicación completa, como la estructura del proyecto con una PCL para disponer de código compartido que separe los datos, el acceso a datos y las capas de negocio.  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Conceptos básicos: capas de la interfaz de usuario de Xamarin.Forms y Native  
 *10-40 minutos*  
  
 Xamarin ofrece dos formas de compilar magníficas aplicaciones nativas: Xamarin Native y Xamarin.Forms.  
  
 Con Xamarin Native puede escribir código de interfaz de usuario independiente para cada plataforma de destino: iOS, Android y Windows.  Con este enfoque tiene acceso directo a API específicas de la plataforma que permiten una experiencia de interfaz de usuario personalizada para cada plataforma.  También tendrá acceso total al diseñador y los controles nativos de cada plataforma como ayuda en la creación de la interfaz de usuario correspondiente.  
  
 Xamarin.Forms ofrece un conjunto generalizado de API que permiten escribir una capa de interfaz de usuario compartida para todas las plataformas de una biblioteca de clases portable.  Xamarin.Forms se representa en controles nativos en cada plataforma de destino para dar una apariencia nativa.  En lugar de utilizar un diseñador, con Xamarin.Forms se compila la interfaz de usuario con C# y XAML.  
  
 No es necesario decidir por adelantado qué método se seguirá; las aplicaciones se pueden implementar con una combinación de Xamarin.Forms y Xamarin Native:  
  
- Use Xamarin.Forms para compilar pantallas de uso general que ofrezcan una interfaz de usuario y funcionalidades similares entre plataformas, como los inicios de sesión, los formularios de contacto y los resultados de búsqueda.  
  
- Use una variedad de funcionalidades de personalización de Xamarin.Forms para ajustar la interfaz de usuario según la plataforma. Se incluyen la API OnPlatform que puede usarse tanto desde código como desde XAML, la creación de una vista personalizada, la extensión de un representador existente y la creación de un representador personalizado.  
  
- Si es necesario, use Xamarin Native para compilar pantallas que usen características de interfaz de usuario únicas de cada plataforma; por ejemplo, una pantalla que use la captura de cámara y la manipulación de imágenes nativas.  
  
  Se recomienda que comience siempre a partir de una solución de Xamarin.Forms para configurar el uso compartido del código de la interfaz de usuario entre plataformas y la utilización de las capacidades de personalización para realizar ajustes específicos de la plataforma. En los casos en que necesite pantallas completamente específicas de la plataforma, puede agregarlas individualmente con Xamarin Native.  
  
  Para más información:  
  
1. [Xamarin.Forms](/xamarin/xamarin-forms/) (xamarin.com) proporciona una breve introducción, y las ventajas y desventajas de Xamarin.Forms frente a las capas de interfaz de usuario nativa (es decir, Xamarin.iOS y Xamarin.Android).  
  
2. Los primeros tres minutos del vídeo de James Montemagno [Xamarin.Forms: aplicaciones nativas de iOS, Android y Windows con C# y XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (Channel9, 13 m 3 s) ofrecen otra visión general y permiten ver otras demostraciones.  
  
3. (Opcional) [An Introduction to Xamarin.Forms](/xamarin/get-started/quickstarts/deepdive?pivots=windows) (Una introducción a Xamarin.Forms) en xamarin.com  
  
4. (Opcional) Vea ejemplos del uso de OnPlatform para la personalización en la documentación de [Device Class](/xamarin/xamarin-forms/platform/device) (Clase Device) en xamarin.com  
  
5. (Opcional) [Multiplataforma: compartir código de la interfaz de usuario en plataformas móviles con Xamarin.Forms](https://msdn.microsoft.com/magazine/dn904669.aspx) por Jason Smith (MSDN Magazine) es un artículo en el que se describen las distintas opciones de personalización de Xamarin.Forms, cuyos detalles se tratan en [Customizing Controls on Each Platform](/xamarin/xamarin-forms/app-fundamentals/custom-renderer/) (Personalizar los controles en cada plataforma) en xamarin.com.  
  
## <a name="deeper-dive-debugging-with-emulators"></a>En profundidad: depuración con emuladores  
 *10-15 minutos*  
  
 Para depurar las aplicaciones entre plataformas sin tener que usar un dispositivo físico, necesitará utilizar lo siguiente:  
  
1. **Un emulador de Android.** Según la versión de Windows que esté utilizando, se recomienda el emulador de Microsoft Visual Studio para Android o Xamarin Player, los cuales ofrecen un rendimiento rápido y admiten una variedad de funcionalidades de dispositivo:  
  
    - **Máquinas de Windows 8 y versiones posteriores:** se recomienda usar el [emulador de Microsoft Visual Studio para Android](https://www.visualstudio.com/features/msft-android-emulator-vs.aspx), que se instala con Visual Studio.  En el vídeo [Visual Studio Emulator for Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) (Emulador de Visual Studio para Android) de Channel9 (5 m 55 s), se ofrece información general y una demostración  
  
    - **Windows 7 o versiones anteriores, o Windows ejecutándose en Mac OS X**: use [Xamarin Android Player](/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (xamarin.com).  
  
2. **Simulador de iOS de Apple.** Para más información, lea [Getting Started with the iOS Simulator](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (Introducción al simulador de iOS) en apple.com.  
  
3. **Emulador de Microsoft Windows Phone.** Para obtener más información, lea [Windows Phone Emulator for Windows Phone 8](https://msdn.microsoft.com/library/dn632391.aspx)(Emulador de Windows Phone para Windows Phone 8).  
  
## <a name="components"></a> Deeper Dive: Xamarin Components  
 *10 minutos*  
  
 Muchas de las capacidades extendidas están disponibles para aplicaciones de Xamarin a través de los componentes de Xamarin. Puede encontrar el catálogo completo disponible para descargar en [http://components.xamarin.com/](/xamarin/cross-platform/troubleshooting/component-nuget?tabs=windows), que incluye componentes para los controles de interfaz de usuario adicionales, autenticación, una variedad de servicios en la nube, como Microsoft Azure, y mucho más.
