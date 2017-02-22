---
title: "Escribir en el almac&#233;n de configuraci&#243;n de usuario | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
---
# Escribir en el almac&#233;n de configuraci&#243;n de usuario
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Configuración de usuario es grabable como las de la **Herramientas \/ opciones** cuadro de diálogo, ventanas de propiedades y algunos otros cuadros de diálogo. Extensiones de Visual Studio pueden utilizar para almacenar pequeñas cantidades de datos. Este tutorial muestra cómo agregar el Bloc de notas para Visual Studio como una herramienta externa al leer y escribir en el almacén de configuración de usuario.  
  
### Copia de seguridad de la configuración de usuario  
  
1.  Debe ser capaz de restablecer la configuración de herramientas externas, para que pueda depurar y repita el procedimiento. Para ello, debe guardar la configuración original para que se puedan restaurar según sea necesario.  
  
2.  Abra Regedit.exe.  
  
3.  Vaya a HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0Exp\\External Tools\\.  
  
    > [!NOTE]
    >  Asegúrese de que se encuentre en la clave que contiene \\14.0Exp\\ y no \\14.0\\. Cuando se ejecuta la instancia experimental de Visual Studio, la configuración de usuario está en el subárbol del registro "14.0Exp".  
  
4.  Haga clic en la subclave \\External Tools\\ y, a continuación, haga clic en **exportar**. Asegúrese de que **rama seleccionada** está seleccionada.  
  
5.  Guarde el archivo externo Tools.reg resultante.  
  
6.  Más adelante, cuando desea restablecer la configuración de herramientas externas, seleccione la clave del registro HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0Exp\\External Tools\\ y haga clic en **Eliminar** en el menú contextual.  
  
7.  Cuando el **Confirmar eliminación de clave** aparece el cuadro de diálogo, haga clic en **Sí**.  
  
8.  Haga clic en el archivo externo Tools.reg que guardó anteriormente, haga clic en **Abrir con**, y, a continuación, haga clic en **Editor del registro**.  
  
## Escribir en el almacén de configuración de usuario  
  
1.  Cree un proyecto VSIX denominado UserSettingsStoreExtension y, a continuación, agregue un comando personalizado denominado UserSettingsStoreCommand. Para obtener más información sobre cómo crear un comando personalizado, vea [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  En UserSettingsStoreCommand.cs, agregue las siguientes instrucciones using:  
  
    ```c#  
    using System.Collections.Generic; using Microsoft.VisualStudio.Settings; using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  En MenuItemCallback, elimine el cuerpo del método y obtener el usuario almacenan valores como sigue:  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings); }  
    ```  
  
4.  Ahora, averigüe si el Bloc de notas ya está configurada como una herramienta externa. Es necesario recorrer en iteración todas las herramientas externas para determinar si el valor de ToolCmd es "Notepad", como sigue:  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings); // Find out whether Notepad is already an External Tool. int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys"); bool hasNotepad = false; CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo; for (int i = 0; i < toolCount; i++) { if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0) { hasNotepad = true; break; } } }  
  
    ```  
  
5.  Si no se ha establecido el Bloc de notas como una herramienta externa, establecer como sigue:  
  
    ```vb  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings); // Find out whether Notepad is already installed. int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys"); bool hasNotepad = false; CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo; for (int i = 0; i < toolCount; i++) { if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0) { hasNotepad = true; break; } } string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad"; if (!hasNotepad) { userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad"); userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe"); userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, ""); userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)"); userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, ""); userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011); userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1); } }  
    ```  
  
6.  Probar el código. Recuerde que agrega el Bloc de notas como una herramienta externa, por lo que se debe revertir el registro antes de ejecutar una segunda vez.  
  
7.  Compilar el código e iniciar la depuración.  
  
8.  En el **herramientas** menú, haga clic en **invocar UserSettingsStoreCommand**. Esto agregará el Bloc de notas para la **herramientas** menú.  
  
9. Ahora debería ver el Bloc de notas en las herramientas \/ opciones de menú y haga clic en **el Bloc de notas** debe devolver una instancia del Bloc de notas.