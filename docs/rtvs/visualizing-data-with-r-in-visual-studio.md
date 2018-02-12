---
title: "Visualización de datos con Herramientas de R para Visual Studio | Microsoft Docs"
description: "Describe cómo trazar datos desde programas de R en Visual Studio con ventanas de trazados."
ms.custom: 
ms.date: 06/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 04b8cec39a21f3874d86226347469e8cf664eea7
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2018
---
# <a name="creating-visual-data-plots-with-r"></a>Crear trazados de datos visuales con R

El trazado es una parte fundamental del flujo de trabajo de un científico de datos. En las herramientas de R para Visual Studio (RTVS), toda la actividad de trazado se centra en una o más ventanas de trazado, que están diseñadas para mejorar la productividad de esta actividad principal.

![Imagen prominente del trazado](media/plotting-hero-image.png)

En el siguiente vídeo (2m 02s) se proporciona un breve paseo introductorio por el trazado en RTVS:

<iframe width="560" height="315" src="https://www.youtube.com/embed/ZTbKmz5RSgY" frameborder="0" allowfullscreen></iframe>

## <a name="the-plot-window"></a>La ventana de trazado

Una ventana de trazado contiene una serie de trazados, donde cada uno de ellos se genera mediante un comando `plot`. Por ejemplo, al usar `plot(1:100)` se crea una nueva ventana de trazado si ninguna está disponible:

![Trazado lineal de 1 a 100](media/plotting-1-to-100.png)

Técnicamente hablando, los comandos `plot` de R representan su resultado en un dispositivo de gráficos de R; una ventana de trazado representa el contenido de un dispositivo de gráficos de R, que es el motivo por el que a cada ventana de trazado se le proporciona un número de dispositivo.

Las ventanas de trazado son independientes de los proyectos de Visual Studio, y permanecen abiertas cuando carga y cierra proyectos.

