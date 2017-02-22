---
title: "Obtener informaci&#243;n del servicio desde el almac&#233;n de configuraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# Obtener informaci&#243;n del servicio desde el almac&#233;n de configuraci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede usar el almacén de configuración para buscar todos los servicios disponibles o para determinar si está instalado un servicio determinado. Debe conocer el tipo de la clase de servicio.  
  
### Para enumerar los servicios disponibles  
  
1.  Cree un proyecto VSIX denominado FindServicesExtension y, a continuación, agregue un comando personalizado denominado FindServicesCommand. Para obtener más información sobre cómo crear un comando personalizado, vea [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  En FindServicesCommand.cs, agregue las siguientes instrucciones using:  
  
    ```vb  
    using System.Collections.Generic; using Microsoft.VisualStudio.Settings; using Microsoft.VisualStudio.Shell.Settings; using System.Windows.Forms;  
    ```  
  
3.  Obtener el almacén de configuración de la configuración, a continuación, busque la subcolección denominada servicios. Esta colección incluye todos los servicios disponibles. En el método MenuItemCommand, quite el código existente y reemplácelo por el siguiente:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); string message = "Available services:\n"; IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services"); int n = 0; foreach (string service in collection) { message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n"; } MessageBox.Show(message); }  
    ```  
  
4.  Compile la solución y comience la depuración. Aparece la instancia experimental.  
  
5.  En la instancia experimental, en la **herramientas** menú, haga clic en **invocar FindServicesCommand**.  
  
     Debería ver un cuadro de mensaje enumera todos los servicios.  
  
     Para comprobar esta configuración, puede utilizar el editor del registro.  
  
## Buscar un servicio específico  
 También puede utilizar el <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> método para determinar si está instalado un servicio determinado. Debe conocer el tipo de la clase de servicio.  
  
1.  En MenuItemCallback del proyecto creado en el procedimiento anterior, busque el almacén de configuración de la configuración para el `Services` colección que tiene la subcolección denominada por el GUID del servicio. En este caso, busque el servicio de ayuda.  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper(); bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID); string message = "Help Service Available: " + hasHelpService; MessageBox.Show(message); }  
    ```  
  
2.  Compile la solución y comience la depuración.  
  
3.  En la instancia experimental, en la **herramientas** menú, haga clic en **invocar FindServicesCommand**.  
  
     Debería ver un mensaje con el texto **Ayuda servicio disponible:**  seguido **True** o **False**. Para comprobar esta configuración, puede utilizar un editor del registro, tal como se muestra en los pasos anteriores.