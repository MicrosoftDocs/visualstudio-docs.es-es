---
title: Preguntas frecuentes sobre las herramientas de R para Visual Studio
description: Preguntas más frecuentes sobre R en Visual Studio.
ms.date: 12/04/2017
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 8c89f1d59405fb7475e827cac9624c6623d7041e
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189100"
---
# <a name="frequently-asked-questions"></a>Preguntas más frecuentes

## <a name="visual-studio-support"></a>Compatibilidad con Visual Studio

**P. ¿RTVS funciona en OS X o Linux?**

A. Actualmente, RTVS se basa en Visual Studio, que es una implementación solo para Windows. Microsoft está investigando el asunto de la compatibilidad en Visual Studio Code y Visual Studio para Mac. Eche un vistazo al [problema de RTVS n.º 1295](https://github.com/Microsoft/RTVS/issues/1295).

**P. ¿Funciona RTVS con las ediciones de Express de Visual Studio?**

A. No.

**P. ¿Puedo utilizar extensiones de Visual Studio con RTV?**

A. Por supuesto. De hecho, a continuación se muestran algunas que conocen las personas que trabajan con R.

- [VsVim para enlaces de teclado vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Editor de Markdown con vista previa activa](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Consulte [Visual Studio Marketplace](https://marketplace.visualstudio.com/) para más información.

**P. Dado que RTVS está en Visual Studio, ¿significa eso que R se puede utilizar fácilmente con C#, C++ y otros lenguajes de Microsoft?**

A. No. RTVS es una herramienta para desarrollar código de R y usa los intérpretes de R nativos estándar. Actualmente no hay compatibilidad para la interoperabilidad entre R y otros lenguajes.

**P. ¿RTVS funciona con una configuración regional que no sea en inglés?**

A. La versión 1.0 de RTVS es solo en inglés. La versión 1.1 se traducirá al mismo conjunto de idiomas que Visual Studio. Mientras tanto, utilice el [paquete de idioma en inglés para Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48157) o, en Visual Studio 2017, ejecute el programa de instalación y seleccione Inglés en la pestaña **Paquetes de idioma**.

![Configuración internacional para Visual Studio de 2017](media/FAQ-international-settings.png)

**P. Me gusta mi configuración actual de Visual Studio, pero desea probar la nueva configuración de ciencia de datos. ¿Qué debo hacer?**

A. Guarde la configuración actual de Visual Studio mediante **Herramientas** > **Importar y exportar configuraciones** y luego cambie la configuración de ciencia de datos. Para restaurar la configuración guardada, use el comando **Importar y exportar configuraciones** de nuevo.

**P. ¿Puedo almacenar mi proyecto de Visual Studio en un recurso compartido de red?**

A. No, Visual Studio no es compatible con la carga de proyectos de un recurso compartido de red.

## <a name="r-interpretersintegration"></a>Integración/intérpretes de R

**P. ¿Con qué intérpretes de R funciona RTVS?**

A. [CRAN R](https://cran.r-project.org/), [Microsoft R Client y Microsoft Machine Learning Server](/machine-learning-server/)

**P. ¿Dónde puedo descargar esos intérpretes?**

A. Consulte [Instalación](installing-r-tools-for-visual-studio.md).

P. **¿Qué es Microsoft R Server?**

A. R Server es el nombre anterior de [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

**P. ¿RTVS funciona con las ediciones de 32 bits de R?**

A. No, RTVS solo es compatible con las ediciones de 64 bits de R que se ejecutan en ediciones de 64 bits de Windows.

**P. ¿Funciona RTVS con mi sistema de control de código fuente?**

A. Sí, puede usar cualquier sistema de control de código fuente que esté integrado en Visual Studio.

**P. ¿Cuál es la configuración de *.gitignore* recomendada para un proyecto de RTVS?**

A. GitHub mantiene un repositorio de los archivos *.gitignore* recomendados. Puede verlo aquí: [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Servicios remotos

Q. **¿Qué es Servicios remotos en Visual Studio?**

A. Con Servicios remotos de R para Visual Studio se puede configurar un equipo Windows o Linux para, luego, conectarse a él desde RTVS. Vea [Configurar áreas de trabajo remotas](setting-up-remote-r-workspaces.md).

Q. **¿RTVS se puede conectar a Microsoft Machine Learning Server?**

A. No, porque Microsoft ML Server es una tecnología distinta y no proporciona el mecanismo de conectividad que RTVS necesita.

Q. **¿Puede RTVS conectarse a una máquina virtual creada con la imagen de máquina virtual de ciencia de datos en Azure?**

A. Sí. La imagen [Máquina virtual de ciencia de datos - Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) viene preinstalada con Servicios remotos de R para Visual Studio.

P. **¿Puede RTVS conectarse a un equipo remoto que tenga R instalado?**

Para ejecutar código R en un equipo remoto, debe haber algún servicio que realice escuchas de solicitudes, reciba el código y envíe los resultados al equipo cliente, que es justamente lo que Servicios remotos de R hace en Visual Studio. Vea [Configurar áreas de trabajo remotas](setting-up-remote-r-workspaces.md).

Q. **¿Qué es una sesión remota?**

A. Vea el artículo [Execute on remote server](/machine-learning-server/r/how-to-execute-code-remotely) (Ejecutar en un servidor remoto) en la documentación de Machine Learning Server.

## <a name="rtvs-development-and-features"></a>Características y desarrollo de RTVS

**P. Falta la característica X, ¡pero RStudio la tiene!**

A. RStudio es un IDE fantástico y maduro para R que se ha estado desarrollando durante muchos años. RTVS pretende tener todas las características importantes que el usuario necesita para tener éxito. Ayude a priorizar el trabajo futuro mediante el archivado de problemas en [GitHub](https://github.com/Microsoft/RTVS/issues/).

**P. ¿Puedo contribuir a RTV?**

A. Por supuesto. El código fuente reside en [Github](https://github.com/microsoft/RTVS). Utilice el rastreador de problemas para enviar errores y comentar los archivados.

También se agradece la contribución a esta documentación: solo tiene que seleccionar el comando **Editar** en la esquina superior derecha de cualquier página. Los comentarios sobre la documentación también se agradecen, que se pueden agregar en la parte inferior de cualquier página.
