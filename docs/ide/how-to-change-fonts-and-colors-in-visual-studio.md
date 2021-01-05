---
title: Cambio de temas, fuentes, texto y contraste para mejorar la accesibilidad
description: Aprenda a cambiar los temas de color, los colores de fuentes, los tamaños de texto y los colores de contraste adicional de Visual Studio para facilitar el uso y permitir una mejor accesibilidad.
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
helpviewer_keywords:
- Visual Studio, color themes
- color themes, Visual Studio
ms.assetid: 60d91ba1-244b-4c43-847f-60b744f1352a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c52be25c007a16d7e6221663c434767c02d8d50
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/18/2020
ms.locfileid: "97683900"
---
# <a name="how-to-change-fonts-colors-and-themes-in-visual-studio"></a>Procedimiento Cambio de fuentes, colores y temas en Visual Studio

Puede cambiar las fuentes y los colores en Visual Studio de muchas maneras. Por ejemplo, puede cambiar el tema azul predeterminado a un tema oscuro (conocido también como "modo oscuro"). También puede seleccionar un tema de contraste adicional si es lo mejor para sus necesidades. También puede cambiar la fuente y el tamaño de texto predeterminados tanto en el IDE como en el editor de código.

## <a name="change-the-color-theme"></a>Cambio del tema de color

Aquí se muestra cómo cambiar el tema de color del marco del IDE y las ventanas de herramientas en Visual Studio.

1. En la barra de menús, seleccione **Herramientas** > **Opciones**.

1. En la lista de opciones, elija **Entorno** > **General**.

1. En la lista **Tema de color**, elija el tema **Azul** predeterminado, el tema **Claro**, el tema **Oscuro** o el tema **Azul (contraste adicional)** .

   ![Captura de pantalla del cuadro de diálogo Opciones para cambiar el tema de color](media/fonts-colors-theme.png "Captura de pantalla del cuadro de diálogo Opciones que puede usar para cambiar el tema de color")

    > [!NOTE]
    > Al cambiar un tema de color, el texto del IDE vuelve a ser el predeterminado o las fuentes y tamaños previamente personalizados para ese tema.

    :::moniker range="vs-2017"

    > [!TIP]
    > Para crear y editar sus propios temas de Visual Studio, instale el [editor de temas de color para Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor).

    :::moniker-end

    :::moniker range="vs-2019"

    > [!TIP]
    > Para crear y editar sus propios temas de Visual Studio, instale el [diseñador de temas de color de Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner).

    :::moniker-end

## <a name="change-fonts-and-text-size"></a>Cambio de las fuentes y del tamaño del texto

Puede cambiar la fuente y el tamaño del texto tanto del marco como de las ventanas de herramientas del IDE al completo, o solo de ciertas ventanas o elementos de texto. También puede cambiar la fuente y el tamaño del texto en el editor.

### <a name="to-change-the-font-and-text-size-in-the-ide"></a>Para cambiar el tamaño y la fuente del texto del IDE

1. En la barra de menús, seleccione **Herramientas** > **Opciones**.

1. En la lista de opciones, elija **Entorno** > **Fuentes y colores**.

1. En la lista **Mostrar configuración para**, elija **Entorno**.

   ![Captura de pantalla del cuadro de diálogo Opciones para cambiar fuentes y colores del IDE](media/fonts-colors-environment.png "Captura de pantalla del cuadro de diálogo Opciones para cambiar fuentes y colores del IDE")

    > [!NOTE]
    > Si solo quiere cambiar la fuente de las ventanas de herramientas, en la lista **Mostrar configuración para**, elija **Todas las ventanas de herramientas de texto**.

1. Modifique las opciones **Fuente** y **Tamaño** para cambiar la fuente y el tamaño del texto del IDE.

1. Seleccione el elemento apropiado en **Mostrar elementos** y, después, modifique las opciones **Primer plano del elemento** y **Fondo del elemento**.

### <a name="to-change-the-font-and-text-size-in-the-editor"></a>Para cambiar la fuente y el tamaño del texto en el editor

1. En la barra de menús, seleccione **Herramientas** > **Opciones**.

1. En la lista de opciones, elija **Entorno** > **Fuentes y colores**.

1. En la lista **Mostrar configuración para**, seleccione **Editor de texto**.

   ![Captura de pantalla del cuadro de diálogo Opciones para cambiar fuentes y colores en el editor](media/fonts-colors-text-editor.png "Captura de pantalla del cuadro de diálogo Opciones para cambiar las fuentes y los colores en el editor")

1. Modifique las opciones **Fuente** y **Tamaño** para cambiar la fuente y el tamaño del texto del editor.

1. Seleccione el elemento apropiado en **Mostrar elementos** y, después, modifique las opciones **Primer plano del elemento** y **Fondo del elemento**.

Para más información, consulte la página [Cambiar las fuentes y los colores del editor de Visual Studio](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="accessibility-options"></a>Opciones de accesibilidad

Si tiene problemas de visión, hay opciones de tema de color. Puede usar una opción de contraste alto para *todas* las aplicaciones y la UI en un equipo, o una opción de contraste adicional solo para Visual Studio.

### <a name="use-windows-high-contrast"></a>Uso del contraste alto de Windows

Use cualquiera de los procedimientos siguientes para alternar la opción de contraste alto de Windows:

- En Windows o en cualquier aplicación de Microsoft, presione las teclas **Alt izquierda**+**Mayús izquierda**+**Impr Pant**.

- En Windows, elija **Inicio** > **Configuración** > **Accesibilidad** > **Contraste alto**.

    > [!WARNING]
    > La configuración de contraste alto de Windows afecta a todas las aplicaciones y a la UI del equipo.

### <a name="use-visual-studio-extra-contrast"></a>Uso del contraste adicional de Visual Studio

Use los procedimientos siguientes para alternar la opción de contraste adicional de Visual Studio:

1. En la barra de menús de Visual Studio, elija **Herramientas** > **Opciones** y luego, en la lista de opciones, elija **Entorno** > **General**.

1. En la lista desplegable **Tema de color**, elija el tema **Azul (contraste adicional)** y luego elija **Aceptar**.

Para más información sobre otras opciones de accesibilidad de Visual Studio disponibles, vea la página [Características de accesibilidad de Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md).

> [!TIP]
> Si hay una opción de accesibilidad para los colores o las fuentes que cree que puede ser útil pero no está disponible actualmente en Visual Studio, háganoslo saber seleccionando **Sugerir una característica** en [Visual Studio Developer Community](https://aka.ms/feedback/suggest?space=8). Para más información sobre este foro y cómo funciona, vea la página [Sugerir una característica](../ide/suggest-a-feature.md).

## <a name="next-steps"></a>Pasos siguientes

Para obtener más detalles sobre todos los elementos de la interfaz de usuario (UI) para los que puede cambiar las combinaciones de fuentes y colores, vea la página [Fuentes y colores, Entorno, Opciones (cuadro de diálogo)](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).

## <a name="see-also"></a>Vea también

- [Procedimiento Cambiar las fuentes y los colores del editor de Visual Studio](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)
- [Características del editor de código de Visual Studio](../ide/writing-code-in-the-code-and-text-editor.md)
- [Personalización del IDE y el editor de Visual Studio](../ide/quickstart-personalize-the-ide.md)
