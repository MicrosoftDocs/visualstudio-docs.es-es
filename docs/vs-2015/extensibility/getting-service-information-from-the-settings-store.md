---
title: Obtención de información de servicio de la configuración de Store | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0328842e3698015bceb8e24663d218e4cd3c5dfa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581584"
---
# <a name="getting-service-information-from-the-settings-store"></a>Obtención de información de servicio desde el almacén de configuración
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [obtener información de servicio de la configuración de Store](https://docs.microsoft.com/visualstudio/extensibility/getting-service-information-from-the-settings-store).  
  
Puede usar el almacén de configuración para encontrar todos los servicios disponibles o para determinar si está instalado un servicio determinado. Debe conocer el tipo de la clase de servicio.  
  
### <a name="to-list-the-available-services"></a>Para enumerar los servicios disponibles  
  
1.  Cree un proyecto VSIX denominado FindServicesExtension y, a continuación, agregue un comando personalizado denominado FindServicesCommand. Para obtener más información sobre cómo crear un comando personalizado, consulte [creación de una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  En FindServicesCommand.cs, agregue las siguientes instrucciones using:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3.  Obtiene el almacén de configuración de la configuración y luego busque la subcolección servicios con nombre. Esta colección incluye todos los servicios disponibles. En el método MenuItemCommand, quite el código existente y reemplácelo con lo siguiente:  
  
    ```  
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
  
4.  Compile la solución y comience la depuración. Aparece la instancia experimental.  
  
5.  En la instancia experimental, en el **herramientas** menú, haga clic en **FindServicesCommand invocar**.  
  
     Debería ver un cuadro de mensaje enumera todos los servicios.  
  
     Para comprobar esta configuración, puede usar el editor del registro.  
  
## <a name="finding-a-specific-service"></a>Buscar un servicio específico  
 También puede usar el <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> método para determinar si se instala un servicio determinado. Debe conocer el tipo de la clase de servicio.  
  
1.  En MenuItemCallback del proyecto que creó en el procedimiento anterior, busque el almacén de configuración de la configuración para el `Services` recopilación que tiene la subcolección denominada por el GUID del servicio. En este caso, busque el servicio de ayuda.  
  
    ```  
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
  
2.  Compile la solución y comience la depuración.  
  
3.  En la instancia experimental, en el **herramientas** menú, haga clic en **FindServicesCommand invocar**.  
  
     Debería ver un mensaje con el texto **ayudar el servicio está disponible:** seguido **True** o **False**. Para comprobar esta configuración, puede usar un editor del registro, como se muestra en los pasos anteriores.

