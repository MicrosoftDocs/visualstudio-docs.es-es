---
title: Getting Started with Python | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 21e724e585f2a5bf0e1fe2a6b70f89c1bd5f5eec
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298199"
---
# <a name="getting-started-with-python"></a>Introducción a Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

The Python Tools for Visual Studio (PTVS), is a free, [open-source](https://github.com/Microsoft/ptvs) plug-in for Visual Studio that a powerful Python development experience.  
  
## <a name="python-the-language"></a>Lenguaje de Python
  
Python is a popular programming language that is used by many universities, scientists, app scripters, casual developers, and professional developers, working on applications, web sites, and cloud services.

As a programming language, Python is:
  
- Confiable.
- Generally useful for scripting quick programs, app scripting, desktop apps, web servers, web services, and scientific computing.
- Fácil de aprender y con un diseño adecuado para promover una codificación correcta (numerosas universidades lo usan para cursos de introducción a la programación).
- Flexible, supporting imperative, functional, and object-oriented programming styles.
- De código abierto y gratuito.
- Runs well on all major operating systems.  
- Supported by many free, useful, and well-designed libraries.  
- Supported by lots of documentation, samples, and a strong developer community.  

To learn more about the language, start with [Python for Beginners](https://www.python.org/about/gettingstarted/) on python.org.

To install Python itself, visit [https://www.python.org/download/](https://www.python.org/download/).

## <a name="python-tools-for-visual-studio"></a>Python Tools para Visual Studio
  
The Python Tools for Visual Studio, which you can install from [visualstudio.com](https://www.visualstudio.com/explore/python-vs), provide the following features:  
  
- Compatibilidad con varios intérpretes: distintas versiones de CPython, IronPython e IPython  
- Un sistema de proyectos que selecciona implícitamente una estructura de carpetas de código Python y también permite control explícito para que pueda identificar el código de la aplicación, el de prueba, las páginas web, JavaScript, los scripts de compilación y demás.  
- Plantillas de proyecto de consola, web, Azure, datos científicos y otros tipos de proyectos.    
- The Azure SDK for Python (see below)    
- Características de edición avanzada y comprensión de código, incluyendo usar color de sintaxis, autocompletado en el código y las bibliotecas, ayuda para las firmas, vista de clases, Ir a definición, Buscar todas las referencias, refactorización y mucho más.    
- Una ventana interactiva (REPL)
- IPython con visualizaciones de datos.
- Compatibilidad con IronPython y .NET/WPF.    
- Depuración enriquecida sin un proyecto de Visual Studio, la capacidad de adjuntar a un ejecutable existente, depuración en modo mixto, depuración remota en Windows/Linux/Mac y depuración en la ventana interactiva.   
- Herramientas de generación de perfiles.  
- Herramientas de pruebas.  
  
Los siguientes recursos le ayudarán a empezar:

- [Guía de instalación](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [Introducción y vídeos Deep Dive cortos](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
- Demostración de instalación y características (27 minutos)]( https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Documentación](https://github.com/Microsoft/PTVS/wiki)  

Note that Visual Studio does not at present provide the means to create a stand-alone executable using Python, which essentially means a program with an embedded Python interpreter. Pero hay varias formas dentro de la comunidad de Python para hacerlo, como se describe en [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython también se puede insertar en una aplicación nativa, como se describe en la entrada de blog [Using CPython's Embeddable Zip File](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/) (Uso del archivo Zip insertable de CPython).
  
## <a name="building-ui-with-python"></a>Building UI with Python  

The main offering for building a UI with Python is the [Qt Project](https://www.qt.io/qt-for-application-development/), with bindings for Python known as [PySide (the official binding)](https://wiki.qt.io/PySide) (also see [PySide downloads](https://download.qt.io/official_releases/pyside/.))and [PyQt](https://wiki.python.org/moin/PyQt). En la actualidad, la compatibilidad con Python en Visual Studio no incluye herramientas específicas para el desarrollo de la interfaz de usuario.

## <a name="azure-sdk-for-python"></a>SDK de Azure para Python
  
El SDK de Azure para Python, que es compatible con Windows, Mac y Linux, facilita el uso y la administración de los servicios de Microsoft Azure. Consulte los siguientes recursos para obtener más información: 

- Para instalar el SDK, use el [Índice de paquetes de Python](https://pypi.python.org/pypi/azure) o siga [Instalar Python y el SDK](https://docs.microsoft.com/azure/python/python-sdk-azure-install) en la documentación de Azure. 
- [El SDK de Azure SDK para el Centro de desarrolladores de Python](https://azure.microsoft.com/develop/python/) dispone de numerosos recursos de ayuda, desde instalación hasta documentación con tutoriales.  A continuación se indican algunos aspectos destacados:  
- Guías de ayuda y procedimientos:
  - [Blob de almacenamiento](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Cola de almacenamiento](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Tabla de almacenamiento](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Colas de Service Bus](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Temas y suscripciones de Service Bus](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Administración de servicios](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Ciencia computacional

Además de todas las bibliotecas de datos científicos de Python, Python Tools para Visual Studio admite IPython y blocs de notas de IPython, que se pueden hospedar en Azure.

Se recomienda obtener IPython y las bibliotecas informáticas científicas (matplotlib, scipy, numpy, etc.) de la [Universidad de California en Irvine](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).  
  
## <a name="see-also"></a>Vea también  

[Introducción a PTVS: configuración de Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[Introducción a PTVS: comenzar a codificar (proyectos)](../python/getting-started-with-ptvs-start-coding-projects.md)
[Introducción a PTVS: editar código](../python/getting-started-with-ptvs-editing-code.md)
[Introducción a PTVS: depurar](../python/getting-started-with-ptvs-debugging.md)
[Introducción a PTVS: Python interactivo](../python/getting-started-with-ptvs-interactive-python.md)
[Introducción a PTVS: compilar un sitio web en Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
