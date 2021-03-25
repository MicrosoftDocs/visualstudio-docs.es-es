---
title: Escribiendo en el almacén de configuración de usuario | Microsoft Docs
description: Para obtener información sobre cómo agregar el Bloc de notas a Visual Studio como una herramienta externa, lea y escriba en el almacén de configuración de usuario mediante este tutorial.
ms.custom: SEO-VS-2020
ms.date: 05/23/2019
ms.topic: how-to
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ff3fa6f061f894abce17d2e6c58bfb791740a90
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061776"
---
# <a name="writing-to-the-user-settings-store"></a>Escritura en el almacén de configuración de usuario
La configuración de usuario se pueden escribir como las del cuadro de diálogo **herramientas/opciones** , las ventanas de propiedades y otros cuadros de diálogo. Las extensiones de Visual Studio pueden usarlas para almacenar pequeñas cantidades de datos. En este tutorial se muestra cómo agregar el Bloc de notas a Visual Studio como una herramienta externa mediante la lectura y la escritura en el almacén de configuración de usuario.

## <a name="writing-to-the-user-settings-store"></a>Escritura en el almacén de configuración de usuario

1. Cree un proyecto VSIX denominado UserSettingsStoreExtension y, a continuación, agregue un comando personalizado denominado UserSettingsStoreCommand. Para obtener más información sobre cómo crear un comando personalizado, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md) .

2. En UserSettingsStoreCommand. CS, agregue las siguientes directivas Using:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. En MenuItemCallback, elimine el cuerpo del método y obtenga el almacén de configuración de usuario, como se indica a continuación:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Ahora, averigüe si el Bloc de notas ya está configurado como una herramienta externa. Debe recorrer en iteración todas las herramientas externas para determinar si el valor de ToolCmd es "Notepad", como se indica a continuación:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already an External Tool.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }
    }

    ```

5. Si el Bloc de notas no se ha establecido como una herramienta externa, establézcalo de la siguiente manera:

    ```vb
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already installed.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }

        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";
         if (!hasNotepad)
        {
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);

            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);
        }
    }
    ```

6. Prueba del código Recuerde que agrega el Bloc de notas como una herramienta externa, por lo que debe revertir el registro antes de ejecutarlo una segunda vez.

7. Compile el código e inicie la depuración.

8. En el menú **herramientas** , haga clic en **invocar UserSettingsStoreCommand**. Esto agregará el Bloc de notas al menú **herramientas** .

9. Ahora debería ver el Bloc de notas en el menú Herramientas/Opciones y, al hacer clic en **Bloc** de notas, debe aparecer una instancia del Bloc de notas.
