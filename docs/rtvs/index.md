---
title: R Tools para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: hero-article
ms.assetid: 11324501-ceb6-47a2-ae13-e9e992d3603e
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 2640607b4b4cd817790048e4e1d497f42ed83a08
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2017
---
# <a name="working-with-r-in-visual-studio"></a>Trabajo con R en Visual Studio

R es un entorno y lenguaje muy extensible para cálculos estadísticos y gráficos. Se distribuye de forma gratuita bajo la Licencia para el Público en General GNU, cuenta con soporte técnico de la comunidad seguro y se conoce por su capacidad para generar gráficos con calidad de publicación, como fórmulas y símbolos matemáticos. Puede obtener más información sobre R en [r project.org](https://www.r-project.org/about.html) y [An Introduction to R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html) (Introducción a R).

R Tools para Visual Studio (RTV) es una extensión de [código abierto](https://github.com/microsoft/RTVS) gratis para Visual Studio 2017 y Visual Studio 2015 Update 3 (o posterior), publicada bajo licencia MIT. (Un segundo componente de código abierto denominado [RHost](https://github.com/microsoft/R-Host), que se enlaza a los binarios del intérprete de R, se ha publicado bajo la Licencia para el Público GNU V2).

> [!Note]
> Actualmente RTVS solo se admite en Visual Studio en Windows y no en Visual Studio para Mac.

Para experimentar R en Visual Studio:

- [Instale R Tools](installation.md).
- Siga la guía [Introducción](getting-started-with-r.md), así como los temas [Ejemplos](getting-started-samples.md) y [Obtención de ayuda](getting-started-help.md).

A continuación, siga los vínculos que aparecen a continuación para obtener más información sobre características relacionadas con R, así como las funcionalidades generales del propio Visual Studio.

| Característica | Descripción | Documentación general de Visual Studio | 
| --- | --- | --- |
| [Sistema de proyectos de Visual Studio](projects.md) | Organice y administre archivos relacionados en una estructura práctica y aproveche plantillas útiles para elementos como código de R, documentación de R, R Markdown, consultas de SQL y procedimientos almacenados. Disfrute también del [administrador de paquetes](package-manager.md) y de la [integración de SQL Server](sql-server.md).  | [Soluciones y proyectos en Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Área de trabajo](workspaces.md) | RTVS se puede enlazar a áreas de trabajo locales y remotas, lo que le permite desarrollar código de R localmente con conjuntos de datos más pequeños para después ejecutarlo en equipos basados en la nube más eficaces con conjuntos de datos mucho más grandes. | no disponible |
| [Opciones de R Tools](options.md) | Controlan diferentes aspectos de RTVS. | [Cuadro de diálogo Opciones](../ide/reference/options-dialog-box-visual-studio.md) |
| [Edición enriquecida, IntelliSense y fragmentos de código](code-editing.md) | Incluye colores de sintaxis, [IntelliSense](code-intellisense.md) en todo el código y las bibliotecas, formateo de código, ayuda para las firmas, Ir a definición, Buscar todas las referencias, [fragmentos de código](code-snippets.md) y mucho más. | [Escribir código en el editor de código y texto](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown.md) | Los documentos de R Markdown ayudan a compartir los resultados de datos con código de R integrado dentro de bloques de código de Markdown. | no disponible |
| [Ventana interactiva](interactive-repl.md) | Proporciona una experiencia completa de REPL para R con la capacidad de ejecutar código fácilmente en un archivo de origen en la ventana interactiva. | no disponible |
| [Visualización de datos](visualizing-data.md) | El trazado es una parte integral de la experiencia de R y RTVS admite varias ventanas de trazado independientes, cada una con su propio historial y la capacidad de mover trazados entre ventanas. Los trazados se pueden guardar en archivos de mapa de bits y PDF, o copiarse al Portapapeles como un mapa de bits o metarchivo.  | no disponible |
| [Explorador de variables](variable-explorer.md) | Examine variables en los ámbitos globales o específicos del paquete, con la capacidad de ver tablas que se puede ordenar y exportar a CSV. | no disponible |
| [Depuración repleta de características](debugging.md) | Incluye integración con la ventana interactiva. | [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md) |

Vea también las [preguntas más frecuentes](faq.md).

El vídeo siguiente también proporciona un informe (5 minutos y 48 segundos) de las funcionalidades de R Tools:

> [!VIDEO https://www.youtube.com/embed/RcSDEfMgUvU]

## <a name="send-us-your-feedback"></a>Envíenos sus comentarios.

1. **Problemas de Github**: la mejor forma de ponerse en contacto con el equipo de RTVS es [archivando un problema en GitHub](https://github.com/Microsoft/RTVS/issues), o mediante el menú **R Tools > Comentarios** menú.

1. **Enviar una sonrisa o Enviar una desaprobación**: el menú **R Tools > Comentarios** es una manera rápida para enviar comentarios y adjuntar archivos de registro de RTVS para ayudar en el diagnóstico del problema. (Los registros se escriben en `%temp%/RTVSlogs.zip` en caso de que desee enviarlos por separado). El registro está deshabilitado si ha desactivado la telemetría de Visual Studio a través del comando de menú **Ayuda > Comentarios > Configuración** o durante la instalación.

1. **Correo electrónico**: puede enviar comentarios directamente al equipo a *rtvsuserfeedback (arroba) microsoft.com*.
