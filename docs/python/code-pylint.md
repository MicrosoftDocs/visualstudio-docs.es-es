---
title: Uso de PyLint en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc668a4b-10ae-4199-90b8-c984456b6003
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
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: c8bfaf9f20e7fecb3633ca101170b0f3e686aa53
ms.lasthandoff: 04/10/2017

---

# <a name="using-pylint-to-check-python-code"></a>Uso de PyLint para comprobar el código de Python

[PyLint](https://www.pylint.org/), una herramienta ampliamente usada que busca errores en el código de Python y promueve patrones correctos de codificación en Python, se integra en proyectos de Visual Studio para Python.

Simplemente haga clic con el botón derecho en un proyecto de Python en el Explorador de soluciones y seleccione **Python > Run PyLint... (Ejecutar PyLint...)**:

![Comando PyLint en el menú contextual para proyectos de Python](media/code-pylint-command.png)

Mediante los comandos se le pide que instale PyLint en el entorno activo, si es necesario.

Aparecen errores y advertencias de PyLint en la ventana de lista de errores:

![Lista de errores de PyLint](media/code-pylint-error-list.png)

Haga doble clic en un error e irá directamente al código fuente que generó el problema.

> [!Tip]
> Consulte la [referencia de características de PyLint](https://pylint.readthedocs.io/en/latest/reference_guide/features.html) para obtener una lista detallada de todos los mensajes de salida de PyLint.

## <a name="setting-pylint-command-line-options"></a>Configuración de las opciones de línea de comandos de PyLint

En la sección de [opciones de línea de comandos](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) de la documentación de PyLint se describe cómo controlar el comportamiento de PyLint mediante un archivo de configuración `.pylintrc`. Este archivo se puede colocar en la raíz de un proyecto de Python en Visual Studio, o en alguna otra parte, según cuán extensamente se quiera aplicar esa configuración.

Por ejemplo, para suprimir las advertencias "falta docstring" que se muestran en la imagen anterior con un archivo `.pylintrc` en un proyecto, realice lo siguiente:

1. En la línea de comandos, vaya a la raíz del proyecto (donde encontrará su archivo `.pyproj`) y ejecute el siguiente comando para generar un archivo de configuración comentado:

   ```bash
   pylint --generate-rcfile > .pylintrc
   ```

1. En el Explorador de soluciones de Visual Studio, haga clic con el botón derecho en el proyecto, seleccione **Agregar > Elemento existente...**, vaya al nuevo archivo `.pylintrc`, selecciónelo y haga clic en **Agregar**.

1. Abra el archivo para editarlo; verá una diversas opciones de configuración con las que puede trabajar. Para deshabilitar una advertencia, busque la sección `[MESSAGES CONTROL]` y luego el valor `disable` debajo de ella. Verá una cadena larga de mensajes concretos, a la que se puede anexar cualquier advertencia que desee. En este ejemplo, anexe `,missing-docstring` (incluida la coma de delimitación).

1. Guarde el archivo `.pylintrc` y vuelva a ejecutar PyLint para ver que ahora las advertencias se han suprimido.
