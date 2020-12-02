---
title: Paseo por Visual Studio para Mac
description: Visual Studio para Mac proporciona un entorno de desarrollo integrado para compilar aplicaciones .NET en macOS, incluidos sitios web de ASP.NET Core y proyectos de Xamarin para iOS, Android, Mac y Xamarin.Forms.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: a2caadd454564b389f48987e69e1bc08475affea
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190192"
---
# <a name="visual-studio-2019-for-mac-tour"></a>Paseo por Visual Studio 2019 para Mac

Visual Studio para Mac es un _entorno de desarrollo integrado_ de .NET en Mac que se puede usar para editar, depurar y compilar código y, después, publicar una aplicación. Además de un editor de código y un depurador, Visual Studio para Mac incluye compiladores, herramientas de finalización de código, diseñadores gráficos y características de control de código fuente para facilitar el proceso de desarrollo de software.

Visual Studio para Mac admite muchos de los mismos tipos de archivo que su equivalente de Windows, como `.csproj`, `.fsproj` o `.sln`, y admite características como EditorConfig, lo que significa que puede usar el IDE que mejor le convenga.
La creación, la apertura y el desarrollo de una aplicación son experiencias familiares para cualquiera que haya usado anteriormente Visual Studio en Windows. Además, Visual Studio para Mac emplea muchas de las eficaces herramientas que convierten a su equivalente de Windows en un IDE tan eficaz. La plataforma de compilador Roslyn se usa para la refactorización e IntelliSense. Su sistema de proyecto y motor de compilación usan MSBuild, mientras que su editor de código fuente usa la misma base que Visual Studio en Windows. Usa los mismos motores de depuración para las aplicaciones .NET Core y Xamarin y los mismos diseñadores para Xamarin.iOS y Xamarin.Android.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Qué puedo hacer en Visual Studio para Mac

Visual Studio para Mac admite los siguientes tipos de desarrollo:

- Aplicaciones web de ASP.NET Core con C#, F# y compatibilidad con páginas de Razor, JavaScript y TypeScript
- Aplicaciones de consola .NET Core con C# o F#
- Aplicaciones y juegos de Unity multiplataforma con C#
- Aplicaciones de Android, iOS, tvOS y watchOS en Xamarin con C# o F# y XAML
- Aplicaciones de escritorio de Cocoa en C# o F#

En este artículo se analizan varias secciones de Visual Studio para Mac y se ofrece una visión general de algunas de las características que lo convierten en una herramienta eficaz para crear estas aplicaciones.

## <a name="ide-tour"></a>Paseo por el IDE

Visual Studio para Mac se organiza en varias secciones para administrar archivos de aplicación y configuraciones, crear código de aplicación y depurar.

## <a name="getting-started"></a>Introducción

Al iniciar Visual Studio 2019 para Mac por primera vez, los nuevos usuarios verán una ventana de inicio de sesión. Inicie sesión con una cuenta Microsoft para activar una licencia de pago, si tiene una, o haga clic en el vínculo para consultar las suscripciones de Azure. Puede presionar **Lo haré más tarde** e iniciar sesión más adelante desde el elemento de menú **Visual Studio > Iniciar sesión**:

![Iniciar sesión en su cuenta de Microsoft](media/ide-tour-2019-start-signin.png)

Después, se le ofrecerá la opción de seleccionar los métodos abreviados de teclado que prefiera para personalizar el IDE: Visual Studio para Mac, Visual Studio, Visual Studio Code o Xcode:

![Selección de los métodos abreviados de teclado favoritos](media/ide-tour-2019-keyboard-shortcut.png)

Después de esta experiencia de instalación inicial, verá la _ventana de inicio_ siempre que abra Visual Studio 2019 para Mac, que muestra una lista de proyectos recientes y botones para abrir un proyecto existente o crear uno:

![Elección entre proyectos recientes o creación de uno nuevo](media/ide-tour-2019-start-projects.png)

## <a name="solutions-and-projects"></a>Soluciones y proyectos

En la imagen siguiente, se muestra Visual Studio para Mac con una aplicación cargada:

![Visual Studio para Mac con una aplicación cargada](media/ide-tour-image17.png)

En las secciones siguientes se proporciona una introducción a las áreas principales de Visual Studio para Mac.

## <a name="solution-window"></a>Ventana de la solución

La ventana de la solución organiza los proyectos de una solución:

![Proyectos organizados en la ventana de la solución](media/ide-tour-image18.png)

Aquí es donde se organizan los archivos por el código fuente, los recursos, la interfaz de usuario y las dependencias en proyectos específicos de plataforma.

Para más información sobre el uso de proyectos y soluciones en Visual Studio para Mac, consulte el artículo [Proyectos y soluciones](./projects-and-solutions.md).

## <a name="assembly-references"></a>Referencias de ensamblado

Las referencias de ensamblado de cada proyecto están disponibles en la carpeta Referencias:

