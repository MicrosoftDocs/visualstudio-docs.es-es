---
title: Escribir en el Store de la configuración de usuario | Documentos de Microsoft
ms.date: 05/23/2019
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe8187fe11f4818433aed847a7bc67d4a889ad3a
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206885"
---
# <a name="writing-to-the-user-settings-store"></a>Escritura en el almacén de configuración de usuario
Configuración de usuario son valores grabables como las de la **herramientas / opciones** cuadro de diálogo, ventanas de propiedades y algunos otros cuadros de diálogo. Extensiones de Visual Studio pueden usarlas para almacenar pequeñas cantidades de datos. Este tutorial muestra cómo agregar el Bloc de notas para Visual Studio como una herramienta externa al leer y escribir en el almacén de configuración de usuario.

## <a name="writing-to-the-user-settings-store"></a>Escritura en el almacén de configuración de usuario

1. Cree un proyecto VSIX denominado UserSettingsStoreExtension y, a continuación, agregue un comando personalizado denominado UserSettingsStoreCommand. Para obtener más información sobre cómo crear un comando personalizado, consulte [creación de una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)

2. En UserSettingsStoreCommand.cs, agregue las siguientes instrucciones using:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. En MenuItemCallback, elimine el cuerpo del método y obtener el usuario del almacén de configuración, como se indica a continuación:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Ahora, averigüe si ya está establecido el Bloc de notas como una herramienta externa. Deberá recorrer en iteración todas las herramientas externas para determinar si la configuración de ToolCmd es "Notepad", como se indica a continuación:

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

5. Si no se ha establecido el Bloc de notas como una herramienta externa, establézcalo como sigue:

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

6. Probar el código. Recuerde que agrega el Bloc de notas como una herramienta externa, por lo que debe revertir el registro antes de ejecutarlo una segunda vez.

7. Compilar el código e iniciar la depuración.

8. En el **herramientas** menú, haga clic en **UserSettingsStoreCommand invocar**. Esto agregará el Bloc de notas para el **herramientas** menú.

9. Ahora debería ver el Bloc de notas en las herramientas / opciones de menú y haga clic en **el Bloc de notas** debería abrirse una instancia del Bloc de notas.