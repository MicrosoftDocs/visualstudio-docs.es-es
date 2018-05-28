---
title: Establecimiento de marcadores de código en Visual Studio
ms.date: 02/23/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.BookmarkWindow
ms.assetid: a752ed5f-5cf9-4bf2-865a-2131ca600ed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e0154a9d410e7bbe60913b757f216225239704b
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="set-bookmarks-in-code"></a>Establecimiento de marcadores de código en Visual Studio

Se pueden usar marcadores para marcar líneas en el código de forma que se pueda volver rápidamente a una ubicación concreta o moverse hacia delante o hacia atrás entre ubicaciones. Los comandos y los iconos de los marcadores están disponibles en dos lugares: en la **ventana Marcador** (**Ver** > **Ventana Marcador**) y en la barra de herramientas del editor de texto.

![Barra de herramientas de marcadores](media/bookmark-toolbar.png)

![Ventana Marcador](media/bookmark-window.png)

## <a name="manage-bookmarks"></a>Administración de marcadores

Para agregar un marcador, coloque el cursor en la línea que desea marcar. Haga clic en el botón **Alternar marcador**, o bien presione **Ctrl**+**K**, **Ctrl**+**K**. De esta forma, se agrega el marcador. Si hace clic en el botón **Alternar marcador** (o si presiona **Ctrl**+**K**, **Ctrl**+**K**) de nuevo, se quita el marcador.

Para saber de un vistazo para qué es un marcador específico, puede cambiarle el nombre en la **ventana Marcador** desde el menú contextual. Puede eliminar los marcadores si hace clic en el botón **Eliminar** en la ventana Marcador.

> [!IMPORTANT]
> El marcador se establece en el número de línea, no en el código. Si modifica el código, el marcador se mantiene en el número de línea y no se mueve con el código.

Puede navegar entre los marcadores mediante los botones **Marcador siguiente** y **Marcador anterior** de la ventana Marcador.

Puede organizar los marcadores en carpetas virtuales si hace clic en **Nueva carpeta** en la ventana Marcador y, después, arrastra los marcadores seleccionados a la carpeta nueva.

Puede desactivar los marcadores (sin quitarlos) si hace clic en el botón **Deshabilitar todos los marcadores** en la ventana Marcador. Puede volver a habilitarlos haciendo clic en el mismo botón (que ahora se denominará **Habilitar todos los marcadores**).

## <a name="see-also"></a>Vea también

- [Características del editor de código](../ide/writing-code-in-the-code-and-text-editor.md)