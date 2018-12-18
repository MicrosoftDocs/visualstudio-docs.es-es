---
title: Novedades de la versión preliminar de Visual Studio 2019
titleSuffix: ''
description: Obtenga información sobre las nuevas características de la versión preliminar de Visual Studio 2019.
ms.date: 12/04/2018
ms.prod: visual-studio-dev16
ms.technology: vs-acquisition
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 06e3966703d95f897706eec8c46c2cd78fda859f
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159755"
---
# <a name="what39s-new-in-visual-studio-2019-preview"></a>Novedades de la versión preliminar de Visual Studio 2019

**Actualizado para la [versión preliminar 1 16.0](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)**

La versión preliminar de Visual Studio 2019 incluye muchas mejoras generales, así como nuevas características que optimizan la productividad de los desarrolladores y la colaboración en equipo. Tanto si usa Visual Studio por primera vez como si lo lleva usando años, podrá aprovechar sus características para todos los aspectos del ciclo de desarrollo, desde la creación de un proyecto y la administración del estado de código sencillas hasta flujos de trabajo colaborativos de código abierto y para equipos.

Aquí tiene un resumen detallado de todo lo que ofrece Visual Studio:

* **[Productividad personal y en equipo](#personal-and-team-productivity)**. Productividad para todos donde más importa.
* **[Compatibilidad con el desarrollo moderno](#modern-development-support)**. Compatibilidad con los proyectos actuales y las soluciones futuras.
* **[Innovación continua](#continuous-innovation)**. Escriba código de forma inteligente con la ayuda con tecnología en la nube.

> [!NOTE]
> Para obtener una lista completa de las nuevas características y funcionalidades de la versión preliminar de Visual Studio 2019, consulte las [notas de la versión](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017).

## <a name="personal-and-team-productivity"></a>Productividad personal y en equipo

Es un hecho que las mejoras de rendimiento son algo esencial de las nuevas versiones de Visual Studio, pero junto a ella vienen las mejoras de productividad. Así es como le ayudaremos en este aspecto.

### <a name="new-start-window"></a>Nueva ventana de inicio

Lo primero que verá al abrir Visual Studio 2019 es la nueva ventana de inicio.

   ![Nueva ventana de inicio de Visual Studio 2019](../ide/media/start-window.png)

En esta nueva ventana se mostrarán dos opciones para clonar o extraer código del repositorio, abrir un proyecto o una solución, abrir una carpeta local o crear un proyecto. Este simple cuadro de diálogo resulta muy útil tanto para los usuarios principiantes de Visual Studio como para los más avanzados, ya que permite acceder al código rápidamente.

### <a name="better-search"></a>Búsqueda mejorada

La nueva experiencia de búsqueda, anteriormente conocida como Inicio rápido, es más rápida y eficaz. Ahora los resultados de la búsqueda se mostrarán dinámicamente al escribir. Además, los resultados de la búsqueda incluyen métodos abreviados de teclado de comandos para que pueda memorizarlos fácilmente y usarlos en el futuro.

   ![Nueva característica de búsqueda de Visual Studio 2019](../ide/media/search-feature.png)

Tanto si busca comandos, opciones, documentación u otro material útil, la nueva característica de búsqueda le ayuda a encontrar lo que busca.

### <a name="one-click-code-cleanup"></a>Limpieza de código con un solo clic

Junto al nuevo indicador de estado del documento encontrará un nuevo comando de limpieza de código. Puede usar este nuevo comando para identificar y corregir advertencias y sugerencias con un solo clic.

   ![Nueva característica de limpieza de código de Visual Studio 2019](../ide/media/code-cleanup.png)

La limpieza dará formato al código y aplicará correcciones de código de acuerdo con las sugerencias de la [configuración actual](../ide/code-styles-and-quick-actions.md), los [archivos .editorconfig](../ide/create-portable-custom-editor-options.md) o los[analizadores Roslyn](../code-quality/roslyn-analyzers-overview.md).

### <a name="debugger-improvements"></a>Mejoras del depurador

#### <a name="search-within-a-watch-window-and-format-watch-values"></a>Búsqueda en una ventana Inspección y dar formato a valores de Inspección

A veces, entre varios valores, resulta difícil encontrar una cadena en la ventana Inspección. Es más, seguramente ya le habrá pasado. En la versión preliminar de Visual Studio 2019 hemos agregado la función de búsqueda en las ventanas Inspección, Variables locales y Automático para ayudarle a encontrar los objetos y valores que busca.

También puede dar formato a la visualización de un valor en las ventanas Inspección, Variables locales y Automático.  Haga doble clic en uno de los elementos de cualquiera de las ventanas y agregue una coma (",") para acceder a la lista desplegable de posibles especificadores de formato. Cada uno de ellos incluye una descripción del efecto previsto.

   ![Nueva ventana Inspección y uso del formato para los valores en Visual Studio 2019](../ide/media/search-watch-window.png)

### <a name="visual-studio-live-share"></a>Visual Studio Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) es un servicio para desarrolladores que permite compartir código base y su contexto con un compañero de equipo, de forma que obtengan una colaboración bidireccional instantánea directamente en Visual Studio. Con Live Share, un compañero de equipo puede leer, navegar, editar y depurar un proyecto que ha compartido con él de forma segura y sin problemas.

Además, con la versión preliminar de Visual Studio 2019, este servicio está instalado de forma predeterminada.

## <a name="modern-development-support"></a>Compatibilidad con el desarrollo moderno

### <a name="manage-pull-requests-prs-from-the-ide"></a>Administración de solicitudes de incorporación de cambios (PR) desde el IDE

Hemos incluido una nueva extensión que puede descargar para usarla con la versión preliminar de Visual Studio 2019. Con esta nueva extensión podrá revisar, ejecutar e incluso depurar solicitudes de incorporación de cambios del equipo sin salir del IDE [(entorno de desarrollo integrado)](../get-started/visual-studio-ide.md) de Visual Studio. Actualmente se admite el código de Azure Repos, pero estamos trabajando para incluir GitHub y mejorar la experiencia general.

Para empezar, puede descargar la extensión [Pull Requests for Visual Studio](https://aka.ms/pr4vs) de Visual Studio Marketplace.

### <a name="develop-with-net-core-3-preview-1"></a>Desarrollo con la versión preliminar 1 de .NET Core 3

La versión preliminar de Visual Studio 2019 admite la compilación de aplicaciones [.NET Core 3](http://aka.ms/netcore3preview1) para cualquier plataforma. Seguiremos ofreciendo soporte técnico y mejoras para el desarrollo multiplataforma de C++, así como para el desarrollo móvil de .NET para iOS, y Android con Xamarin.

   ![Desarrollo de aplicaciones con la versión preliminar 1 de .NET Core 3 en Visual Studio 2019](../ide/media/dot-net-core-three-dev.png)

## <a name="continuous-innovation"></a>Innovación continua

### <a name="per-monitor-aware-pma-rendering"></a>Representación con reconocimiento del monitor (PMA)

Si usa monitores configurados con diferentes factores de escala o se conecta de forma remota a una máquina con factores de escala distintos a los de su dispositivo principal, es posible que Visual Studio se muestre borroso o que se represente en una escala incorrecta.

Con la publicación de la versión preliminar 1 de Visual Studio 2019, hemos comenzado a hacer que Visual Studio sea una aplicación con reconocimiento del monitor (PMA). Estamos asentando la base que nos permitirá hacer que Visual Studio se represente correctamente independientemente de los factores de escala de monitor que use.

   ![Representación con reconocimiento del monitor (PMA) en Visual Studio 2019](../ide/media/per-monitor-aware-dpi-scaling.png)

### <a name="visual-studio-intellicode"></a>Visual Studio IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) es una extensión que mejora su desarrollo de software mediante inteligencia artificial (IA). IntelliCode se entrena en 2000 proyectos de código abierto de GitHub, cada uno con más de 100 estrellas, para generar sus recomendaciones.

Estas son algunas formas en las que Visual Studio IntelliCode le puede ayudar a aumentar su productividad:

* Ofrece finalizaciones de código en contexto.
* Guía a los desarrolladores para que cumplan con los patrones y estilos de su equipo.
* Encuentra problemas de código difíciles de detectar.
* Enfoca las revisiones de código, al llamar la atención sobre las áreas que realmente importan.

En la versión preliminar de la extensión IntelliCode para Visual Studio, inicialmente solo se admitía C#. Ahora se ha agregado compatibilidad con C++ y XAML en Visual Studio.

Si usa C#, también hemos agregado la posibilidad de entrenar un modelo personalizado en su propio código.

Para obtener más información sobre la extensión y para descargarla, vea la página [Visual Studio IntelliCode - Preview](https://go.microsoft.com/fwlink/?linkid=872707) en Microsoft DevLabs.

## <a name="give-us-feedback"></a>Envíenos sus comentarios.

¿Por qué enviar comentarios al equipo de Visual Studio? Porque tomamos los comentarios de los clientes muy en serio. Estos impulsan muchas de nuestras acciones.

* Si quiere hacer una sugerencia sobre cómo podemos mejorar Visual Studio, puede hacerlo mediante la herramienta [Proporcionar una sugerencia](../ide/talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features).

* Si experimenta un bloqueo u otro problema de rendimiento, puede compartir fácilmente los pasos de reproducción y los archivos auxiliares con nosotros mediante la herramienta [Notificar un problema](../ide/talk-to-us.md#i-want-to-report-a-problem-with-visual-studio).

## <a name="see-also"></a>Vea también

* [Notas de la versión de Visual Studio 2019](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)
* [Novedades de Visual Studio 2017](whats-new-in-visual-studio.md)
