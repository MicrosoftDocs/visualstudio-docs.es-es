---
title: Obteniendo información del servicio desde el almacén de configuración | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51aa0369793fe5dc4b39fe510c069a7ec93d102a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647976"
---
# <a name="get-service-information-from-the-settings-store"></a>Obtención de información del servicio desde el almacén de configuración
Puede usar el almacén de configuración para buscar todos los servicios disponibles o para determinar si un servicio determinado está instalado. Debe conocer el tipo de la clase de servicio.

## <a name="to-list-the-available-services"></a>Para enumerar los servicios disponibles

1. Cree un proyecto VSIX denominado `FindServicesExtension` y, a continuación, agregue un comando personalizado denominado `FindServicesCommand`. Para obtener más información sobre cómo crear un comando personalizado, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md) .

2. En *FindServicesCommand.CS*, agregue las siguientes directivas Using:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Obtenga el almacén de opciones de configuración y, a continuación, busque la subcolección denominada Services. Esta colección incluye todos los servicios disponibles. En el método `MenuItemCommand`, quite el código existente y reemplácelo por lo siguiente:

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

5. En la instancia experimental, en el menú **herramientas** , haga clic en **invocar FindServicesCommand**.

     Debería ver un cuadro de mensaje en el que se enumeran todos los servicios.

     Para comprobar estos valores, puede utilizar el editor del registro.

## <a name="find-a-specific-service"></a>Buscar un servicio específico
 También puede utilizar el método <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> para determinar si un servicio determinado está instalado. Debe conocer el tipo de la clase de servicio.

1. En el MenuItemCallback del proyecto que creó en el procedimiento anterior, busque la colección de `Services` que tiene la subcolección denominada por el GUID del servicio en el almacén de valores de configuración. En este caso, buscaremos el servicio de ayuda.

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

3. En la instancia experimental, en el menú **herramientas** , haga clic en **invocar FindServicesCommand**.

     Debería ver un mensaje con el servicio de **ayuda de texto disponible:** seguido de **true** o **false**. Para comprobar esta configuración, puede usar un editor del registro, tal como se muestra en los pasos anteriores.
