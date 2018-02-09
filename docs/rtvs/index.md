---
title: R Tools para Visual Studio | Microsoft Docs
description: "Herramientas de R para Visual Studio (RTVS) es una extensión gratuita y de código abierto que proporciona muchas características de lenguaje, como IntelliSense, depuración y áreas de trabajo remotas."
ms.custom: 
ms.date: 11/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: hero-article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 762b56336fa790d57ffa38510aa319e744b5959c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="working-with-r-in-visual-studio"></a>Trabajo con R en Visual Studio

R es un entorno y lenguaje muy extensible para cálculos estadísticos y gráficos. Se distribuye de forma gratuita bajo la Licencia para el Público en General GNU, cuenta con soporte técnico de la comunidad seguro y se conoce por su capacidad para generar gráficos con calidad de publicación, como fórmulas y símbolos matemáticos. Puede obtener más información sobre R en [r project.org](https://www.r-project.org/about.html) y [An Introduction to R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html) (Introducción a R).

R Tools para Visual Studio (RTV) es una extensión de [código abierto](https://github.com/microsoft/RTVS) gratis para Visual Studio 2017 y Visual Studio 2015 Update 3 (o posterior), publicada bajo licencia MIT. (Un segundo componente de código abierto denominado [RHost](https://github.com/microsoft/R-Host), que se enlaza a los binarios del intérprete de R, se ha publicado bajo la Licencia para el Público GNU V2).

> [!Note]
> Actualmente RTVS solo se admite en Visual Studio en Windows y no en Visual Studio para Mac.

Para experimentar R en Visual Studio:

- [Instale R Tools](installing-r-tools-for-visual-studio.md).
- Siga la guía [Introducción](getting-started-with-r.md), así como los artículos [Ejemplos](getting-started-samples.md) y [Ayuda](getting-started-help.md).

A continuación, siga los vínculos que aparecen a continuación para obtener más información sobre características relacionadas con R, así como las funcionalidades generales del propio Visual Studio.

| Característica | Description | Documentación general de Visual Studio | 
| --- | --- | --- |
| [Sistema de proyectos de Visual Studio](r-projects-in-visual-studio.md) | Organice y administre archivos relacionados en una estructura práctica y aproveche plantillas útiles para elementos como código de R, documentación de R, R Markdown, consultas de SQL y procedimientos almacenados. Disfrute también del [administrador de paquetes](r-package-manager-in-visual-studio.md) y de la [integración de SQL Server](integrating-sql-server-with-r.md).  | [Soluciones y proyectos en Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Área de trabajo](r-workspaces-in-visual-studio.md) | RTVS se puede enlazar a áreas de trabajo locales y remotas, lo que le permite desarrollar código de R localmente con conjuntos de datos más pequeños para después ejecutarlo en equipos basados en la nube más eficaces con conjuntos de datos mucho más grandes. | N/D |
| [Opciones de R Tools](options-for-r-tools-in-visual-studio.md) | Controlan diferentes aspectos de RTVS. | [Cuadro de diálogo Opciones](../ide/reference/options-dialog-box-visual-studio.md) |
| [Edición enriquecida, IntelliSense y fragmentos de código](editing-r-code-in-visual-studio.md) | Incluye colores de sintaxis, [IntelliSense](r-intellisense.md) en todo el código y las bibliotecas, formateo de código, ayuda para las firmas, Ir a definición, Buscar todas las referencias, [fragmentos de código](code-snippets-for-r.md) y mucho más. | [Escribir código en el editor de código y texto](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown-with-r-in-visual-studio.md) | Los documentos de R Markdown ayudan a compartir los resultados de datos con código de R integrado dentro de bloques de código de Markdown. | N/D |
| [Ventana interactiva](interactive-repl-for-r-in-visual-studio.md) | Proporciona una experiencia completa de REPL para R con la capacidad de ejecutar código fácilmente en un archivo de origen en la ventana interactiva. | N/D |
| [Visualización de datos](visualizing-data-with-r-in-visual-studio.md) | El trazado es una parte integral de la experiencia de R y RTVS admite varias ventanas de trazado independientes, cada una con su propio historial y la capacidad de mover trazados entre ventanas. Los trazados se pueden guardar en archivos de mapa de bits y PDF, o copiarse al Portapapeles como un mapa de bits o metarchivo.  | N/D |
| [Explorador de variables](variable-explorer.md) | Examine variables en los ámbitos globales o específicos del paquete, con la capacidad de ver tablas que se puede ordenar y exportar a CSV. | N/D |
| [Depuración repleta de características](debugging-r-in-visual-studio.md) | Incluye integración con la ventana interactiva. | [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md) |

Vea también las [preguntas más frecuentes](faq.md).

El vídeo siguiente también proporciona un informe (5 minutos y 48 segundos) de las funcionalidades de R Tools:

> [!VIDEO https://www.youtube.com/embed/RcSDEfMgUvU]

## <a name="send-us-your-feedback"></a>Envíenos sus comentarios.

1. **Problemas de Github**: la mejor forma de ponerse en contacto con el equipo de RTVS es [archivando un problema en GitHub](https://github.com/Microsoft/RTVS/issues), o mediante el menú **R Tools > Comentarios** menú.

1. **Enviar una sonrisa o Enviar una desaprobación**: el menú **R Tools > Comentarios** es una manera rápida para enviar comentarios y adjuntar archivos de registro de RTVS para ayudar en el diagnóstico del problema. (Los registros se escriben en `%temp%/RTVSlogs.zip` en caso de que desee enviarlos por separado). El registro está deshabilitado si ha desactivado la telemetría de Visual Studio a través del comando de menú **Ayuda > Comentarios > Configuración** o durante la instalación.

1. **Correo electrónico**: puede enviar comentarios directamente al equipo a *rtvsuserfeedback (arroba) microsoft.com*.
