---
title: R Tools para Visual Studio
description: Herramientas de R para Visual Studio 2017 (RTVS) es una extensión gratuita de código abierto que proporciona muchas características de lenguaje, como IntelliSense, depuración y áreas de trabajo remotas.
ms.date: 11/13/2017
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 385d58834aa96a3ad9e2002020dd1ce4fda3c87f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000011"
---
# <a name="work-with-r-in-visual-studio"></a>Trabajar con R en Visual Studio

R es un entorno y lenguaje muy extensible para cálculos estadísticos y gráficos. Se distribuye de forma gratuita bajo la Licencia para el Público en General GNU, cuenta con soporte técnico de la comunidad seguro y se conoce por su capacidad para generar gráficos con calidad de publicación, como fórmulas y símbolos matemáticos. Puede obtener más información sobre R en [r project.org](https://www.r-project.org/about.html) y [An Introduction to R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html) (Introducción a R).

R Tools para Visual Studio (RTV) es una extensión de [código abierto](https://github.com/microsoft/RTVS) gratis para Visual Studio 2017 y Visual Studio 2015 Update 3 (o posterior), publicada bajo licencia MIT. (Un segundo componente de código abierto denominado [RHost](https://github.com/microsoft/R-Host), que se enlaza a los binarios del intérprete de R, se ha publicado bajo la Licencia para el Público GNU V2).

> [!Note]
> Actualmente, RTVS solo se admite en Visual Studio 2017 en Windows y no en Visual Studio para Mac. Aún no está disponible para Visual Studio 2019.

Para experimentar R en Visual Studio:

- [Instale R Tools](installing-r-tools-for-visual-studio.md).
- Siga la guía [Introducción](getting-started-with-r.md), así como los artículos [Ejemplos](getting-started-samples.md) y [Ayuda](getting-started-help.md).

A continuación, siga los vínculos que aparecen a continuación para obtener más información sobre características relacionadas con R, así como las funcionalidades generales del propio Visual Studio.

| Característica | Descripción | Documentación general de Visual Studio |
| --- | --- | --- |
| [Sistema de proyectos de Visual Studio](r-projects-in-visual-studio.md) | Organice y administre archivos relacionados en una estructura práctica y aproveche plantillas útiles para elementos como código de R, documentación de R, R Markdown, consultas de SQL y procedimientos almacenados. Disfrute también del [administrador de paquetes](r-package-manager-in-visual-studio.md) y de la [integración de SQL Server](integrating-sql-server-with-r.md).  | [Soluciones y proyectos en Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Área de trabajo](r-workspaces-in-visual-studio.md) | RTVS se puede enlazar a áreas de trabajo locales y remotas, lo que le permite desarrollar código de R localmente con conjuntos de datos más pequeños para después ejecutarlo en equipos basados en la nube más eficaces con conjuntos de datos mucho más grandes. | N/D |
| [Opciones de R Tools](options-for-r-tools-in-visual-studio.md) | Controlan diferentes aspectos de RTVS. | [Cuadro de diálogo Opciones](../ide/reference/options-dialog-box-visual-studio.md) |
| [Edición enriquecida, IntelliSense y fragmentos de código](editing-r-code-in-visual-studio.md) | Incluye colores de sintaxis, [IntelliSense](r-intellisense.md) en todo el código y las bibliotecas, formateo de código, ayuda para las firmas, Ir a definición, Buscar todas las referencias, [fragmentos de código](code-snippets-for-r.md) y mucho más. | [Características del editor de código](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown-with-r-in-visual-studio.md) | Los documentos de R Markdown ayudan a compartir los resultados de datos con código de R integrado dentro de bloques de código de Markdown. | N/D |
| [Ventana interactiva](interactive-repl-for-r-in-visual-studio.md) | Proporciona una experiencia completa de REPL para R con la capacidad de ejecutar código fácilmente en un archivo de origen en la ventana interactiva. | N/D |
| [Visualización de datos](visualizing-data-with-r-in-visual-studio.md) | El trazado es una parte integral de la experiencia de R y RTVS admite varias ventanas de trazado independientes, cada una con su propio historial y la capacidad de mover trazados entre ventanas. Los trazados se pueden guardar en archivos de mapa de bits y PDF, o copiarse al Portapapeles como un mapa de bits o metarchivo.  | N/D |
| [Explorador de variables](variable-explorer.md) | Examine variables en los ámbitos globales o específicos del paquete, con la capacidad de ver tablas que se puede ordenar y exportar a CSV. | N/D |
| [Depuración repleta de características](debugging-r-in-visual-studio.md) | Incluye integración con la ventana interactiva. | [Depurar en Visual Studio](/visualstudio/debugger/debugger-feature-tour) |

Vea también las [preguntas más frecuentes](faq.md).

|   |   |
|---|---|
| ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo") | [Vea un vídeo (youtube.com)](https://www.youtube.com/watch?v=dll3IS1bfWQ) de una introducción a Herramientas de R para Visual Studio (12m 36s). Vea también [más vídeos sobre Herramientas de R](https://www.youtube.com/results?search_query=R+Tools+for+visual+studio). |

## <a name="send-us-your-feedback"></a>Envíenos sus comentarios.

1. **Problemas de GitHub**: la mejor forma de ponerse en contacto con el equipo de RTVS es [registrando un problema en GitHub](https://github.com/Microsoft/RTVS/issues) o usando el menú **Herramientas de R** > **Comentarios**.

1. **Enviar una sonrisa/desaprobación**: el menú **Herramientas de R** > **Comentarios** es una forma rápida de enviar comentarios y adjuntar archivos de registro de RTVS para ayudar en el diagnóstico del problema. (Los registros se escriben en *%temp%/RTVSlogs.zip*, en caso de que quiera enviarlos por separado). Si ha desactivado la telemetría de Visual Studio a través del comando de menú **Ayuda** > **Comentarios** > **Configuración** o durante la instalación, el registro está deshabilitado.

1. **Correo electrónico**: puede enviar comentarios directamente al equipo a *rtvsuserfeedback (at) microsoft.com*.
