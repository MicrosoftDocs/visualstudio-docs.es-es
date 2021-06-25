---
title: Uso del almacén de configuración | Microsoft Docs
description: Obtenga información sobre cómo leer datos del almacén de opciones de configuración, que son opciones de solo Visual Studio y VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4d7fff5bc3eeeb3b4515e2e47027f5b88fb7807d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898388"
---
# <a name="using-the-settings-store"></a>Uso del almacén de configuración
Hay dos tipos de almacenes de configuración:

- Opciones de configuración, que son opciones de solo Visual Studio y VSPackage. Visual Studio combina la configuración de todos los archivos .pkgdef conocidos en este almacén.

- Configuración de usuario, que son configuraciones que se pueden  escribir, como las que se muestran en las páginas del cuadro de diálogo Opciones, páginas de propiedades y otros cuadros de diálogo. Visual Studio extensiones pueden usarlas para el almacenamiento local de pequeñas cantidades de datos.

  En este tutorial se muestra cómo leer datos del almacén de opciones de configuración. Consulte [Escritura en el almacén de configuración de usuario](../extensibility/writing-to-the-user-settings-store.md) para obtener una explicación de cómo escribir en el almacén de configuración de usuario.

## <a name="creating-the-example-project"></a>Crear el proyecto de ejemplo
 En esta sección se muestra cómo crear un proyecto de extensión simple con un comando de menú para la demostración.

1. Cada Visual Studio extensión comienza con un proyecto de implementación de VSIX que contendrá los recursos de extensión. Cree un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto VSIX denominado `SettingsStoreExtension` . Puede encontrar la plantilla de proyecto VSIX en el cuadro **de diálogo** Nuevo proyecto en **Visual C# / Extensibilidad**.

2. Ahora agregue una plantilla de elemento de comando personalizada **denominada SettingsStoreCommand**. En el **cuadro de diálogo Agregar nuevo** elemento, vaya a Visual **C# / Extensibilidad** y seleccione **Comando personalizado**. En el **campo** Nombre de la parte inferior de la ventana, cambie el nombre del archivo de comandos a **SettingsStoreCommand.cs.** Para obtener más información sobre cómo crear un comando personalizado, vea [Crear una extensión con un comando de menú.](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>Uso del almacén de opciones de configuración
 En esta sección se muestra cómo detectar y mostrar las opciones de configuración.

1. En el archivo SettingsStorageCommand.cs, agregue las siguientes directivas using:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. En , quite el cuerpo del método y agregue estas `MenuItemCallback` líneas para obtener el almacén de opciones de configuración:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    es <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> una clase auxiliar administrada a través del <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> servicio.

3. Ahora averigá si Windows Phone Tools están instalados. El código debe ser similar al siguiente:

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

5. En la instancia experimental, en el **menú Herramientas,** haga clic **en Invocar configuraciónStoreCommand**.

    Debería ver un cuadro de mensaje que indica **Microsoft Windows Phone Herramientas de desarrollo:** seguido de **True** o **False.**

   Visual Studio mantiene el almacén de configuración en el registro del sistema.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Para usar un editor del Registro para comprobar los valores de configuración

1. Abra Regedit.exe.

2. Vaya a HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\ .

    > [!NOTE]
    > Asegúrese de que está mirando la clave que contiene \14.0Exp_Config\ y no \14.0_Config \\ . Al ejecutar la instancia experimental de Visual Studio, los valores de configuración se encuentran en el subárbol del Registro "14.0Exp_Config".

3. Expanda el nodo \Productos instalados\. Si el mensaje de los pasos anteriores es **Microsoft Windows Phone Herramientas de desarrollo Instalado: True**, \Installed Products\ debe contener un nodo Windows Phone Herramientas de desarrollo Microsoft. Si el mensaje es **Microsoft Windows Phone Herramientas de desarrollo instalado: False**, \Installed Products\ no debe contener un nodo Windows Phone Herramientas de desarrollo Microsoft.
