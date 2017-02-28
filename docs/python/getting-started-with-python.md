---
title: "Introducción a Python en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 1/3/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 11
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
translationtype: Human Translation
ms.sourcegitcommit: 7d0b0b0b12b9d65f26b67d6f797abc0cf7a0c2c9
ms.openlocfilehash: e7cc978dabb401a8e9bab6791988aa737edb76b0
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-python-in-visual-studio"></a>Introducción a Python en Visual Studio

Python ([http://python.org/download/](http://python.org/download/)) es un lenguaje de programación popular confiable, flexible, libre de usar, fácil de aprender y admitido por una gran comunidad de desarrolladores y muchas bibliotecas gratuitas. Python funciona en todos los principales sistemas operativos y es útil para muchos propósitos, incluyendo aplicaciones web, servicios web, aplicaciones de escritorio, secuencias de comandos y la informática científica. Por lo tanto lo usan muchas universidades, científicos, programadores ocasionales y desarrolladores profesionales.

Para obtener más información sobre el lenguaje, comience con [Python para principiantes](https://www.python.org/about/gettingstarted/) (python.org).

## <a name="python-tools-for-visual-studio"></a>Python Tools para Visual Studio

Python Tools para Visual Studio (PTVS), es una extensión gratuita de código abierto para Visual Studio que proporciona una experiencia de desarrollo Python eficaz, incluyendo un sistema de proyectos y plantillas, edición enriquecida e IntelliSense, depuración completa, y una variedad de otras herramientas.

La extensión proporciona las siguientes características:

- Compatibilidad con varios intérpretes: distintas versiones de CPython, IronPython e IPython
- Un sistema de proyectos que selecciona implícitamente una estructura de carpetas de código Python y también permite control explícito para que pueda identificar el código de la aplicación, el código de prueba, las páginas web, JavaScript, los scripts de compilación y demás.
- Plantillas de proyecto de consola, web, Azure, datos científicos y otros tipos de proyectos.
- Características de edición avanzada y comprensión de código, incluyendo usar color de sintaxis, autocompletado en el código y las bibliotecas, ayuda para las firmas, vista de clases, Ir a definición, Buscar todas las referencias, refactorización y mucho más.
- Una ventana interactiva (REPL)
- Depuración enriquecida sin un proyecto de Visual Studio, la capacidad de adjuntar a un ejecutable existente, depuración en modo mixto, depuración remota en Windows/Linux/Mac y depuración en la ventana interactiva.

- IPython con visualizaciones de datos.
- Compatibilidad con IronPython y .NET/WPF.
- Herramientas de generación de perfiles.
- Herramientas de pruebas.
- El [SDK de Azure para Python](#azure-sdk-for-python)

Los siguientes recursos le ayudarán a empezar:

- [Instalar Herramientas de Python para Visual Studio](https://www.visualstudio.com/vs/python/).
- [Guía de instalación](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)
- [Introducción y vídeos Deep Dive cortos](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
- Demostración de instalación y características (27 minutos)](https://www.youtube.com/watch?v=JNNAOypc6Ek)
- [Documentación](https://github.com/Microsoft/PTVS/wiki)
- [Código fuente](https://github.com/Microsoft/ptvs)


## <a name="azure-sdk-for-python"></a>SDK de Azure para Python

El SDK de Azure para Python, que es compatible con Windows, Mac y Linux, facilita el uso y la administración de los servicios de Microsoft Azure. Consulte los siguientes recursos para obtener más información:

- Para instalar el SDK, use el [Índice de paquetes de Python](https://pypi.python.org/pypi/azure) o siga [Instalar Python y el SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/) en la documentación de Azure.
- [El SDK de Azure SDK para el Centro de desarrolladores de Python](http://azure.microsoft.com/en-us/develop/python/) dispone de numerosos recursos de ayuda, desde instalación hasta documentación con tutoriales.  A continuación se indican algunos aspectos destacados:
- Guías de ayuda y procedimientos:
  - [Blob de almacenamiento](http://azure.microsoft.com/en-us/develop/python/how-to-guides/blob-service/)
  - [Cola de almacenamiento](http://azure.microsoft.com/en-us/develop/python/how-to-guides/queue-service/)
  - [Tabla de almacenamiento](http://azure.microsoft.com/en-us/develop/python/how-to-guides/table-service/)
  - [Colas del bus de servicio](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-queues/)   - [Temas y suscripciones del bus de servicio](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-topics/)
  - [Administración de servicios](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-management/)
- El [repositorio de GitHub del SDK](https://github.com/Azure/azure-sdk-for-python) tiene [pruebas unitarias](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests) que también son una buena fuente de información sobre las API.


## <a name="scientific-computing"></a>Ciencia computacional
Además de todas las bibliotecas de datos científicos de Python, Python Tools para Visual Studio admite IPython y blocs de notas de IPython, que se pueden hospedar en Azure.

Se recomienda obtener IPython y las bibliotecas informáticas científicas (matplotlib, scipy, numpy, etc.) de la [Universidad de California en Irvine](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).

## <a name="see-also"></a>Vea también
 [Introducción a PTVS: configuración de Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
 [Introducción a PTVS: comenzar a codificar (proyectos)](../python/getting-started-with-ptvs-start-coding-projects.md)
 [Introducción a PTVS: editar código](../python/getting-started-with-ptvs-editing-code.md)
 [Introducción a PTVS: depurar](../python/getting-started-with-ptvs-debugging.md)
 [Introducción a PTVS: Python interactivo](../python/getting-started-with-ptvs-interactive-python.md)
 [Introducción a PTVS: compilar un sitio web en Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
