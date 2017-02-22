---
title: "Utilizar el almac&#233;n de configuraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Almacén de configuración, uso"
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# Utilizar el almac&#233;n de configuraci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Hay dos tipos de almacenes de configuración:  
  
-   Opciones de configuración, que es la configuración de Visual Studio y VSPackage de sólo lectura. Visual Studio combina los valores de todos los archivos .pkgdef conocido en este almacén.  
  
-   Configuración de usuario, que es la configuración grabable, como los que se muestran en las páginas de la **opciones** cuadro de diálogo páginas de propiedades y algunos otros cuadros de diálogo. Extensiones de Visual Studio pueden utilizar para el almacenamiento local de pequeñas cantidades de datos.  
  
 Este tutorial muestra cómo leer datos desde el almacén de configuración de la configuración. Consulte [Escribir en el almacén de configuración de usuario](../extensibility/writing-to-the-user-settings-store.md) para obtener una explicación de cómo escribir en el almacén de configuración de usuario.  
  
## Crear el proyecto de ejemplo  
 Esta sección muestra cómo crear un proyecto de extensión simple con un comando de menú para la demostración.  
  
1.  Todas las extensiones de Visual Studio se inicia con un proyecto de implementación de VSIX que contiene los activos de la extensión. Crear un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto VSIX denominado `SettingsStoreExtension`. Puede encontrar la plantilla de proyecto VSIX en la **nuevo proyecto** en el cuadro de diálogo **Visual C\# \/ extensibilidad**.  
  
2.  Ahora agregue una plantilla de elemento de comando personalizado denominada **SettingsStoreCommand**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C\# \/ extensibilidad** y seleccione **comando personalizado**. En el **nombre** campo en la parte inferior de la ventana, el nombre del archivo de comandos **SettingsStoreCommand.cs**. Para obtener más información sobre cómo crear un comando personalizado, vea [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## Utilizando el almacén de configuración de la configuración  
 Esta sección muestra cómo detectar y mostrar valores de configuración.  
  
1.  En el archivo SettingsStorageCommand.cs, agregue las siguientes instrucciones using:  
  
    ```  
    using System.Collections.Generic; using Microsoft.VisualStudio.Settings; using Microsoft.VisualStudio.Shell.Settings; using System.Windows.Forms;  
    ```  
  
2.  En `MenuItemCallback`, quite el cuerpo del método y agregue estas líneas obtener el almacén de configuración de la configuración:  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     El <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> es una clase auxiliar administrada sobre el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> service.  
  
3.  Ahora, averigüe si se instalan herramientas de Windows Phone. El código debe tener este aspecto:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools"); string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled; MessageBox.Show(message); }  
    ```  
  
4.  Probar el código. Compile la solución y comience la depuración.  
  
5.  En la instancia experimental, en la **herramientas** menú, haga clic en **invocar SettingsStoreCommand**.  
  
     Verá el siguiente cuadro de mensaje **Herramientas para desarrolladores de Microsoft Windows Phone:**  seguido **True** o **False**.  
  
 Visual Studio mantiene el almacén de configuración en el registro del sistema.  
  
#### Usar un editor del registro para comprobar la configuración  
  
1.  Abra Regedit.exe.  
  
2.  Vaya a HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0Exp\_Config\\InstalledProducts\\.  
  
    > [!NOTE]
    >  Asegúrese de que se encuentre en la clave que contiene \\14.0Exp\_Config\\ y no \\14.0\_Config\\. Cuando se ejecuta la instancia experimental de Visual Studio, opciones de configuración están en el subárbol del registro "14.0Exp\_Config".  
  
3.  Expanda el nodo \\Installed Products\\. Si el mensaje en los pasos anteriores es **Microsoft Windows Phone Developer Tools instalado: True**, \\Installed Products\\ debe contener un nodo de herramientas para desarrolladores de Microsoft Windows Phone. Si el mensaje es **Microsoft Windows Phone Developer Tools instalado: False**, \\Installed Products\\ no debe contener un nodo de herramientas para desarrolladores de Microsoft Windows Phone.