![Carpeta Referencias en la ventana de la solución](media/ide-tour-image19.png)

Se pueden agregar otras referencias con el cuadro de diálogo **Editar referencias**. Para mostrarlo, haga doble clic en la carpeta Referencias o seleccione **Editar referencias** en las acciones del menú contextual:

![Cuadro de diálogo Editar referencias](media/ide-tour-image20.png)

Para más información sobre el uso de referencias en Visual Studio para Mac, consulte el artículo [Administrar referencias en un proyecto](./managing-references-in-a-project.md).

## <a name="dependencies--packages"></a>Dependencias o paquetes

Todas las dependencias externas usadas en la aplicación se almacenan en la carpeta Dependencias o Paquetes, según si el usuario se encuentra en un proyecto de .NET Core o Xamarin.iOS/Xamarin.Android. Normalmente se proporcionan en forma de NuGet.

NuGet es el administrador de paquetes más popular para el desarrollo de .NET. Con NuGet de Visual Studio, puede buscar paquetes fácilmente y agregarlos al proyecto o la aplicación.

Para agregar una dependencia a la aplicación, haga clic con el botón derecho en la carpeta Dependencias o Paquetes y seleccione **Agregar paquetes**:

![Adición de un paquete NuGet](media/ide-tour-image21.png)

En el artículo [Incluir un paquete NuGet en el proyecto](./nuget-walkthrough.md) puede encontrar información sobre el uso de un paquete NuGet en una aplicación.

## <a name="source-editor"></a>Editor de código fuente

Independientemente de si está escribiendo en C#, XAML o JavaScript, el editor de código comparte los mismos componentes principales con Visual Studio en Windows, con una interfaz de usuario totalmente nativa.

Esto aporta algunas de las siguientes características:

* Interfaz de usuario (basada en Cocoa) nativa de macOS (información en pantalla, superficie del editor, adornos de márgenes, representación de texto e IntelliSense)
* Filtrado de tipos de IntelliSense y "visualización de los elementos de importación"
* Compatibilidad con las entradas de texto nativo
* Compatibilidad con idiomas RTL/bidireccionales
* Roslyn 3
* Compatibilidad con múltiples símbolos de inserción
* Ajuste de línea
* Interfaz de usuario de IntelliSense actualizada
* Búsqueda y reemplazo mejorados
* Compatibilidad con fragmentos de código 
* Aplicación de formato a la selección
* Bombillas en línea

Para obtener más información sobre el uso del editor de código fuente en Visual Studio para Mac, consulte la documentación del [editor de código fuente](./source-editor.md).

Para mantener las pestañas visibles en todo momento, puede aprovechar la ventaja de anclarlas. De este modo, cada vez que inicie un proyecto, siempre aparecerá la pestaña que necesite. Para anclar una pestaña, mantenga el puntero sobre esta y haga clic en el icono _anclar_:

![Anclaje de una pestaña](media/ide-tour-tabpin.png)

## <a name="refactoring"></a>Refactorización

Visual Studio para Mac proporciona dos maneras útiles de refactorizar el código: acciones de contexto y análisis de código fuente. Puede obtener más información sobre ellas en el artículo [Refactorización](./refactoring.md).

## <a name="debugging"></a>Depuración

Visual Studio para Mac tiene depuradores compatibles con los proyectos de .NET Core, .NET Framework, Unity y Xamarin. Visual Studio para Mac usa el depurador de .NET Core y Mono Soft Debugger, que permiten al IDE depurar código administrado en todas las plataformas. Para más información sobre la depuración, visite el artículo [Depuración](./debugging.md).

El depurador contiene visualizadores completos para tipos especiales, como cadenas, colores y direcciones URL, además de tamaños, coordenadas y curvas de Bézier.

Para más información sobre las visualizaciones de datos del depurador, vea el artículo [Visualizaciones de datos](./data-visualizations.md).

## <a name="version-control"></a>Control de versiones

Visual Studio para Mac se integra con los sistemas de control de código fuente Git y Subversion. Los proyectos con control de código fuente se reconocen por la rama que aparece junto al nombre de la solución:

![Nombre de rama para indicar que se trata de un proyecto con control de código fuente](media/ide-tour-image22.png)

Los archivos con cambios sin confirmar tienen una anotación en sus iconos en la ventana de la solución, como se muestra en la imagen siguiente:

![Archivos sin confirmar en la ventana de la solución](media/ide-tour-image23.png)

Para más información sobre el uso del control de versiones en Visual Studio, consulte el artículo [Control de versiones](./version-control.md).

## <a name="next-steps"></a>Pasos siguientes

- [Instalación de Visual Studio para Mac](installation.md)
- [Revisión de las cargas de trabajo disponibles](workloads.md)

## <a name="related-video"></a>Vídeo relacionado

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Vea también

- [IDE de Visual Studio (en Windows)](/visualstudio/ide/visual-studio-ide)