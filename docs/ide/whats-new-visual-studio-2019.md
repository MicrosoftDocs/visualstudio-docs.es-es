---
title: Novedades de Visual Studio 2019
titleSuffix: ''
description: Obtenga más información sobre las nuevas características de Visual Studio 2019.
ms.date: 06/17/2021
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: d34c3a3b4d808b1f4e24051763f1c0876a175a3a
ms.sourcegitcommit: a9526ab1556c47570286c7a7d3314af67fd1dcf0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/18/2021
ms.locfileid: "112365474"
---
# <a name="whats-new-in-visual-studio-2019"></a>Novedades de Visual Studio 2019

**Actualizado para la versión 16.10.** Vea las [notas de la versión completas](/visualstudio/releases/2019/release-notes/) | Visualización de la [hoja de ruta del producto](/visualstudio/productinfo/vs-roadmap)

>[!div class="button"]
>[Descargar Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

Con Visual Studio 2019, recibirá las mejores herramientas y servicios para cualquier desarrollador, aplicación y plataforma. Independientemente de si usa Visual Studio por primera vez o si ya lo ha usado durante años, nuestra última versión le gustará mucho.

Este es un completo resumen general de todas las novedades:

* **[Desarrollo](#develop)** : concéntrese y mantenga su productividad con mejor rendimiento, la limpieza instantánea del código y mejores resultados de la búsqueda.
* **[Colaboración](#collaborate)** : disfrute de una colaboración natural mediante un flujo de trabajo con "prioridad de Git", la edición y depuración en tiempo real y las revisiones de código directamente en Visual Studio.
* **[Depuración](#debug)** : resalte valores específicos y navegue a ellos, optimice el uso de la memoria y cree capturas de pantalla automáticas de la ejecución de la aplicación.

Si quiere ver una lista completa de todas las novedades de esta versión, consulte las [notas de la versión](/visualstudio/releases/2019/release-notes/).

## <a name="develop"></a>Desarrollar

Vea el vídeo siguiente para obtener más información sobre cómo puede ahorrar tiempo con las nuevas características. <br><br>*Duración del vídeo: 3 minutos*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Búsqueda mejorada

La nueva experiencia de búsqueda, anteriormente conocida como Inicio rápido, es más rápida y eficaz. Ahora los resultados de la búsqueda se mostrarán dinámicamente al escribir. Además, los resultados de la búsqueda a menudo pueden incluir métodos abreviados de teclado de comandos para que pueda memorizarlos y usarlos en el futuro.

   ![Animación de la experiencia de búsqueda nueva en Visual Studio 2019](media/vs-2019/new-search-feature.gif "Nueva experiencia de búsqueda de Visual Studio 2019.")

La nueva lógica de búsqueda aproximada encontrará todo lo que necesite, independientemente de los errores tipográficos que pueda haber. Por lo tanto, independientemente de si busca comandos, opciones, documentación u otro material útil, la nueva característica de búsqueda le ayuda a encontrar lo que busca.

Para más información, consulte [Uso de la búsqueda de Visual Studio](visual-studio-search.md).

#### <a name="intelligent-search-service"></a>Servicio de búsqueda inteligente

**Novedades en la versión 16.9**: mediante el uso de tecnología basada en la nube, inteligencia artificial y aprendizaje automático, hemos mejorado los resultados de la búsqueda. Ahora, no solo la búsqueda en Visual Studio genera resultados más relevantes, también puede ayudarle a descubrir las características del producto más fácilmente.

Para más información, consulte la entrada de blog sobre el [servicio de búsqueda inteligente de Visual Studio](https://devblogs.microsoft.com/visualstudio/intelligent-visual-studio-search-service/).

### <a name="refactorings"></a>Refactorizaciones

Hay una gran cantidad de refactorizaciones nuevas y muy útiles en C# que facilitan la organización de su código. Estas se muestran como sugerencias en la bombilla e incluyen acciones tales como mover miembros a la interfaz o a la clase base, ajustar los espacios de nombres para que coincidan con la estructura de carpetas, convertir los bucles foreach en consultas de Linq y muchas más.

   ![Animación de la experiencia de refactorización en Visual Studio 2019](media/vs-2019/refactorings.gif "Experiencia de refactorizaciones de Visual Studio 2019.")

Para invocar las refactorizaciones, basta con presionar **Ctrl+.** y seleccionar la acción que quiere usar.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) mejora los esfuerzos de desarrollo de software mediante inteligencia artificial (IA). IntelliCode se entrena en 2000 proyectos de código abierto de GitHub, cada uno con más de 100 estrellas, para generar sus recomendaciones.

![Animación de IntelliCode en Visual Studio 2019](media/vs-2019/IntelliCode.gif "IntelliCode en Visual Studio 2019.")

Estas son algunas formas en las que Visual Studio IntelliCode le puede ayudar a aumentar su productividad:

* Ofrece finalizaciones de código en contexto.
* Guía a los desarrolladores para que cumplan con los patrones y estilos de su equipo.
* Encuentra problemas de código difíciles de detectar.
* Enfoca las revisiones de código, al llamar la atención sobre las áreas que realmente importan.

En la versión preliminar de IntelliCode como extensión para Visual Studio solo se admitía C#. Ahora, como **novedad de 16.1**, se ha agregado compatibilidad con C# y XAML al paquete. (La compatibilidad con C++ y TypeScript/JavaScript aún está en versión preliminar).

Si usa C#, también hemos agregado la posibilidad de entrenar un modelo personalizado en su propio código.

Para obtener más información sobre IntelliCode, vea las entradas de blog [Announcing the general availability of IntelliCode plus a sneak peek](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) (Anuncio de la disponibilidad general de IntelliCode más un vistazo) y [Code more, scroll less with Visual Studio IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) (Codifique más y desplácese menos con Visual Studio IntelliCode).

### <a name="code-cleanup"></a>Limpieza de código

Junto al nuevo indicador de estado del documento encontrará un nuevo comando de limpieza de código. Puede usar este comando nuevo para identificar y corregir advertencias y sugerencias con una sola acción (o clic de un botón).

La limpieza dará formato al código y aplicará todas las correcciones de código de acuerdo con las sugerencias de la [configuración actual](code-styles-and-code-cleanup.md) y los [archivos .editorconfig](create-portable-custom-editor-options.md).

   ![Captura de pantalla del nuevo control de limpieza de código en Visual Studio 2019](media/vs-2019/code-cleanup-profile.png "Nuevo control de limpieza de código de Visual Studio 2019.")

También puede guardar las colecciones de reparadores como un perfil. Por ejemplo, si tiene un conjunto pequeño de reparadores dirigidas que aplica con frecuencia mientras codifica y después tiene otro conjunto integral de reparadores para aplicar antes de una revisión del código, puede configurar perfiles para abordar estas distintas tareas.

   ![Captura de pantalla de la configuración del control de limpieza de código en Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png "Control de limpieza de código de configuración de Visual Studio 2019.")

### <a name="per-monitor-aware-pma-rendering"></a>Representación con reconocimiento del monitor (PMA)

Si usa monitores configurados con diferentes factores de escala o se conecta de forma remota a una máquina con factores de escala distintos a los de su dispositivo principal, es posible que Visual Studio se muestre borroso o que se represente en una escala incorrecta.

Con el lanzamiento de Visual Studio 2019, se está convirtiendo a Visual Studio en una aplicación con reconocimiento del monitor (PMA). Ahora, Visual Studio representa correctamente independientemente de los factores de escala de visualización que se usen.

   ![Representación con reconocimiento del monitor (PMA) en Visual Studio 2019](media/vs-2019/pma-dpi-scaling.png "Representación con reconocimiento del monitor (PMA) en Visual Studio 2019.")

Para obtener más información, consulte la entrada de blog [Better multi-monitor experience with Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) (Una mejor experiencia de varios monitores con Visual Studio 2019).

### <a name="test-explorer"></a>Explorador de pruebas

**Novedades de la versión 16.2** Se ha actualizado el Explorador de pruebas para mejorar el control de conjuntos de pruebas de gran tamaño y ofrecer un filtrado más sencillo, comandos más reconocibles, vistas de listas de reproducción por pestañas y columnas personalizables que permiten ajustar de forma precisa qué información de prueba se muestra.

   ![Captura de pantalla que muestra las mejoras de la interfaz de usuario en el Explorador de pruebas](media/vs-2019/test-explorer-ui.png "Mejoras en la interfaz de usuario del Explorador de pruebas.")

### <a name="net-core"></a>.NET Core

**Novedades en 16.3**: hemos incluido compatibilidad con .NET Core 3.0, de código abierto, multiplataforma y totalmente compatible con Microsoft.

Para obtener más información, consulte la entrada de blog [Anuncio de .NET Core 3.0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).

## <a name="collaborate"></a>Colaborar

Vea el vídeo siguiente para obtener más información sobre cómo puede recurrir al equipo para solucionar problemas. <br><br>*Duración del vídeo: 4:22 minutos*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Flujo de trabajo de prioridad de Git

Algo que verá al abrir Visual Studio 2019 es la nueva ventana de inicio.

   ![Captura de pantalla de la nueva ventana de inicio de Visual Studio 2019](media/vs-2019/start-window-dark.png "Nueva ventana de inicio de Visual Studio 2019.")

La ventana de inicio presenta varias opciones para ponerse a codificar rápidamente. En primer lugar, pusimos la opción para clonar o extraer el código de un repositorio.

   ![Animación de la experiencia con "prioridad de Git" en Visual Studio 2019](media/vs-2019/git-first.gif "Primera experiencia con Git en Visual Studio 2019.")

La ventana de inicio también incluye opciones para abrir un proyecto o una solución, abrir una carpeta local o crear un proyecto.

Para más información, vea la entrada de blog [Get to code: How we designed the new Visual Studio start window](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) (Llegar al código: cómo hemos diseñado la nueva ventana de inicio de Visual Studio).

### <a name="git-productivity"></a>Productividad de Git

**Novedades en 16.8**: Ahora Git es la experiencia de control de versiones predeterminada en Visual Studio 2019. Hemos creado el conjunto de características y lo hemos iterado según los comentarios recibidos durante las dos últimas versiones. Ahora, la nueva experiencia está activada de forma predeterminada para todos los usuarios. En el nuevo menú de Git puede clonar, crear o abrir repositorios. Use las ventanas de herramientas de Git integradas para confirmar y enviar cambios en el código, administrar ramas, conocer las últimas novedades relativas a los repositorios remotos y resolver conflictos de fusión mediante combinación.

Para más información, consulte la página [Experiencia de Git en Visual Studio](../version-control/git-with-visual-studio.md).

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) es un servicio para desarrolladores que permite compartir código base y su contexto con un compañero de equipo, de forma que se establezca una colaboración bidireccional instantánea directamente en Visual Studio. Con Live Share, un compañero de equipo puede leer, navegar, editar y depurar un proyecto que ha compartido con él de forma segura y sin problemas.

Además, con Visual Studio 2019, este servicio está instalado de forma predeterminada.

![Animación que muestra la característica de colaboración Live Share en Visual Studio 2019](media/vs-2019/live-share.gif "Característica de colaboración de Live Share de Visual Studio 2019.")

Para más información, consulte las entradas de blog [Visual Studio Live Share for real-time code reviews and interactive education](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) (Visual Studio Live Share para revisiones de código en tiempo real y educación interactiva) y [Live Share now included with Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) (Live Share ahora está incluido en Visual Studio 2019).

### <a name="integrated-code-reviews"></a>Revisiones de código integrado

Se ha incluido una nueva extensión que puede descargar para su uso con Visual Studio 2019. Con esta extensión nueva podrá revisar, ejecutar e incluso depurar solicitudes de incorporación de cambios del equipo sin salir de Visual Studio. Se admite el código tanto en repositorios de GitHub como de Azure DevOps.

   ![Captura de pantalla de la nueva extensión Solicitudes de incorporación de cambios de Visual Studio 2019](media/vs-2019/pr-experience.png "Nueva extensión Solicitud de incorporación de cambios de Visual Studio 2019.")

Para obtener más información, vea la entrada de blog [Code reviews using the Visual Studio Pull Requests extension](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) (Revisiones de código mediante la extensión Solicitudes de incorporación de cambios de Visual Studio).

## <a name="debug"></a>Depuración

Vea el vídeo siguiente para obtener más información sobre cómo centrarse en un destino concreto al depurar. <br><br>*Duración del vídeo: 3:54 minutos*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Aumento del rendimiento

Tomamos los puntos de interrupción de datos que antes eran exclusivos de C++ y los adaptamos a aplicaciones .NET Core.

   ![Animación que muestra los puntos de interrupción de datos de depuración en Visual Studio 2019](media/vs-2019/debug-data-breakpoints.gif "Puntos de interrupción de datos de depuración de Visual Studio 2019.")

Por lo tanto, ya sea que esté codificando en C++ o en .NET Core, los puntos de interrupción de datos pueden ser una buena alternativa a poner simplemente puntos de interrupción normales. Los puntos de interrupción de datos también son ideales para escenarios como buscar dónde se modifica un objeto global o se agrega o quita de una lista.

Y si es desarrollador de C++ que desarrolla aplicaciones de gran tamaño, Visual Studio 2019 ha dejado los símbolos fuera del proceso, lo que permite depurar esas aplicaciones sin que se presenten problemas relacionados con la memoria.

### <a name="search-while-debugging"></a>Búsqueda durante la depuración

A veces, entre varios valores, resulta difícil encontrar una cadena en la ventana Inspección. Es más, seguramente ya le habrá pasado. En Visual Studio 2019, se ha agregado la búsqueda en las ventanas Inspección, Variables locales y Automático para ayudarle a encontrar los objetos y valores que busca.

   ![Animación que muestra la ventana de búsqueda de depuración en Visual Studio 2019](media/vs-2019/debug-window-search.gif "Ventana de búsqueda de depuración de Visual Studio 2019.")

También puede dar formato a la visualización de un valor en las ventanas Inspección, Variables locales y Automático. Haga doble clic para seleccionar uno de los elementos de cualquiera de las ventanas y agregue una coma (",") para acceder a la lista desplegable de posibles especificadores de formato. Cada uno de ellos incluye una descripción del efecto previsto.

   ![Nueva ventana Inspección y uso del formato para los valores en Visual Studio 2019](media/search-watch-window.png "Nueva característica de ventana de inspección y valores de formato de Visual Studio 2019.")

Para más información, vea la entrada de blog [Enhanced in Visual Studio 2019: Search for Objects and Properties in the Watch, Autos, and Locals Windows](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) (Mejoras en Visual Studio 2019: búsqueda de objetos y propiedades en las ventanas Inspección, Automático y Variables locales)

### <a name="snapshot-debugger"></a>Depurador de instantáneas

Obtenga una instantánea de la ejecución de la aplicación en la nube para ver exactamente qué es lo que sucede. (Esta característica solo está disponible en Visual Studio Enterprise).

   ![Animación que muestra Snapshot Debugger en Visual Studio 2019 Enterprise](media/vs-2019/snapshot-debugger.gif "Snapshot Debugger de Visual Studio 2019 Enterprise.")

Agregamos compatibilidad con las aplicaciones de ASP.NET (escritorio y core) que se ejecutan en máquinas virtuales (VM) de Azure. Además, agregamos compatibilidad con las aplicaciones que se ejecutan en Azure Kubernetes Service. El Depurador de instantáneas puede permitirle disminuir considerablemente el tiempo que tarda en resolver los problemas que se producen en los entornos de producción.

Para más información, vea la página [Depuración de aplicaciones de Azure de ASP.NET en vivo con Snapshot Debugger](../debugger/debug-live-azure-applications.md) y la entrada de blog [Introducing Time Travel Debugging for Visual Studio Enterprise 2019](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) (Presentación de la depuración de viaje en el tiempo para Visual Studio Enterprise 2019).

### <a name="microsoft-edge-insider-support"></a>Soporte técnico de Microsoft Edge Insider

**Novedades de la versión 16.2**: Puede establecer un punto de interrupción en una aplicación de JavaScript e iniciar una sesión de depuración mediante el explorador [Microsoft Edge Insider](https://www.microsoftedgeinsider.com/). Al hacerlo, Visual Studio abre una nueva ventana del explorador con la depuración habilitada, que puede usar para recorrer el código JavaScript de la aplicación en Visual Studio.

   ![Captura de pantalla que muestra la representación de código JavaScript en un explorador](media/vs-2019/edge-chromium-breakpoint.png "Representación de código JavaScript en un explorador.")

### <a name="pinnable-properties-tool"></a>Herramienta para anclar propiedades

**Novedades en 16.4**: Ahora, es más fácil identificar objetos por sus propiedades durante la depuración con la nueva herramienta para anclar propiedades. Simplemente mantenga el cursor sobre la propiedad que quiere mostrar en la ventana del depurador de las ventanas Inspección, Automático y Variables locales, seleccione el icono de anclaje y verá inmediatamente la información que busca en la parte superior de la ventana.

   ![Animación que muestra cómo anclar propiedades en el depurador de Visual Studio mediante la herramienta para anclar propiedades](media/vs-2019/debugger-pinnable-properties.gif "Ancle propiedades en el depurador de Visual Studio mediante la herramienta para anclar propiedades.")

Para más información, consulte la entrada de blob [Propiedades que se pueden anclar: Depuración y visualización los objetos administrados a SU manera](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/).

## <a name="whats-next"></a>Pasos adicionales

Visual Studio se actualiza frecuentemente con características nuevas que pueden mejorar todavía más la experiencia de desarrollo. Para obtener más información sobre las últimas innovaciones, vea el [blog de Visual Studio](https://devblogs.microsoft.com/visualstudio/). Para consultar un registro de las novedades publicadas en versión preliminar hasta la fecha, vea las [Notas de la versión preliminar](/visualstudio/releases/2019/release-notes-preview/). Asimismo, para obtener una lista de lo que estamos planeando publicar a continuación, consulte la [Guía básica de Visual Studio](/visualstudio/productinfo/vs-roadmap).

Mientras tanto, esto es lo que hay actualmente en funcionamiento:

- **Experiencia mejorada de Git en Visual Studio 2019 (versión preliminar)**

   Aunque la herramienta de control de versiones de Git es la experiencia predeterminada en la versión [16.8](/visualstudio/releases/2019/release-notes-history/) de Visual Studio 2019 y posteriores, se siguen agregando características para mejorar la experiencia en la versión más reciente de Visual Studio 2019 Preview, [versión 16.11.](/visualstudio/releases/2019/release-notes-preview/)

   Para obtener más información, vea la página [Control de versiones en Visual Studio](/visualstudio/version-control/).

- **La primera versión pública de Visual Studio 2022 (Preview) ya está disponible**

    La versión preliminar pública de la próxima versión principal, [Visual Studio 2022](/visualstudio/releases/2022/release-notes-preview/), ya está disponible. La nueva versión es más rápida, accesible y ligera. Y, por primera vez en la historia, Visual Studio es de 64 bits. Para obtener un vínculo de descarga y más información, vea **[Visual Studio 2022 Preview 1 ya disponible.](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-1-now-available/)** .

## <a name="give-us-feedback"></a>Envíenos sus comentarios.

¿Por qué enviar comentarios al equipo de Visual Studio? Porque tomamos los comentarios de los clientes muy en serio. Estos impulsan muchas de nuestras acciones.

* Si quiere hacer una sugerencia sobre cómo se puede mejorar Visual Studio, puede hacerlo mediante la herramienta [Sugerir una característica](suggest-a-feature.md).

* Si experimenta un problema por el cual Visual Studio deja de responder o se bloquea, u otro problema de rendimiento, puede compartir fácilmente los pasos de reproducción y los archivos auxiliares con nosotros por medio de la herramienta [Notificar un problema](how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Vea también

* [Novedades de los documentos de Visual Studio](whats-new-visual-studio-docs.md)
* [Notas de la versión de Visual Studio 2019](/visualstudio/releases/2019/release-notes/)
* [Notas de la versión de Visual Studio 2019 para Mac](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [Novedades del SDK de Visual Studio 2019](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Novedades de C++ en Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio/)
* [Novedades de C# 9.0](/dotnet/csharp/whats-new/csharp-9)
* [Novedades de .NET 5](/dotnet/core/dotnet-five)
* [Novedades de .NET Framework](/dotnet/framework/whats-new/)
* [Conferencia Microsoft Build](https://www.microsoft.com/build)
* [Conferencia Microsoft Ignite](https://www.microsoft.com/ignite)
