---
title: Novedades de Visual Studio 2019
titleSuffix: ''
description: Obtenga más información sobre las nuevas características de Visual Studio 2019.
ms.date: 04/04/2019
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 25a7f5f0e53518e9beb4b509ab27ae4de0f28fa7
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018160"
---
# <a name="whats-new-in-visual-studio-2019"></a>Novedades de Visual Studio 2019

**Actualizado para la [versión 16.0](/visualstudio/releases/2019/release-notes/)**

>[!div class="button"]
>[Descargar Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

Con Visual Studio 2019, recibirá las mejores herramientas y servicios para cualquier desarrollador, aplicación y plataforma. Independientemente de si usa Visual Studio por primera vez o si ya lo ha usado durante años, esta nueva versión le gustará mucho.

Este es un resumen de alto nivel de todas las novedades:

* **[Desarrollo](#develop)**: concéntrese y mantenga su productividad con mejor rendimiento, la limpieza instantánea del código y mejores resultados de la búsqueda.
* **[Colaboración](#collaborate)**: disfrute de la colaboración natural mediante un flujo de trabajo que da prioridad a la nube, la edición y depuración en tiempo real y las revisiones de código directamente en Visual Studio.
* **[Depuración](#debug)**: resalte valores específicos y navegue a ellos, optimice el uso de la memoria y cree capturas de pantalla automáticas de la ejecución de la aplicación.

Si quiere ver una lista completa de todas las novedades de esta versión, consulte las [notas de la versión](/visualstudio/releases/2019/release-notes/). 

## <a name="develop"></a>Desarrollar

Ahorre tiempo con las características nuevas.
<br><br>
> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Búsqueda mejorada

La nueva experiencia de búsqueda, anteriormente conocida como Inicio rápido, es más rápida y eficaz. Ahora los resultados de la búsqueda se mostrarán dinámicamente al escribir. Además, los resultados de la búsqueda a menudo pueden incluir métodos abreviados de teclado de comandos para que pueda memorizarlos fácilmente y usarlos en el futuro.

   ![Animación de la experiencia de búsqueda nueva en Visual Studio 2019](media/vs-2019/new-search-feature.gif)

La nueva lógica de búsqueda aproximada encontrará todo lo que necesite, independientemente de los errores tipográficos que pueda haber. Por lo tanto, independientemente de si busca comandos, opciones, documentación u otro material útil, la nueva característica de búsqueda le ayuda a encontrar lo que busca.

### <a name="refactorings"></a>Refactorizaciones

Las nuevas refactorizaciones de C# facilitan la organización del código. Para invocar las refactorizaciones, basta con presionar **Ctrl+.** y seleccionar la acción que quiere usar. 

   ![Animación de la experiencia de refactorización en Visual Studio 2019](media/vs-2019/refactorings.gif)

Agregamos muchas refactorizaciones nuevas, incluida una que permite ajustar los parámetros de método.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) es una extensión que mejora su desarrollo de software mediante inteligencia artificial (IA). IntelliCode se entrena en 2000 proyectos de código abierto de GitHub, cada uno con más de 100 estrellas, para generar sus recomendaciones.

 ![Animación de IntelliCode en Visual Studio 2019](media/vs-2019/IntelliCode.gif)

Estas son algunas formas en las que Visual Studio IntelliCode le puede ayudar a aumentar su productividad:

* Ofrece finalizaciones de código en contexto.
* Guía a los desarrolladores para que cumplan con los patrones y estilos de su equipo.
* Encuentra problemas de código difíciles de detectar.
* Enfoca las revisiones de código, al llamar la atención sobre las áreas que realmente importan.

En la versión preliminar de la extensión IntelliCode para Visual Studio, inicialmente solo se admitía C#. Ahora se ha agregado compatibilidad con C++ y XAML en Visual Studio.

Si usa C#, también hemos agregado la posibilidad de entrenar un modelo personalizado en su propio código.

Para más información sobre IntelliCode, consulte la entrada de blog [Code more, scroll less with Visual Studio IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) (Codifique más y desplácese menos con Visual Studio IntelliCode). 

### <a name="code-cleanup"></a>Limpieza de código

Junto al nuevo indicador de estado del documento encontrará un nuevo comando de limpieza de código. Puede usar este nuevo comando para identificar y corregir advertencias y sugerencias con un solo clic.

La limpieza dará formato al código y aplicará correcciones de código de acuerdo con las sugerencias de la [configuración actual](code-styles-and-quick-actions.md), los [archivos .editorconfig](create-portable-custom-editor-options.md) o los[analizadores Roslyn](../code-quality/roslyn-analyzers-overview.md).

   ![Captura de pantalla del nuevo control de limpieza de código en Visual Studio 2019](media/vs-2019/code-cleanup-profile.png)

También puede guardar las colecciones de reparadores como un perfil. Por ejemplo, si tiene un conjunto pequeño de reparadores dirigidas que aplica con frecuencia mientras codifica y después tiene otro conjunto integral de reparadores para aplicar antes de una revisión del código, puede configurar perfiles para abordar estas distintas tareas.

   ![Captura de pantalla del nuevo control de limpieza de código en Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png)

## <a name="collaborate"></a>Colaborar

Trabaje en equipo para solucionar problemas.
<br><br>
> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="cloud-first-workflow"></a>Flujo de trabajo que da prioridad a la nube

Algo que verá al abrir Visual Studio 2019 es la nueva ventana de inicio.

   ![Captura de pantalla de la nueva ventana de inicio de Visual Studio 2019](media/vs-2019/start-window-dark.png)

La ventana de inicio presenta varias opciones para ponerse a codificar rápidamente. En primer lugar, pusimos la opción para clonar o extraer el código de un repositorio.  

   ![Animación de la experiencia con "prioridad de Git" en Visual Studio 2019](media/vs-2019/git-first.gif)

La ventana de inicio también incluye opciones para abrir un proyecto o una solución, abrir una carpeta local o crear un proyecto.

Para más información, vea la entrada de blog [Get to code: How we designed the new Visual Studio start window](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) (Llegar al código: cómo hemos diseñado la nueva ventana de inicio de Visual Studio).

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) es un servicio para desarrolladores que permite compartir código base y su contexto con un compañero de equipo, de forma que se establezca una colaboración bidireccional instantánea directamente en Visual Studio. Con Live Share, un compañero de equipo puede leer, navegar, editar y depurar un proyecto que ha compartido con él de forma segura y sin problemas.

Además, con Visual Studio 2019, este servicio está instalado de forma predeterminada.

![Animación que muestra la característica de colaboración Live Share en Visual Studio 2019](media/vs-2019/live-share.gif)

Para más información, consulte las entradas de blog [Visual Studio Live Share for real-time code reviews and interactive education](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) (Visual Studio Live Share para revisiones de código en tiempo real y educación interactiva) y [Live Share now included with Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) (Live Share ahora está incluido en Visual Studio 2019).

### <a name="integrated-code-reviews"></a>Revisiones de código integrado

Se ha incluido una nueva extensión que puede descargar para su uso con Visual Studio 2019. Con esta extensión nueva podrá revisar, ejecutar e incluso depurar solicitudes de incorporación de cambios del equipo sin salir de Visual Studio. Se admite el código tanto en repositorios de GitHub como de Azure DevOps.

   ![Captura de pantalla de la nueva ventana de inicio de Visual Studio 2019](media/vs-2019/pr-experience.png)

Para empezar, puede descargar la extensión [Pull Requests for Visual Studio](https://aka.ms/pr4vs) de Visual Studio Marketplace.

## <a name="debug"></a>Depuración

Céntrese con un destino preciso.
<br><br>
> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Aumento del rendimiento

Tomamos los puntos de interrupción de datos que antes eran exclusivos de C++ y los adaptamos a aplicaciones .NET Core.

   ![Animación que muestra los puntos de interrupción de datos de depuración en Visual Studio 2019](media/vs-2019/debug-data-breakpoints.gif)

Por lo tanto, ya sea que esté codificando en C++ o en .NET Core, los puntos de interrupción de datos pueden ser una buena alternativa a poner simplemente puntos de interrupción normales. Los puntos de interrupción de datos también son ideales para escenarios como buscar dónde se modifica un objeto global o se agrega o quita de una lista. 

Y si es desarrollador de C++ que desarrolla aplicaciones de gran tamaño, Visual Studio 2019 ha dejado los símbolos fuera del proceso, lo que permite depurar esas aplicaciones sin que se presenten problemas relacionados con la memoria.

### <a name="search-while-debugging"></a>Búsqueda durante la depuración

A veces, entre varios valores, resulta difícil encontrar una cadena en la ventana Inspección. Es más, seguramente ya le habrá pasado. En Visual Studio 2019, se ha agregado la búsqueda en las ventanas Inspección, Variables locales y Automático para ayudarle a encontrar los objetos y valores que busca.

   ![Animación que muestra la ventana de búsqueda de depuración en Visual Studio 2019](media/vs-2019/debug-window-search.gif)

También puede dar formato a la visualización de un valor en las ventanas Inspección, Variables locales y Automático.  Haga doble clic en uno de los elementos de cualquiera de las ventanas y agregue una coma (",") para acceder a la lista desplegable de posibles especificadores de formato. Cada uno de ellos incluye una descripción del efecto previsto.

   ![Nueva ventana Inspección y uso del formato para los valores en Visual Studio 2019](media/search-watch-window.png)

Para más información, vea la entrada de blog [Enhanced in Visual Studio 2019: Search for Objects and Properties in the Watch, Autos, and Locals Windows](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) (Mejoras en Visual Studio 2019: búsqueda de objetos y propiedades en las ventanas Inspección, Automático y Variables locales)

### <a name="snapshot-debugger"></a>Depurador de instantáneas

Obtenga una instantánea de la ejecución de la aplicación en la nube para ver exactamente qué es lo que sucede. (Esta característica solo está disponible en Visual Studio Enterprise).

   ![Animación que muestra Snapshot Debugger en Visual Studio 2019 Enterprise](media/vs-2019/snapshot-debugger.gif)

Agregamos compatibilidad con las aplicaciones de ASP.NET (escritorio y core) que se ejecutan en máquinas virtuales (VM) de Azure. Además, agregamos compatibilidad con las aplicaciones que se ejecutan en Azure Kubernetes Service. El Depurador de instantáneas puede permitirle disminuir considerablemente el tiempo que tarda en resolver los problemas que se producen en los entornos de producción.

Para más información, vea la página [Depuración de aplicaciones de Azure de ASP.NET en vivo con Snapshot Debugger](../debugger/debug-live-azure-applications.md) y la entrada de blog [Introducing Time Travel Debugging for Visual Studio Enterprise 2019](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) (Presentación de la depuración de viaje en el tiempo para Visual Studio Enterprise 2019).

## <a name="give-us-feedback"></a>Envíenos sus comentarios.

¿Por qué enviar comentarios al equipo de Visual Studio? Porque tomamos los comentarios de los clientes muy en serio. Estos impulsan muchas de nuestras acciones.

* Si quiere hacer una sugerencia sobre cómo podemos mejorar Visual Studio, puede hacerlo mediante la herramienta [Proporcionar una sugerencia](talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features).

* Si experimenta un bloqueo u otro problema de rendimiento, puede compartir fácilmente los pasos de reproducción y los archivos auxiliares con nosotros mediante la herramienta [Notificar un problema](talk-to-us.md#i-want-to-report-a-problem-with-visual-studio).

## <a name="see-also"></a>Vea también

* [Anuncio de Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/visual-studio-2019-code-faster-work-smarter-create-the-future/)
* [Notas de la versión de Visual Studio 2019](/visualstudio/releases/2019/release-notes/)
* [Novedades del SDK de Visual Studio 2019](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Visual Studio 2019 para Mac ya está disponible](https://devblogs.microsoft.com/visualstudio/visual-studio-2019-for-mac-is-now-available/)
* [Conferencia sobre Microsoft Connect(); 2018](https://www.microsoft.com/connectevent)
