---
title: R Tools para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 5/1/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11324501-ceb6-47a2-ae13-e9e992d3603e
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: e166fceac0f29b5ee0880d2542eedddc066fa9f1
ms.contentlocale: es-es
ms.lasthandoff: 05/12/2017

---

# <a name="working-with-r-in-visual-studio"></a>Trabajo con R en Visual Studio

R es un entorno y lenguaje muy extensible para cálculos estadísticos y gráficos. Se distribuye de forma gratuita bajo la Licencia para el Público en General GNU, cuenta con soporte técnico de la comunidad seguro y se conoce por su capacidad para generar gráficos con calidad de publicación, como fórmulas y símbolos matemáticos. Puede obtener más información sobre R en [r project.org](https://www.r-project.org/about.html) y [An Introduction to R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html) (Introducción a R).

R Tools para Visual Studio (RTV) es una extensión de [código abierto](https://github.com/microsoft/RTVS) gratis para Visual Studio 2017 y Visual Studio 2015 Update 3 (o posterior), publicada bajo licencia MIT. (Un segundo componente de código abierto denominado [RHost](https://github.com/microsoft/R-Host), que se enlaza a los binarios del intérprete de R, se ha publicado bajo la Licencia para el Público GNU V2).

Para experimentar R en Visual Studio:

- [Instale R Tools](installation.md).
- Siga la guía [Introducción](getting-started-with-r.md), así como los temas [Ejemplos](getting-started-samples.md) y [Obtención de ayuda](getting-started-help.md).

A continuación, siga los vínculos que aparecen a continuación para obtener más información sobre características relacionadas con R, así como las funcionalidades generales del propio Visual Studio.

| Característica | Descripción | Documentación general de Visual Studio | 
| --- | --- | --- |
| [Sistema de proyectos de Visual Studio](projects.md) | Organice y administre archivos relacionados en una estructura práctica y aproveche plantillas útiles para elementos como código de R, documentación de R, R Markdown, consultas de SQL y procedimientos almacenados. Disfrute también del [administrador de paquetes](package-manager.md) y de la [integración de SQL Server](sql-server.md).  | [Soluciones y proyectos en Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Área de trabajo](workspaces.md) | RTVS se puede enlazar a áreas de trabajo locales y remotas, lo que le permite desarrollar código de R localmente con conjuntos de datos más pequeños para después ejecutarlo en equipos basados en la nube más eficaces con conjuntos de datos mucho más grandes y colaborar con compañeros. | no disponible |
| [Opciones de R Tools](options.md) | Controlan diferentes aspectos de RTVS. | [Cuadro de diálogo Opciones](../ide/reference/options-dialog-box-visual-studio.md) |
| [Edición enriquecida, IntelliSense y fragmentos de código](code-editing.md) | Incluye colores de sintaxis, [IntelliSense](code-intellisense.md) en todo el código y las bibliotecas, formateo de código, ayuda para las firmas, Ir a definición, Buscar todas las referencias, [fragmentos de código](code-snippets.md) y mucho más. | [Escribir código en el editor de código y texto](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown.md) | Los documentos de R Markdown ayudan a compartir los resultados de datos con código de R integrado dentro de bloques de código de Markdown. | no disponible |
| [Ventana interactiva](interactive-repl.md) | Proporciona una experiencia completa de REPL para R con la capacidad de ejecutar código fácilmente en un archivo de origen en la ventana interactiva. | no disponible |
| [Visualización de datos](visualizing-data.md) | El trazado es una parte integral de la experiencia de R y RTVS admite varias ventanas de trazado independientes, cada una con su propio historial y la capacidad de mover trazados entre ventanas. Los trazados se pueden guardar en archivos de mapa de bits y PDF, o copiarse al Portapapeles como un mapa de bits o metarchivo.  | no disponible |
| [Explorador de variables](variable-explorer.md) | Examine variables en los ámbitos globales o específicos del paquete, con la capacidad de ver tablas que se puede ordenar y exportar a CSV. | no disponible |
| [Depuración repleta de características](debugging.md) | Incluye integración con la ventana interactiva. | [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md) |

El vídeo siguiente también proporciona un informe (5 minutos y 48 segundos) de las funcionalidades de R Tools:

> [!VIDEO https://www.youtube.com/embed/RcSDEfMgUvU]

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

**P. ¿Funciona RTVS con las ediciones de Express de Visual Studio?**

Un archivo . No.

**P. ¿Con qué intérpretes de R funciona RTVS?**

Un archivo . [CRAN R](https://cran.r-project.org/), [Microsoft R Client y Microsoft R Server](https://msdn.microsoft.com/microsoft-r/)

**P. ¿Dónde puedo descargar esos intérpretes?**

Un archivo . Consulte [Instalación](installation.md).

**P. ¿Puedo utilizar extensiones de Visual Studio con RTV?**

Un archivo . Por supuesto. De hecho, a continuación se muestran algunas que conocen las personas que trabajan con R.

- [VsVim para enlaces de teclado vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [Github](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Editor de Markdown con vista previa activa](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Consulte [Visual Studio Marketplace](https://marketplace.visualstudio.com/) para más información.

**P. Dado que RTVS está en Visual Studio, ¿significa eso que R se puede utilizar fácilmente con C#, C++ y otros lenguajes de Microsoft?**

Un archivo . No. RTVS es una herramienta para desarrollar código de R y usa los intérpretes de R nativos estándar. Actualmente no hay compatibilidad para la interoperabilidad entre R y otros lenguajes.

**P. Falta la característica X, ¡pero RStudio la tiene!**

Un archivo . RStudio es un IDE fantástico y maduro para R que se ha estado desarrollando durante muchos años. RTVS pretende tener todas las características importantes que el usuario necesita para tener éxito. Ayude a priorizar el trabajo futuro realizando la [encuesta sobre RTVS](https://www.surveymonkey.com/r/RTVS1).

**P. ¿Funcionará RTVS en OS X o Linux?**

Un archivo . No, RTVS se basa en Visual Studio, que es una implementación solo para Windows. Dicho esto, Microsoft está investigando la creación de un nuevo conjunto de herramientas basadas en [Visual Studio Code](https://code.visualstudio.com/), el popular editor multiplataforma de Microsoft.

**P. ¿Puedo contribuir a RTV?**

Un archivo . Por supuesto. El código fuente reside en [Github](https://github.com/microsoft/RTVS). Utilice el rastreador de problemas para enviar errores y comentarios existentes en los archivos.

También se agradece la contribución a esta documentación; simplemente seleccione el comando **Editar** en la esquina superior derecha de cualquier página. Los comentarios sobre la documentación también se agradecen, que se pueden agregar en la parte inferior de cualquier página.

**P. ¿Funciona RTVS con mi sistema de control de código fuente?**

Un archivo . Sí, puede usar cualquier sistema de control de código fuente que esté integrado en Visual Studio.

**P. No uso una configuración regional en inglés de Estados Unidos en Windows o en Visual Studio. ¿Funcionará RTV?**

Un archivo . La versión 1.0 de RTVS será solo en inglés. La versión 1.1 se traducirá al mismo conjunto de idiomas que Visual Studio. Mientras tanto, utilice el [paquete de idioma en inglés para Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48157) o, en Visual Studio 2017, ejecute el programa de instalación y seleccione Inglés en la pestaña **Paquetes de idioma**.

![Configuración internacional para Visual Studio de 2017](media/FAQ-international-settings.png)

**P. ¿Funcionará RTVS con las ediciones de 32 bits de R?**

Un archivo . No, RTVS solo es compatible con las ediciones de 64 bits de R que se ejecutan en ediciones de 64 bits de Windows.

**P. Me gusta mi configuración actual de Visual Studio, pero desea probar la nueva configuración de ciencia de datos. ¿Qué debo hacer?**

Un archivo . Guarde la configuración actual de Visual Studio mediante **Herramientas > Importar y exportar configuraciones...**  y luego cambie la configuración de ciencia de datos. Para restaurar la configuración guardada, use el comando **Importar y exportar configuraciones...**  de nuevo.

**P. ¿Cuáles es la configuración de `.gitignore` recomendada para un proyecto de RTV?**

Un archivo . Github mantiene un repositorio principal de los archivos de `.gitignore` recomendados. Puede verlo aquí: [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

**P. ¿Puedo almacenar mi proyecto de Visual Studio en un recurso compartido de red?**

Un archivo . No, Visual Studio no lo admite.

## <a name="send-us-your-feedback"></a>Envíenos sus comentarios.

1. **Problemas de Github**: la mejor forma de ponerse en contacto con el equipo de RTVS es [archivando un problema en GitHub](https://github.com/Microsoft/RTVS/issues), o mediante el menú **R Tools > Comentarios** menú.

1. **Enviar una sonrisa o Enviar una desaprobación**: el menú **R Tools > Comentarios** es una manera rápida para enviar comentarios y adjuntar archivos de registro de RTVS para ayudar en el diagnóstico del problema. (Los registros se escriben en `%temp%/RTVSlogs.zip` en caso de que desee enviarlos por separado). Tenga en cuenta que el registro está deshabilitado si ha desactivado la telemetría de Visual Studio a través del comando de menú **Ayuda > Comentarios > Configuración** o durante la instalación.

1. **Correo electrónico**: puede enviar comentarios directamente al equipo a *rtvsuserfeedback (arroba) microsoft.com*.

