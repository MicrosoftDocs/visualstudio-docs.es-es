---
title: Mediante la configuración de Store | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e7d103415869cc30f2c940b632c73f611986af2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811367"
---
# <a name="using-the-settings-store"></a>Uso del almacén de configuración
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hay dos tipos de almacenes de configuración:  
  
- Opciones de configuración, que es la configuración de Visual Studio y VSPackage de solo lectura. Visual Studio combina los valores de todos los archivos .pkgdef conocido en este almacén.  
  
- Configuración de usuario, que es la configuración grabable, como los que se muestran en las páginas de la **opciones** cuadro de diálogo, páginas de propiedades y algunos otros cuadros de diálogo. Extensiones de Visual Studio pueden usarlas para el almacenamiento local de pequeñas cantidades de datos.  
  
  En este tutorial se muestra cómo leer datos desde el almacén de configuración de configuración. Consulte [escribir en el Store de la configuración de usuario](../extensibility/writing-to-the-user-settings-store.md) para obtener una explicación de cómo se escriben en el almacén de configuración de usuario.  
  
## <a name="creating-the-example-project"></a>Crear el proyecto de ejemplo  
 En esta sección se muestra cómo crear un proyecto de extensión simple con un comando de menú de demostración.  
  
1.  Todas las extensiones de Visual Studio se inicia con un proyecto de implementación de VSIX que contendrá los recursos de extensión. Crear un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proyecto VSIX denominado `SettingsStoreExtension`. Puede encontrar la plantilla de proyecto VSIX en el **nuevo proyecto** en el cuadro de diálogo **Visual C# / extensibilidad**.  
  
2.  Ahora agregue una plantilla de elemento de comando personalizado denominada **SettingsStoreCommand**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C# / extensibilidad** y seleccione **comando personalizado**. En el **nombre** campo en la parte inferior de la ventana, cambie el nombre de archivo de comandos para **SettingsStoreCommand.cs**. Para obtener más información sobre cómo crear un comando personalizado, consulte [creación de una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>Utilizando el Store de opciones de configuración  
 En esta sección se muestra cómo detectar y mostrar los valores de configuración.  
  
1. En el archivo SettingsStorageCommand.cs, agregue las siguientes instrucciones using:  
  
   ```  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.Settings;  
   using Microsoft.VisualStudio.Shell.Settings;  
   using System.Windows.Forms;  
   ```  
  
2. En `MenuItemCallback`, quite el cuerpo del método y agregue estas líneas obtención el almacén de configuración de la configuración:  
  
   ```  
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
   ```  
  
    El <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> es una clase auxiliar administrada a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> service.  
  
3. Ahora, averigüe si se instalan las herramientas de Windows Phone. El código debe tener este aspecto:  
  
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
  
4. Probar el código. Compile la solución y comience la depuración.  
  
5. En la instancia experimental, en el **herramientas** menú, haga clic en **SettingsStoreCommand invocar**.  
  
    Debería ver el siguiente cuadro de mensaje **Microsoft Windows Phone Developer Tools:** seguido **True** o **False**.  
  
   Visual Studio mantiene el almacén de configuración en el registro del sistema.  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Para usar un editor del registro para comprobar los valores de configuración  
  
1.  Abra Regedit.exe.  
  
2.  Vaya a HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.  
  
    > [!NOTE]
    >  Asegúrese de que está mirando la clave que contiene \14.0Exp_Config\ y no \14.0_Config\\. Cuando se ejecuta la instancia experimental de Visual Studio, opciones de configuración están en el subárbol del registro "14.0Exp_Config".  
  
3.  Expanda el nodo \Installed Products\. Si el mensaje en los pasos anteriores es **Microsoft Windows Phone Developer Tools instalado: True**, \Installed Products\ debe contener un nodo de Microsoft Windows Phone Developer Tools. Si el mensaje es **Microsoft Windows Phone Developer Tools instalado: False**, \Installed Products\ no debe contener un nodo de Microsoft Windows Phone Developer Tools.

