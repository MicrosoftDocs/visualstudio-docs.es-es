---
title: Obtención de información de servicio desde el almacén de configuraciones . Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b15d5c9f122ca66d21940b9998969b0d39d1a74d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711370"
---
# <a name="get-service-information-from-the-settings-store"></a>Obtener información de servicio del almacén de configuración
Puede usar el almacén de configuración para buscar todos los servicios disponibles o para determinar si un servicio determinado está instalado. Debe conocer el tipo de la clase de servicio.

## <a name="to-list-the-available-services"></a>Para enumerar los servicios disponibles

1. Cree un proyecto `FindServicesExtension` VSIX con nombre `FindServicesCommand`y, a continuación, agregue un comando personalizado denominado . Para obtener más información sobre cómo crear un comando personalizado, consulte [Crear una extensión con un comando](../extensibility/creating-an-extension-with-a-menu-command.md) de menú

2. En *FindServicesCommand.cs*, agregue las siguientes directivas using:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Obtenga el almacén de valores de configuración y, a continuación, busque la subcolección denominada Servicios. Esta colección incluye todos los servicios disponibles. En `MenuItemCommand` el método, quite el código existente y sustitúyalo por lo siguiente:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string message = "Available services:\n";
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");
        int n = 0;
        foreach (string service in collection)
        {
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";
        }

        MessageBox.Show(message);
    }
    ```

4. Compile la solución y comience la depuración. Aparece la instancia experimental.

5. En la instancia experimental, en el menú **Herramientas** , haga clic en **Invocar FindServicesCommand**.

     Debería ver un cuadro de mensaje con todos los servicios.

     Para comprobar esta configuración, puede usar el editor del Registro.

## <a name="find-a-specific-service"></a>Encuentre un servicio específico
 También puede utilizar <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> el método para determinar si un servicio determinado está instalado. Debe conocer el tipo de la clase de servicio.

1. En el MenuItemCallback del proyecto que creó en el procedimiento `Services` anterior, busque en el almacén de valores de configuración la colección que tiene la subcolección nombrada por el GUID del servicio. En este caso buscaremos el servicio de Ayuda.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);
        string message = "Help Service Available: " + hasHelpService;

        MessageBox.Show(message);
    }
    ```

2. Compile la solución y comience la depuración.

3. En la instancia experimental, en el menú **Herramientas** , haga clic en **Invocar FindServicesCommand**.

     Debería ver un mensaje con el texto Servicio de **ayuda disponible:** seguido de **Verdadero** o **Falso**. Para comprobar esta configuración, puede usar un editor del Registro, como se muestra en los pasos anteriores.
