---
title: Obtener información del servicio del almacén de configuración | Microsoft Docs
description: Obtenga información sobre cómo usar el almacén de configuración para buscar todos los servicios disponibles o para determinar si un servicio determinado está instalado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb014803945ea88cd6c2c27eee8c120059014a18
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900647"
---
# <a name="get-service-information-from-the-settings-store"></a>Obtener información de servicio del almacén de configuración
Puede usar el almacén de configuración para buscar todos los servicios disponibles o para determinar si un servicio determinado está instalado. Debe conocer el tipo de la clase de servicio.

## <a name="to-list-the-available-services"></a>Para enumerar los servicios disponibles

1. Cree un proyecto VSIX denominado `FindServicesExtension` y agregue un comando personalizado denominado `FindServicesCommand` . Para obtener más información sobre cómo crear un comando personalizado, vea [Crear una extensión con un comando de menú.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. En *FindServicesCommand.cs,* agregue las siguientes directivas using:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Obtenga el almacén de opciones de configuración y, a continuación, busque la subcolección llamada Services. Esta colección incluye todos los servicios disponibles. En el `MenuItemCommand` método , quite el código existente y reemplázlo por lo siguiente:

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

5. En la instancia experimental, en el **menú Herramientas,** haga clic **en Invocar FindServicesCommand**.

     Debería ver un cuadro de mensaje que enumera todos los servicios.

     Para comprobar esta configuración, puede usar el editor del Registro.

## <a name="find-a-specific-service"></a>Buscar un servicio específico
 También puede usar el método <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> para determinar si un servicio determinado está instalado. Debe conocer el tipo de la clase de servicio.

1. En MenuItemCallback del proyecto que creó en el procedimiento anterior, busque en el almacén de opciones de configuración la colección que tiene la subcolección denominada por el `Services` GUID del servicio. En este caso, buscaremos el servicio de Ayuda.

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

3. En la instancia experimental, en el **menú Herramientas,** haga clic **en Invocar FindServicesCommand**.

     Debería ver un mensaje con el texto **Servicio de Ayuda disponible:** seguido de **True** o **False.** Para comprobar esta configuración, puede usar un editor del Registro, como se muestra en los pasos anteriores.
