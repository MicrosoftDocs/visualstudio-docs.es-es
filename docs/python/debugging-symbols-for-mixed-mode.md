---
title: "Símbolos de la depuración en modo mixto con Herramientas de Python para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be5fdf2f-b55f-488a-9772-58adfe07a7ab
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
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 9f7ba91262875344ded1e09277883abff292f359
ms.lasthandoff: 03/07/2017

---

# <a name="installing-debugging-symbols-for-python-interpreters"></a>Instalación de símbolos de depuración para intérpretes de Python

Para proporcionar una experiencia de depuración completa, el [depurador en modo mixto](debugging-mixed-mode.md) de Herramientas de Python para Visual Studio (PTVS) necesita analizar numerosas estructuras de datos internas en el intérprete de Python que se va a utilizar. El propio intérprete necesita símbolos de depuración para esta tarea. Por ejemplo, el archivo de símbolos correspondiente para python27.dll es python27.pdb.

Cuando PTVS detecta que necesita símbolos, le solicita que vaya a una carpeta que contenga archivos de símbolo o que los descargue:

![Solicitud de símbolos durante la depuración en modo mixto](media/mixed-mode-debugging-symbols-required.png) 

Puede descargar los archivos de símbolos de la [distribución oficial](#official-distribution) o en [Enthought Canopy](#enthought-canopy), tal como se describe a continuación. Si utiliza una distribución de Python de terceros, como ActiveState Python, debe ponerse en contacto con los autores de la distribución para solicitarles los símbolos. (WinPython, sin embargo, incorpora el intérprete de Python estándar sin cambios, así que, en este caso, use los símbolos de la distribución oficial para el número de versión correspondiente).

Una vez que ha obtenido los archivos .pdb para su intérprete, PTVS debe reconocerlos como se indica a continuación, a fin de que se carguen automáticamente cuando se inicia una sesión de depuración:

1. Seleccione el comando de menú **Herramientas > Opciones** y después vaya a **Depuración > Símbolos**:

![Opciones de símbolos para el depurador en modo mixto](media/mixed-mode-debugging-symbols.png)

1. Seleccione el botón Agregar en la barra de herramientas (el botón más a la izquierda se muestra arriba, a la derecha del icono !), navegue hasta la carpeta que contiene los archivos .pdb y seleccione **Aceptar**.


## <a name="official-distribution"></a>Distribución oficial

En Python 3.5 y versiones posteriores, puede incluir símbolos de depuración a través del instalador (con una nueva instalación o con la modificación de una existente). Seleccione **Instalación personalizada**, seleccione **Siguiente** para acceder a **Opciones avanzadas** y después seleccione los cuadros "Download debugging symbols**(Descargar símbolos de depuración) y**Download debug binaries** (Descargar archivos binarios de depuración):

![Instalador de Python 3.x que incluye símbolos de depuración](media/mixed-mode-debugging-symbols-installer35.png)

En Python 3.4.x y versiones anteriores, los símbolos están disponibles como archivos .zip descargables. Después de descargar los archivos, extráigalos en una carpeta y siga las instrucciones de la sección anterior para registrarlos en PTVS.

| Versión de Python | Descargas | 
| --- | --- | 
| 3.4.4 | [32 bits](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32 bits](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32 bits](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32 bits](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32 bits](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32 bits](http://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64 bits](http://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32 bits](http://python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64 bits](http://python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32 bits](http://python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64 bits](http://python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32 bits](http://python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64 bits](http://python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32 bits](http://python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64 bits](http://python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32 bits](http://python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64 bits](http://python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.11 | [32 bits](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32 bits](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32 bits](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32 bits](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32 bits](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32 bits](http://python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64 bits](http://python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32 bits](http://python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64 bits](http://python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32 bits](http://python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64 bits](http://python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32 bits](http://python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64 bits](http://python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32 bits](http://python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64 bits](http://python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32 bits](http://python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64 bits](http://python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |


## <a name="enthought-canopy"></a>Enthought Canopy

Enthought Canopy ofrece símbolos para sus archivos binarios, a partir de la versión 1.2. Se instalan automáticamente junto con la distribución, pero tendrá que agregar manualmente la carpeta que los contiene en la ruta de acceso a los símbolos, como se ha descrito anteriormente. Si se trata de una instalación por usuario típica de Canopy, los símbolos se encuentran en `%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts` para la versión de 64 bits y en `%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts` para la versión de 32 bits.

Enthought Canopy 1.1 y las versiones anteriores y Enthought Python Distribution (EPD) no proporcionan símbolos para el intérprete y, por tanto, no son compatibles con la depuración en modo mixto.