Al generar un trazado se usa la ventana de trazado "activa", guardando cualquier trazado anterior en el historial de trazados (vea [Historial de trazados](#plot-history)). Por ejemplo, escriba `plot(100:1)` y el primer trazado se reemplaza por una línea hacia abajo.

Como todas las demás ventanas de Visual Studio. La ventana de trazado admite diseños personalizados (vea [Personalizar los diseños de ventana de Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)). Las ventanas de trazado pueden acoplarse en diferentes ubicaciones dentro del marco de Visual Studio, cambiar su tamaño dentro de ese marco o salirse de ese marco por completo para cambiar su tamaño de manera independiente. 

Al cambiar el tamaño de una ventana de trazado siempre se vuelve a representar el trazado para proporcionar la mejor calidad de imagen. Normalmente quiere cambiar el tamaño de un trazado antes de exportar el trazado a un archivo o al Portapapeles con los comandos descritos en la sección siguiente.

## <a name="plot-window-commands"></a>Comandos de la ventana de trazado

La barra de herramientas de la ventana de trazado incluye comandos aplicables, la mayoría de los cuales también están disponibles en el menú **Herramientas de R > Trazados**.

| Botón | Comando | Description | 
| --- | --- | --- |
| ![Botón Nueva ventana de trazado](media/plotting-toolbar-01-new-plot-window.png) | Nueva ventana de trazado | Crea una ventana de trazado independiente con su propio historial. Vea [Varias ventanas de trazado](#multiple-plot-windows). |
| ![Botón Activar ventana de trazado](media/plotting-toolbar-02-activate-plot-window.png) | Activar ventana de trazado | Establece la ventana de trazado actual como la ventana activa, de manera que los comandos `plot` posteriores se representen en esa ventana. Vea [Varias ventanas de trazado](#multiple-plot-windows). Vea [Varias ventanas de trazado](#multiple-plot-windows). |
| ![Botón Ventana del historial de trazado](media/plotting-toolbar-03-plot-history.png) | Ventana del historial de trazado | Abre una ventana con todos los trazados del historial que se muestran como miniaturas. Vea [Historial de trazados](#plot-history). |
| ![Botones del historial de trazados](media/plotting-toolbar-04-plot-history-arrows.png) | Trazado siguiente o anterior |  Se dirige al trazado siguiente o anterior del historial. También puede ir al historial presionando Ctrl+Alt+F11 (anterior) y Ctrl+Alt+F12 (siguiente). Vea [Historial de trazados](#plot-history). |
| ![Botón Guardar como imagen](media/plotting-toolbar-05-save-as-image.png)| Guardar como imagen | Solicita un nombre de archivo y guarda el trazado actual (el contenido de la ventana, en el tamaño de la ventana) en un archivo de imagen. Los formatos disponibles son `.png`, `.jpg`, `.bmp` y `.tif`. |
| ![Botón Guardar como PDF](media/plotting-toolbar-06-save-as-pdf.png)| Guardar como PDF | Guarda el trazado actual en un archivo PDF con el tamaño de ventana actual. El trazado se volverá a representar si se escala el PDF. |
| ![Botón Copiar como mapa de bits](media/plotting-toolbar-07-copy-as-bitmap.png)| Copiar como mapa de bits | Copia el trazado al Portapapeles como un mapa de bits de trama, con el tamaño de ventana actual. | 
| ![Botón Copiar como metarchivo](media/plotting-toolbar-08-copy-as-metafile.png)| Copiar como metarchivo | Copia el trazado al Portapapeles como un [metarchivo de Windows](https://en.wikipedia.org/wiki/Windows_Metafile) (Wikipedia). | 
| ![Botón Quitar trazado](media/plotting-toolbar-09-remove-plot.png)| Quitar trazado | Quita el trazado actual del historial. |
| ![Botón Borrar todos los trazados](media/plotting-toolbar-10-clear-all-plots.png) | Borrar todos los trazados | Quita todos los trazados del historial (solicita confirmación). |

## <a name="multiple-plot-windows"></a>Varias ventanas de trazado

Como los científicos de datos trabajan a menudo con muchos trazados de diferentes conjuntos de datos, RTVS le permite crear todas las ventanas de trazados independientes que quiera. Después, puede organizar esas ventanas como desee dentro del marco de Visual Studio o fuera de ese marco. (Vea [Personalizar los diseños de ventana de Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) para obtener información general sobre el acoplamiento y el cambio de tamaño de las ventanas).

Cree una nueva ventana de trazado con el botón de la barra de herramientas o **Herramientas de R > Trazados > Nueva ventana de trazado**. La nueva ventana de trazado se convierte en la ventana *activa*, que es el lugar donde se representan los trazados nuevos. Para cambiar la ventana activa, cámbiela y seleccione el botón de la barra de herramientas Activar ventana de trazados o **Herramientas de R > Trazados > Activar ventana de trazados**.

Además, los trazados son objetos independientes, lo que significa que puede copiar o moverlos entre ventanas de trazado con la opción de arrastrar y soltar del mouse o con los comandos **Copiar**, **Cortar** y **Pegar** en el contexto del botón derecho y con los menús **Editar**.

El comportamiento predeterminado de arrastrar y soltar es copiar; para mover, arrastre y suelte mientras mantiene presionada la tecla Mayús.

## <a name="plot-history"></a>Historial de trazados

Los comandos de trazado se conservan en un historial de trazados para cada ventana, garantizando que todo el trazado de una sesión se mantiene. Para ir al historial, use los botones de flecha en la barra de herramientas de la ventana de trazado o presione Ctrl+Alt+F11 y Ctrl+Alt+F12. También puede quitar los trazados únicos o borrarlos todos de la ventana de nuevo con los botones de la barra de herramientas o con los comandos de menú **Herramientas de R > Trazados**.

Para ver la colección completa de trazados, abra la ventana del historial de trazados con el botón de la barra de herramientas o **Herramientas de R > Trazados > Ventana del historial de trazados**.
El historial le proporciona una lista de miniaturas para los trazados que se han mostrado en esa ventana, agrupados por diferentes ventanas de trazado (o dispositivos). Con los botones de zoom de la barra de herramientas se cambia el tamaño de las miniaturas.

![Ventana del historial de trazado](media/plotting-plot-history-window.png)

Para abrir un trazado en su ventana asociada, haga doble clic en ese trazado, selecciónelo y, después, seleccione el botón de la barra de herramientas **Mostrar trazado**, o haga doble clic con el botón derecho y seleccione **Mostrar trazado**. También puede seleccionar un trazado individual y copiar, cortar o eliminar desde el menú contextual o desde los menús **Editar**.

La duración de su historial de trazado en todas las ventanas está vinculado a la duración de su sesión de R interactiva. Si restablece la sesión de R, o sale y reinicia Visual Studio, su historial de trazados se restablece.

## <a name="programmatically-manipulating-plot-windows"></a>Manipular ventanas de trazado mediante programación

Puede manipular ventanas de trazado mediante programación desde el código de R, con números de dispositivo para identificar las ventanas de trazado específicas. 

- `dev.list()`: mostrar todos los dispositivos de gráficos en la sesión actual de R.
- `dev.new()`: crear un nuevo dispositivo de gráficos (una nueva ventana de trazado).
- `dev.set(<device number>)`: establecer el dispositivo de gráficos activo.
- `dev.off()`: eliminar el dispositivo activo.
