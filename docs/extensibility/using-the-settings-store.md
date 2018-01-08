---
title: "Uso del almacén de configuración | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ecb7cf4a40793116159bd2ff8292f0303e3cc46f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-settings-store"></a>Uso del almacén de configuración
Hay dos tipos de almacenes de configuración:  
  
-   Opciones de configuración, que es la configuración de Visual Studio y VSPackage de solo lectura. Visual Studio combina los valores de todos los archivos de .pkgdef conocidos en este almacén.  
  
-   Configuración de usuario, que es la configuración grabable, como los que se muestran en páginas en el **opciones** cuadro de diálogo, páginas de propiedades y algunos otros cuadros de diálogo. Extensiones de Visual Studio pueden utilizar para el almacenamiento local de pequeñas cantidades de datos.  
  
 Este tutorial muestra cómo leer datos desde el almacén de configuración de configuración. Vea [escriben en el almacén de configuración de usuario](../extensibility/writing-to-the-user-settings-store.md) para obtener una explicación de cómo se escriben en el almacén de configuración de usuario.  
  
## <a name="creating-the-example-project"></a>Crear el proyecto de ejemplo  
 Esta sección muestra cómo crear un proyecto de extensión simple con un comando de menú de demostración.  
  
1.  Cada extensión de Visual Studio se inicia con un proyecto de implementación de VSIX que contendrá los activos de la extensión. Crear un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto VSIX denominado `SettingsStoreExtension`. Puede encontrar la plantilla de proyecto VSIX en la **nuevo proyecto** en el cuadro de diálogo **Visual C# / extensibilidad**.  
  
2.  Ahora agregue una plantilla de elemento de comando personalizado denominada **SettingsStoreCommand**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C# / extensibilidad** y seleccione **comando personalizado**. En el **nombre** campo en la parte inferior de la ventana, cambie el nombre de archivo de comandos para **SettingsStoreCommand.cs**. Para obtener más información sobre cómo crear un comando personalizado, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>Uso del almacén de configuración de configuración  
 Esta sección muestra cómo detectar y mostrar valores de configuración.  
  
1.  En el archivo SettingsStorageCommand.cs, agregue las siguientes instrucciones using:  
  
    ```  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
2.  En `MenuItemCallback`, quite el cuerpo del método y agregue estas líneas obtener el almacén de configuración de configuración:  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
    SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     El <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> es una clase de aplicación auxiliar administrada por el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> service.  
  
3.  Ahora, averigüe si se instalan herramientas de Windows Phone. El código debe ser similar al siguiente:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");  
        string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  Probar el código. Compile la solución y comience la depuración.  
  
5.  En la instancia experimental, en la **herramientas** menú, haga clic en **SettingsStoreCommand invocar**.  
  
     Debería ver el siguiente cuadro de mensaje **herramientas de desarrollo de Microsoft Windows Phone:** seguido **True** o **False**.  
  
 Visual Studio guarda el almacén de configuración en el registro del sistema.  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Usar un editor del registro para comprobar los valores de configuración  
  
1.  Abra Regedit.exe.  
  
2.  Vaya a HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.  
  
    > [!NOTE]
    >  Asegúrese de que se trata de la clave que contiene \14.0Exp_Config\ y no \14.0_Config\\. Cuando se ejecuta la instancia experimental de Visual Studio, opciones de configuración están en el subárbol del registro "14.0Exp_Config".  
  
3.  Expanda el nodo \Installed Products\. Si el mensaje en los pasos anteriores es **instalada de herramientas de desarrollador de Microsoft Windows Phone: True**, \Installed Products\ debe contener un nodo de herramientas de desarrollo de Microsoft Windows Phone. Si el mensaje es **instalada de herramientas de desarrollador de Microsoft Windows Phone: False**, a continuación, \Installed Products\ no debe contener un nodo de herramientas de desarrollo de Microsoft Windows Phone.