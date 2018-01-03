---
title: "Identificar y personalizar métodos abreviados de teclado en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.ToolsOptionsPages.Environment.Keyboard
helpviewer_keywords:
- keyboard shortcuts [Visual Studio], customizing
- importing shortcut keys [Visual Studio]
- shortcut key combinations [Visual Studio]
- commands [Visual Studio], shortcut keys
- custom shortcut keys [Visual Studio]
- customizing keyboard shortcuts [Visual Studio]
- exporting shortcut keys [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7258a1ba99764fa7af7ce73874f447db99b8b168
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="identifying-and-customizing-keyboard-shortcuts-in-visual-studio"></a>Identificar y personalizar métodos abreviados de teclado en Visual Studio

Puede identificar los métodos abreviados de teclado de los comandos de Visual Studio, personalizarlos y exportarlos para que los usen otras personas. Muchos métodos abreviados invocan siempre los mismos comandos, pero el comportamiento de un método abreviado puede variar en función de las condiciones siguientes:

- Las opciones predeterminadas del entorno que eligió la primera vez que ejecutó Visual Studio (por ejemplo, Desarrollo general o Visual C#)

- Si ha personalizado el comportamiento del método abreviado.

- El contexto en el que se encuentra al elegir el método abreviado. Por ejemplo, el método abreviado F2 invoca el comando Edit.EditCell si utiliza el Diseñador de configuración y el comando File.Rename si utiliza Team Explorer.

Independientemente de la configuración, la personalización y el contexto, siempre puede buscar y cambiar un método abreviado de teclado en el cuadro de diálogo **Opciones**. También puede buscar los métodos abreviados de teclado predeterminados para varias decenas de comandos en [Métodos abreviados de teclado para comandos de uso frecuente](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md), y puede encontrar una lista completa de todos los métodos abreviados predeterminados (basados en la configuración general de desarrollo) en [Métodos abreviados de teclado predeterminados](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Si un método abreviado se asigna a un comando en el contexto Global y no a otros contextos, el método abreviado invocará siempre ese comando. Pero se puede asignar un método abreviado a un comando en el contexto Global y otro comando distinto en un contexto específico. Si utiliza ese método abreviado en el contexto específico, el método abreviado invoca el comando del contexto concreto, no el del contexto Global.

> [!NOTE]
> La configuración y edición de Visual Studio podría cambiar los nombres y las ubicaciones de los comandos de menú y las opciones que aparecen en los cuadros de diálogo. Este tema se basa en la **configuración general de desarrollo**.

## <a name="identifying-a-keyboard-shortcut"></a>Identificar un método abreviado de teclado

1. En la barra de menús, elija **Herramientas**, **Opciones**.

2. Expanda **Entorno** y elija **Teclado**.

   ![Mostrar métodos abreviados de teclado en el cuadro de diálogo Opciones](../ide/media/optionskeyboard.png "OptionsKeyboard")

3. En el cuadro **Mostrar los comandos que contengan**, escriba todo o parte del nombre del comando sin espacios.

   Por ejemplo, puede buscar comandos de `solutionexplorer`.

4. En la lista, elija el comando correcto.

    Por ejemplo, puede elegir **View.SolutionExplorer**.

5. Si el comando tiene un método abreviado de teclado, aparece en la lista **Métodos abreviados para el comando seleccionado**.

   ![Ver un método abreviado de un comando específico](../ide/media/viewshortcut.png "ViewShortcut")

## <a name="customizing-a-keyboard-shortcut"></a>Personalizar un método abreviado de teclado

1. En la barra de menús, elija **Herramientas**, **Opciones**.

2. Expanda la carpeta **Entorno** y elija **Teclado**.

3. Opcional: filtre la lista de comandos escribiendo el nombre del comando parcial o totalmente y sin espacios en el cuadro **Mostrar los comandos que contengan**.

4. En la lista, elija el comando al que desea asignar un método abreviado de teclado.

En la lista **Usar nuevo método abreviado**, elija el área de características en la que quiere usar el método abreviado.

    For example, you can choose **Global** if you want the shortcut to work in all contexts. You can use any shortcut that isn't mapped (as Global) in another editor. Otherwise, the editor overrides the shortcut.

    > [!NOTE]
    > You can't assign the following keys as part of a keyboard shortcut in **Global**: Print Scrn/Sys Rq, Scroll Lock, Pause/Break, Tab, Caps Lock, Insert, Home, End, Page Up, Page Down, the Windows logo key, the Application key, any of the Arrow keys, or Enter; Num Lock, Delete, or Clear on the numeric keypad; the Ctrl+Alt+Delete key combination.

6. En el cuadro **Presionar teclas de método abreviado**, especifique el método abreviado que quiere usar.

    > [!NOTE]
    > Puede crear un método abreviado que combine una letra con la tecla Alt, Ctrl o ambas. También puede crear un método abreviado que combine la tecla Mayús y una letra con la tecla Alt, Ctrl o ambas.

     Si un método abreviado ya está asignado a otro comando, aparece en el cuadro **El método abreviado lo utiliza actualmente**. En ese caso, elija la tecla Retroceso para eliminar ese método abreviado antes de probar con otro.

    ![Especificar un método abreviado diferente para un comando](../ide/media/reassignshortcut.png "ReassignShortcut")

7. Elija el botón **Asignar**.

    > [!NOTE]
    > Si especifica un método abreviado diferente para un comando, elija el botón **Asignar** y luego el botón **Cancelar**. El cuadro de diálogo se cierra, pero el cambio no se revierte.

## <a name="sharing-custom-keyboard-shortcuts"></a>Compartir métodos abreviados de teclado

Puede compartir los métodos abreviados de teclado personalizados exportándolos a un archivo y proporcionando el archivo a otras personas para que puedan importar los datos.

### <a name="to-export-only-keyboard-shortcuts"></a>Para exportar solo métodos abreviados de teclado

1. En la barra de menús, elija **Herramientas**, **Importar y exportar configuraciones**.

2. Seleccione **Exportar la configuración de entorno seleccionada** y elija el botón **Siguiente**.

3. En **¿Qué configuración desea exportar?**, desactive la casilla **Todas las configuraciones**, expanda **Opciones** y, después, expanda **Entorno**.

4. Active la casilla **Teclado** y elija el botón **Siguiente**.

    ![Exportar solo los métodos abreviados de teclado personalizados](../ide/media/exportshortcuts.png "ExportShortcuts")

5. En los cuadros **¿Qué nombre desea dar al archivo de configuración?** y **Almacenar mi archivo de configuración en este directorio**, deje los valores predeterminados o especifique otros diferentes y elija el botón **Finalizar**.

    Los métodos abreviados se guardan de forma predeterminada en un archivo en la carpeta %USERPROFILE%\Documents\Visual Studio 2017\Settings. El nombre del archivo indica la fecha en la que exportó la configuración y la extensión es .vssettings.

### <a name="to-import-only-keyboard-shortcuts"></a>Para importar solo métodos abreviados de teclado

1. En la barra de menús, elija **Herramientas**, **Importar y exportar configuraciones**.

2. Elija el botón de opción **Importar la configuración de entorno seleccionada** y después el botón **Siguiente**.

3. Elija el botón de opción **No, solo importar la nueva configuración, reemplazando la configuración actual** y elija el botón **Siguiente**.

4. En **Mi configuración**, elija el archivo que contiene los métodos abreviados que quiere importar o elija el botón **Examinar** para buscar el archivo correcto.

5. Elija el botón **Siguiente**.

6.  En **¿Qué configuración desea importar?**, desactive la casilla **Todas las configuraciones**, expanda **Opciones** y, después, expanda **Entorno**.

7. Active la casilla **Teclado** y elija el botón **Finalizar**.

    ![Importar solo los métodos abreviados de teclado personalizados](../ide/media/importshortcuts.png "ImportShortcuts")

## <a name="see-also"></a>Vea también

[Características de accesibilidad de Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)