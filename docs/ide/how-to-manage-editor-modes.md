---
title: Pantalla completa y modo de espacio virtual
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f2bf05eaaa5a61f7614b5d35ac6f8467ad6089a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820444"
---
# <a name="how-to-manage-editor-modes"></a>Procedimiento Administrar los modos del editor

Puede mostrar el editor de código de Visual Studio en varios modos de visualización.

> [!NOTE]
> Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los descritos en este artículo, en función de los valores de configuración o de edición activos. Para cambiar la configuración, por ejemplo, **General** o **Visual C++**, elija **Herramientas** > **Importar y exportar configuraciones** y, después, **Restablecer todas las configuraciones**.

## <a name="enable-full-screen-mode"></a>Habilitar el modo de pantalla completa

Puede decidir ocultar todas las ventanas de herramientas y ver solo las ventanas de documento habilitando el modo **Pantalla completa**.

-   Presione **Alt**+**Mayús**+**Entrar** para entrar o salir del modo **Pantalla completa**.

     O bien

-   Ejecute el comando `View.Fullscreen` en la ventana **Comandos**.

## <a name="enable-virtual-space-mode"></a>Habilitar el modo de espacio virtual

En el modo de **espacio virtual**, los espacios se insertan al final de cada línea de código. Seleccione esta opción para colocar los comentarios en una posición coherente al lado del código.

1.  Seleccione **Opciones** en el menú **Herramientas**.

2.  Expanda la carpeta **Editor de texto** y pulse **Todos los lenguajes** para establecer esta opción globalmente, o pulse una carpeta de lenguaje específica. Por ejemplo, para activar los números de línea solo en Visual Basic, elija el nodo **Básico** > **Editor de texto**.

3.  Seleccione las opciones **General** y en **Configuración**, seleccione **Habilitar espacio virtual**.

    > [!NOTE]
    > **Espacio virtual** está habilitado en el modo **Selección de columnas**. Cuando el modo **Espacio virtual** no está habilitado, el punto de inserción se mueve desde el final de una línea directamente al primer carácter de la siguiente.

## <a name="see-also"></a>Vea también

- [Personalizar el editor](../ide/customizing-the-editor.md)
- [Personalizar los diseños de ventana de Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)
- [Fuentes y colores, Entorno, Opciones (Cuadro de diálogo)](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)