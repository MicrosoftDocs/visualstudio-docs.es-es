---
title: Novedades de Visual Studio 2019
titleSuffix: ''
description: Obtenga más información sobre las nuevas características de Visual Studio 2019.
ms.date: 02/08/2019
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 4667fd19f59453e9efc856aefeaaf8d43aff302d
ms.sourcegitcommit: 61dc40d6c707f8c79779ec1091b296530d5a7b81
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987423"
---
# <a name="whats-new-in-visual-studio-2019-preview"></a>Novedades de la versión preliminar de Visual Studio 2019

**Actualizado para la [versión Preview 2](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)**

>[!div class="button"]
>[Descarga de la versión preliminar](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+preview)

La versión preliminar de Visual Studio 2019 incluye muchas mejoras generales, así como nuevas características que optimizan la productividad de los desarrolladores y la colaboración en equipo. Tanto si usa Visual Studio por primera vez como si lo lleva usando años, podrá aprovechar sus características para todos los aspectos del ciclo de desarrollo, desde la creación de un proyecto y la administración del estado de código sencillas hasta flujos de trabajo colaborativos de código abierto y para equipos.<br/><br/>

>[!VIDEO https://channel9.msdn.com/Events/Connect/Microsoft-Connect--2018/D190/player]

Aquí tiene un resumen detallado de todo lo que ofrece Visual Studio:

* **[Productividad personal y en equipo](#personal-and-team-productivity)**. Productividad para todos donde más importa.
* **[Compatibilidad con el desarrollo moderno](#modern-development-support)**. Compatibilidad con los proyectos actuales y las soluciones futuras.
* **[Innovación continua](#continuous-innovation)**. Escriba código de forma inteligente con la ayuda con tecnología en la nube.

> [!NOTE]
> Para obtener una lista completa de las nuevas características y funcionalidades de la versión preliminar de Visual Studio 2019, consulte las [notas de la versión](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017). Y para obtener un resumen de las novedades de nuestra segunda versión preliminar, vea la entrada de blog [Visual Studio 2019 Preview 2 is now available](https://blogs.msdn.microsoft.com/visualstudio/2019/01/24/visual-studio-2019-preview-2-is-now-available/) (Visual Studio 2019 Preview 2 ya disponible).

## <a name="personal-and-team-productivity"></a>Productividad personal y en equipo

Es un hecho que las mejoras de rendimiento son algo esencial de las nuevas versiones de Visual Studio, pero junto a ella vienen las mejoras de productividad. Así es como le ayudaremos en este aspecto.

### <a name="new-start-window"></a>Nueva ventana de inicio

Lo primero que verá al abrir Visual Studio 2019 es la nueva ventana de inicio.

   ![Nueva ventana de inicio de Visual Studio 2019](media/start-window.png)

En esta nueva ventana se mostrarán dos opciones para clonar o extraer código del repositorio, abrir un proyecto o una solución, abrir una carpeta local o crear un proyecto. Este simple cuadro de diálogo resulta muy útil tanto para los usuarios principiantes de Visual Studio como para los más avanzados, ya que permite acceder al código rápidamente.

Para más información, vea la entrada de blog [Get to code: How we designed the new Visual Studio start window](https://blogs.msdn.microsoft.com/visualstudio/2018/12/13/get-to-code-how-we-designed-the-new-visual-studio-start-window/) (Llegar al código: cómo hemos diseñado la nueva ventana de inicio de Visual Studio).

### <a name="better-search"></a>Búsqueda mejorada

La nueva experiencia de búsqueda, anteriormente conocida como Inicio rápido, es más rápida y eficaz. Ahora los resultados de la búsqueda se mostrarán dinámicamente al escribir. Además, los resultados de la búsqueda incluyen métodos abreviados de teclado de comandos para que pueda memorizarlos fácilmente y usarlos en el futuro.

   ![Nueva característica de búsqueda de Visual Studio 2019](media/search-feature.png)

Tanto si busca comandos, opciones, documentación u otro material útil, la nueva característica de búsqueda le ayuda a encontrar lo que busca.

### <a name="one-click-code-cleanup"></a>Limpieza de código con un solo clic

Junto al nuevo indicador de estado del documento encontrará un nuevo comando de limpieza de código. Puede usar este nuevo comando para identificar y corregir advertencias y sugerencias con un solo clic.

   ![Nueva característica de limpieza de código de Visual Studio 2019](media/code-cleanup.png)

La limpieza dará formato al código y aplicará correcciones de código de acuerdo con las sugerencias de la [configuración actual](code-styles-and-quick-actions.md), los [archivos .editorconfig](create-portable-custom-editor-options.md) o los[analizadores Roslyn](../code-quality/roslyn-analyzers-overview.md).

### <a name="debugger-improvements"></a>Mejoras del depurador

#### <a name="search-within-a-watch-window-and-format-watch-values"></a>Búsqueda en una ventana Inspección y dar formato a valores de Inspección

A veces, entre varios valores, resulta difícil encontrar una cadena en la ventana Inspección. Es más, seguramente ya le habrá pasado. En la versión preliminar de Visual Studio 2019 hemos agregado la función de búsqueda en las ventanas Inspección, Variables locales y Automático para ayudarle a encontrar los objetos y valores que busca.

También puede dar formato a la visualización de un valor en las ventanas Inspección, Variables locales y Automático.  Haga doble clic en uno de los elementos de cualquiera de las ventanas y agregue una coma (",") para acceder a la lista desplegable de posibles especificadores de formato. Cada uno de ellos incluye una descripción del efecto previsto.

   ![Nueva ventana Inspección y uso del formato para los valores en Visual Studio 2019](media/search-watch-window.png)

Para más información, vea la entrada de blog [Enhanced in Visual Studio 2019: Search for Objects and Properties in the Watch, Autos, and Locals Windows](https://blogs.msdn.microsoft.com/visualstudio/2019/01/28/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) (Mejoras en Visual Studio 2019: búsqueda de objetos y propiedades en las ventanas Inspección, Automático y Variables locales)

### <a name="visual-studio-live-share"></a>Visual Studio Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) es un servicio para desarrolladores que permite compartir código base y su contexto con un compañero de equipo, de forma que obtengan una colaboración bidireccional instantánea directamente en Visual Studio. Con Live Share, un compañero de equipo puede leer, navegar, editar y depurar un proyecto que ha compartido con él de forma segura y sin problemas.

Además, con la versión preliminar de Visual Studio 2019, este servicio está instalado de forma predeterminada.

   ![Un archivo GIF animado que muestra la característica de colaboración Live Share en Visual Studio 2019](media/live-share-collaboration.gif)

Para más información, vea la entrada de blog [Visual Studio Live Share for real-time code reviews and interactive education](https://blogs.msdn.microsoft.com/visualstudio/2018/12/06/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) (Visual Studio Live Share para revisiones de código en tiempo real y educación interactiva).

## <a name="modern-development-support"></a>Compatibilidad con el desarrollo moderno

### <a name="manage-pull-requests-prs-from-the-ide"></a>Administración de solicitudes de incorporación de cambios (PR) desde el IDE

Hemos incluido una nueva extensión que puede descargar para usarla con la versión preliminar de Visual Studio 2019. Con esta nueva extensión podrá revisar, ejecutar e incluso depurar solicitudes de incorporación de cambios del equipo sin salir del IDE [(entorno de desarrollo integrado)](../get-started/visual-studio-ide.md) de Visual Studio. Actualmente se admite el código de Azure Repos, pero estamos trabajando para incluir GitHub y mejorar la experiencia general.

Para empezar, puede descargar la extensión [Pull Requests for Visual Studio](https://aka.ms/pr4vs) de Visual Studio Marketplace.

### <a name="develop-with-net-core-3-preview"></a>Desarrollo con la versión preliminar de .NET Core 3

La versión preliminar de Visual Studio 2019 admite la compilación de aplicaciones [.NET Core 3](https://dotnet.microsoft.com/download/dotnet-core/3.0) para cualquier plataforma. Seguiremos ofreciendo soporte técnico y mejoras para el desarrollo multiplataforma de C++, así como para el desarrollo móvil de .NET para iOS, y Android con Xamarin.

   ![Desarrollo de aplicaciones con la versión preliminar de .NET Core 3 en Visual Studio 2019](media/dot-net-core-three-dev.png)

Para obtener más información, consulte las siguientes páginas:

* Notas de la versión de [.NET Core 3 versión preliminar 1](https://github.com/dotnet/core/blob/master/release-notes/3.0/preview/3.0.0-preview1.md) y [.NET Core 3 versión preliminar 2](https://github.com/dotnet/core/blob/master/release-notes/3.0/preview/3.0.0-preview2.md)
* Entradas de blob [Announcing .NET Core 3 Preview 1](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/) (Anuncio de .NET Core 3 versión preliminar 1) y [Announcing .NET Core 3 Preview 2](https://blogs.msdn.microsoft.com/dotnet/2019/01/29/announcing-net-core-3-preview-2/) (Anuncio de .NET Core 3 versión preliminar 2)

## <a name="continuous-innovation"></a>Innovación continua

### <a name="per-monitor-aware-pma-rendering"></a>Representación con reconocimiento del monitor (PMA)

Si usa monitores configurados con diferentes factores de escala o se conecta de forma remota a una máquina con factores de escala distintos a los de su dispositivo principal, es posible que Visual Studio se muestre borroso o que se represente en una escala incorrecta.

Con la publicación de Visual Studio 2019 Preview, se toman los primeros pasos para hacer que Visual Studio sea una aplicación con reconocimiento del monitor (PMA). Estamos asentando la base que nos permitirá hacer que Visual Studio se represente correctamente independientemente de los factores de escala de monitor que use.

   ![Representación con reconocimiento del monitor (PMA) en Visual Studio 2019](media/per-monitor-aware-dpi-scaling.png)

Para obtener más información, consulte la entrada de blog [Better multi-monitor experience with Visual Studio 2019](https://blogs.msdn.microsoft.com/visualstudio/2019/02/07/a-better-multi-monitor-experience-with-visual-studio-2019/) (Una mejor experiencia de varios monitores con Visual Studio 2019).

### <a name="visual-studio-intellicode"></a>Visual Studio IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) es una extensión que mejora su desarrollo de software mediante inteligencia artificial (IA). IntelliCode se entrena en 2000 proyectos de código abierto de GitHub, cada uno con más de 100 estrellas, para generar sus recomendaciones.

Estas son algunas formas en las que Visual Studio IntelliCode le puede ayudar a aumentar su productividad:

* Ofrece finalizaciones de código en contexto.
* Guía a los desarrolladores para que cumplan con los patrones y estilos de su equipo.
* Encuentra problemas de código difíciles de detectar.
* Enfoca las revisiones de código, al llamar la atención sobre las áreas que realmente importan.

 ![Un ejemplo de una sugerencia de IntelliSense](media/intellicode-intellisense-suggestion.png)

En la versión preliminar de la extensión IntelliCode para Visual Studio, inicialmente solo se admitía C#. Ahora se ha agregado compatibilidad con C++ y XAML en Visual Studio.

Si usa C#, también hemos agregado la posibilidad de entrenar un modelo personalizado en su propio código.

Para más información sobre las actualizaciones más recientes, vea la entrada de blog [Visual Studio IntelliCode supports more languages and learns from your code](https://blogs.msdn.microsoft.com/visualstudio/2018/12/05/visual-studio-intellicode-supports-more-languages-and-learns-from-your-code/) (Visual Studio IntelliCode admite más lenguajes y aprende del código). Asimismo, para más información sobre la extensión y cómo descargarla, vea la página [Visual Studio IntelliCode - Preview](https://go.microsoft.com/fwlink/?linkid=872707) en Microsoft DevLabs.

## <a name="give-us-feedback"></a>Envíenos sus comentarios.

¿Por qué enviar comentarios al equipo de Visual Studio? Porque tomamos los comentarios de los clientes muy en serio. Estos impulsan muchas de nuestras acciones.

* Si quiere hacer una sugerencia sobre cómo podemos mejorar Visual Studio, puede hacerlo mediante la herramienta [Proporcionar una sugerencia](talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features).

* Si experimenta un bloqueo u otro problema de rendimiento, puede compartir fácilmente los pasos de reproducción y los archivos auxiliares con nosotros mediante la herramienta [Notificar un problema](talk-to-us.md#i-want-to-report-a-problem-with-visual-studio).

## <a name="see-also"></a>Vea también

* [Notas de la versión de Visual Studio 2019](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)
* [Conferencia sobre Microsoft Connect(); 2018](https://www.microsoft.com/connectevent)
* [Novedades de Visual Studio 2017](whats-new-visual-studio-2017.md)
