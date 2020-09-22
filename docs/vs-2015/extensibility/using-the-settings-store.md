---
title: Usar el almacén de configuración | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b6c2810a81ada06152faea06e86a27f7907a643
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843151"
---
# <a name="using-the-settings-store"></a>Uso del almacén de configuración
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hay dos tipos de almacenes de configuración:  
  
- Opciones de configuración, que son la configuración de Visual Studio y VSPackage de solo lectura. Visual Studio combina la configuración de todos los archivos. pkgdef conocidos en este almacén.  
  
- Configuración de usuario, que es una configuración que se pueden escribir, como las que se muestran en las páginas del cuadro de diálogo **Opciones** , las páginas de propiedades y otros cuadros de diálogo. Las extensiones de Visual Studio pueden usarlas para el almacenamiento local de pequeñas cantidades de datos.  
  
  En este tutorial se muestra cómo leer datos del almacén de valores de configuración. Consulte [escribir en el almacén de configuración de usuario](../extensibility/writing-to-the-user-settings-store.md) para obtener una explicación de cómo escribir en el almacén de configuración de usuario.  
  
## <a name="creating-the-example-project"></a>Crear el proyecto de ejemplo  
 En esta sección se muestra cómo crear un proyecto de extensión simple con un comando de menú para la demostración.  
  
1. Cada extensión de Visual Studio comienza con un proyecto de implementación de VSIX que contendrá los recursos de la extensión. Cree un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Proyecto VSIX denominado `SettingsStoreExtension` . Puede encontrar la plantilla de Proyecto VSIX en el cuadro de diálogo **nuevo proyecto** en **Visual C#/extensibilidad**.  
  
2. Ahora, agregue una plantilla de elemento de comando personalizada denominada **SettingsStoreCommand**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a **Visual C#/extensibilidad** y seleccione **comando personalizado**. En el campo **nombre** situado en la parte inferior de la ventana, cambie el nombre del archivo de comandos a **SettingsStoreCommand.CS**. Para obtener más información sobre cómo crear un comando personalizado, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md) .  
  
## <a name="using-the-configuration-settings-store"></a>Usar el almacén de valores de configuración  
 En esta sección se muestra cómo detectar y mostrar los valores de configuración.  
  
1. En el archivo SettingsStorageCommand.cs, agregue las siguientes instrucciones Using:  
  
   ```  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.Settings;  
   using Microsoft.VisualStudio.Shell.Settings;  
   using System.Windows.Forms;  
   ```  
  
2. En `MenuItemCallback` , quite el cuerpo del método y agregue estas líneas para obtener el almacén de valores de configuración:  
  
   ```  
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
   ```  
  
    <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager>Es una clase auxiliar administrada sobre el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> servicio.  
  
3. Ahora Averigüe si Windows Phone herramientas están instaladas. El código debe tener este aspecto:  
  
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
  
4. Prueba del código Compile la solución y comience la depuración.  
  
5. En la instancia experimental, en el menú **herramientas** , haga clic en **invocar SettingsStoreCommand**.  
  
    Debería ver un cuadro de mensaje que indica que **Microsoft Windows Phone herramientas de desarrollo:**  seguido de **true** o **false**.  
  
   Visual Studio mantiene el almacén de configuración en el registro del sistema.  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Para usar un editor del registro para comprobar las opciones de configuración  
  
1. Abra Regedit.exe.  
  
2. Vaya a HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\14.0Exp_Config \InstalledProducts \\ .  
  
    > [!NOTE]
    > Asegúrese de que está examinando la clave que contiene \ 14.0Exp_Config \ y no \ 14.0_Config \\ . Al ejecutar la instancia experimental de Visual Studio, las opciones de configuración se encuentran en el subárbol del registro "14.0Exp_Config".  
  
3. Expanda el nodo \Installed Products \. Si el mensaje de los pasos anteriores es **Microsoft Windows Phone herramientas de desarrollo instalado: true**, \Installed Products \ debe contener un nodo microsoft Windows Phone herramientas de desarrollo. Si el mensaje es **Microsoft Windows Phone herramientas de desarrollo instalado: false**, \Installed Products \ no debe contener un nodo Microsoft Windows Phone herramientas de desarrollo.
