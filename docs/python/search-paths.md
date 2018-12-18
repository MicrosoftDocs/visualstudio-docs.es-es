---
title: Aplicación de las rutas de acceso de búsqueda de Python
description: Información general del modo en que Visual Studio utiliza las rutas de acceso de búsqueda de Python en entornos y proyectos.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: ab55c7cf1daa02416e6192a02a01ee3f9a35f6f0
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607906"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Cómo usa Visual Studio las rutas de acceso de búsqueda de Python

Con un uso típico de Python, la variable de entorno `PYTHONPATH` (o `IRONPYTHONPATH`, etc.) proporciona la ruta de acceso de búsqueda predeterminada para los archivos de módulo. Es decir, cuando usa una instrucción `from <name> import...`or`import <name>`, Python busca un nombre coincidente en las siguientes ubicaciones en orden:

1. Módulos integrados de Python.
1. La carpeta que contiene el código de Python que está ejecutando.
1. La "ruta de acceso de búsqueda de módulo" tal y como la definió la variable de entorno aplicable. (Consulte [The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) (Ruta de acceso de búsqueda de módulos) y [Environment variables](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) (Variables de entorno) en la documentación principal de Python).

Sin embargo, Visual Studio omite la variable de entorno de ruta de acceso de búsqueda, incluso si se ha establecido para todo el sistema. De hecho, se omite precisamente *porque* se establece para todo el sistema y, por tanto, surgen determinadas preguntas que no se pueden responder automáticamente: ¿Están los módulos a los que se hace referencia diseñados para Python 2.7 o Python 3.6+? ¿Van a invalidar a los módulos de biblioteca estándar? ¿Es consciente el desarrollador de este comportamiento o se trata de un intento de secuestro de sesión malintencionado?

Visual Studio proporciona así un medio para especificar rutas de acceso de búsqueda directamente tanto en entornos como en proyectos. El código que ejecuta o depura en Visual Studio recibe rutas de acceso de búsqueda en el valor de `PYTHONPATH` (y otras variables equivalente). Mediante la incorporación de rutas de acceso de búsqueda, Visual Studio inspecciona las bibliotecas en estas ubicaciones y crea bases de datos de IntelliSense para ellas cuando sea necesario (Visual Studio 2017, versión 15.5 y anteriores; crear la base de datos puede tardar algún tiempo dependiendo del número de bibliotecas).

Para agregar una ruta de búsqueda, vaya al **Explorador de soluciones**, expanda el nodo del proyecto, haga clic con el botón derecho en **Rutas de búsqueda**, seleccione **Add Folder to Search Path** (Agregar carpeta a ruta de búsqueda):

![Comando Agregar carpeta a ruta de búsqueda de Rutas de búsqueda en el Explorador de soluciones](media/search-paths-command.png)

Este comando muestra un explorador en el que se puede seleccionar la carpeta que se va a incluir.

Si la variable de entorno `PYTHONPATH` ya incluye las carpetas que quiere, use **Agregar PYTHONPATH a rutas de búsqueda** como un cómodo acceso directo.

Una vez que se han agregado las carpetas a las rutas de búsqueda, Visual Studio usa esas rutas para cualquier entorno asociado al proyecto. (Puede ver errores si el entorno se basa en Python 3 e intenta agregar una ruta de acceso de búsqueda a los módulos de Python 2.7).

Los archivos con una extensión *.zip* o *.egg* también se pueden agregar como rutas de búsqueda al seleccionar el comando **Add Zip Archive to Search Path** (Agregar archivo Zip a ruta de búsqueda). Al igual que con las carpetas, el contenido de estos archivos se examina y se pone a disposición de IntelliSense.

## <a name="see-also"></a>Vea también

- [Creación y administración de entornos de Python en Visual Studio](managing-python-environments-in-visual-studio.md)
- [Selección de un intérprete para un proyecto](selecting-a-python-environment-for-a-project.md)
- [Uso de requirements.txt para las dependencias](managing-required-packages-with-requirements-txt.md)
- [Referencia de ventana Entornos de Python](python-environments-window-tab-reference.md)
