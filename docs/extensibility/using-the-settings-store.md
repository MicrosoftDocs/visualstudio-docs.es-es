---
title: Uso de la tienda de configuración ( Settings Store) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3bbc09586f883e067e32f525a0331c1a9e253f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698516"
---
# <a name="using-the-settings-store"></a>Uso del almacén de configuración
Hay dos tipos de tiendas de configuración:

- Configuración, que son de solo lectura Visual Studio y VSPackage configuración. Visual Studio combina la configuración de todos los archivos .pkgdef conocidos en este almacén.

- Configuración de usuario, que son configuraciones que se pueden escribir, como las que se muestran en las páginas del cuadro de diálogo **Opciones,** las páginas de propiedades y otros cuadros de diálogo. Las extensiones de Visual Studio pueden usarlas para el almacenamiento local de pequeñas cantidades de datos.

  En este tutorial se muestra cómo leer datos del almacén de configuración. Consulte [Escritura en el almacén](../extensibility/writing-to-the-user-settings-store.md) de configuración de usuario para obtener una explicación de cómo escribir en el almacén de configuración de usuario.

## <a name="creating-the-example-project"></a>Creación del proyecto de ejemplo
 En esta sección se muestra cómo crear un proyecto de extensión simple con un comando de menú para la demostración.

1. Cada extensión de Visual Studio comienza con un proyecto de implementación de VSIX que contendrá los activos de extensión. Cree [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un proyecto `SettingsStoreExtension`VSIX denominado . Puede encontrar la plantilla de proyecto VSIX en el cuadro de diálogo **Nuevo proyecto** en **Visual C. / Extensibilidad**.

2. Ahora agregue una plantilla de elemento de comando personalizada denominada **SettingsStoreCommand**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a Visual **C/ Extensibilidad** y seleccione **Comando personalizado**. En el campo **Nombre** en la parte inferior de la ventana, cambie el nombre del archivo de comandos a **SettingsStoreCommand.cs**. Para obtener más información sobre cómo crear un comando personalizado, consulte [Creación de una extensión con un comando](../extensibility/creating-an-extension-with-a-menu-command.md) de menú

## <a name="using-the-configuration-settings-store"></a>Uso del almacén de configuración
 En esta sección se muestra cómo detectar y mostrar los valores de configuración.

1. En el archivo SettingsStorageCommand.cs, agregue las siguientes directivas using:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. En `MenuItemCallback`, quite el cuerpo del método y agregue estas líneas obtenga el almacén de valores de configuración:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    Es <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> una clase auxiliar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> administrada sobre el servicio.

3. Ahora averigua si las herramientas de Windows Phone están instaladas. El código debe tener este aspecto:

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

5. En la instancia experimental, en el menú **Herramientas** , haga clic en **Invocar SettingsStoreCommand**.

    Debería ver un cuadro de mensaje que dice Herramientas de desarrollo de **Microsoft Windows Phone:** seguido de **Verdadero** o **Falso**.

   Visual Studio mantiene el almacén de configuración en el registro del sistema.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Usar un editor del Registro para verificar la configuración

1. Abra regedit.exe.

2. Navegue hasta HKEY_CURRENT_USER, Software, Microsoft, VisualStudio, 14,0Exp_Config, InstalledProducts\\.

    > [!NOTE]
    > Asegúrese de que está mirando la clave que contiene el valor de\\14.0Exp_Config y no el 14,0_Config . Al ejecutar la instancia experimental de Visual Studio, los valores de configuración se encuentran en el subárbol del Registro "14.0Exp_Config".

3. Expanda el nodo "Productos instalados". Si el mensaje de los pasos anteriores es **Microsoft Windows Phone Developer Tools Installed: True**, entonces , los productos instalados deben contener un nodo de Microsoft Windows Phone Developer Tools. Si el mensaje es **Microsoft Windows Phone Developer Tools Installed: False**, no debe contener un nodo Herramientas de desarrollo de Microsoft Windows Phone.
