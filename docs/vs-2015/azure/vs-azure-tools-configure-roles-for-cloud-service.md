---
title: Configurar los roles para un servicio de nube de Azure con Visual Studio | Microsoft Docs
description: Obtenga información sobre cómo instalar y configurar roles para Azure cloud services con Visual Studio.
author: ghogen
manager: douge
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: ce2259debb55c4792c2998f0e67df69dbc8cb7f9
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003076"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Configuración de roles de servicio en la nube de Azure con Visual Studio
Un servicio de nube de Azure puede tener uno o varios roles de web o de trabajo. Para cada rol, deberá definir cómo se configura ese rol y también configurar cómo se ejecuta esa función. Para más información acerca de los roles en cloud services, vea el vídeo [Introducción a Azure Cloud Services](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services). 

La información de su servicio en la nube se almacena en los siguientes archivos:

- **ServiceDefinition.csdef** -el archivo de definición de servicio define la configuración de tiempo de ejecución de su servicio en la nube, incluidos los roles que se requieren, los puntos de conexión y el tamaño de máquina virtual. Ninguno de los datos almacenados en `ServiceDefinition.csdef` puede cambiarse cuando se ejecuta el rol.
- **ServiceConfiguration.cscfg** : el archivo de configuración de servicio configura el número de instancias de un rol se ejecuta y los valores de la configuración definen para un rol. Los datos almacenados en `ServiceConfiguration.cscfg` se pueden cambiar mientras se ejecuta el rol.

Para almacenar valores diferentes para la configuración que controla cómo se ejecuta un rol, puede definir varias configuraciones de servicio. Puede usar una configuración de servicio diferente para cada entorno de implementación. Por ejemplo, puede establecer la cadena de conexión de la cuenta de almacenamiento para usar el emulador de almacenamiento local de Azure en una configuración de servicio local y crear otra configuración del servicio para usar el almacenamiento de Azure en la nube.

Al crear un servicio de nube de Azure en Visual Studio, se crean automáticamente dos configuraciones de servicio y se agregan al proyecto de Azure:

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Configurar un servicio de nube de Azure
Puede configurar un servicio de nube de Azure desde el Explorador de soluciones en Visual Studio, tal como se muestra en los pasos siguientes:

1. Cree o abra un proyecto de servicio de nube de Azure en Visual Studio.

1. En **el Explorador de soluciones**, haga clic en el proyecto y, en el menú contextual, seleccione **propiedades**.
   
    ![Menú contextual de proyecto de explorador de soluciones](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. En la página de propiedades del proyecto, seleccione el **desarrollo** ficha. 

    ![Página de propiedades del proyecto: pestaña desarrollo](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. En el **configuración del servicio** lista, seleccione el nombre de la configuración del servicio que desea editar. (Si desea realizar cambios en todas las configuraciones de servicio para este rol, seleccione **todas las configuraciones**.)
   
    > [!IMPORTANT]
    > Si elige una configuración de servicio específica, algunas propiedades están deshabilitadas porque solo se pueden establecer para todas las configuraciones. Para editar estas propiedades, debe seleccionar **todas las configuraciones de**.
    > 
    > 
   
    ![Lista de configuración del servicio para un servicio de nube de Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Cambiar el número de instancias de rol
Para mejorar el rendimiento de servicio en la nube, puede cambiar el número de instancias de un rol que se está ejecutando, en función del número de usuarios o la carga esperada para un rol determinado. Cuando se ejecuta el servicio en la nube en Azure, se crea una máquina virtual independiente para cada instancia de un rol. Esto afecta a la facturación de la implementación de este servicio en la nube. Para obtener más información sobre la facturación, consulte [comprender la factura de Microsoft Azure](/azure/billing/billing-understand-your-bill).

1. Cree o abra un proyecto de servicio de nube de Azure en Visual Studio.

1. En **el Explorador de soluciones**, expanda el nodo del proyecto. En el **Roles** nodo, haga clic en el rol que desea actualizar y, en el menú contextual, seleccione **propiedades**.

    ![Menú de contextual del rol de Azure en el Explorador de soluciones](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Seleccione el **configuración** ficha.

    ![Ficha Configuración](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. En el **configuración del servicio** lista, seleccione la configuración del servicio que desea actualizar.
   
    ![Lista de configuración del servicio](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. En el **recuento de instancias** texto, escriba el número de instancias que desea iniciar para este rol. Cada instancia se ejecuta en una máquina virtual independiente al publicar el servicio en la nube en Azure.

    ![Actualizar el recuento de instancias](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. Desde Visual Studio, barra de herramientas, seleccione **guardar**.

## <a name="manage-connection-strings-for-storage-accounts"></a>Administrar cadenas de conexión para las cuentas de almacenamiento
Puede agregar, quitar o modificar las cadenas de conexión para sus configuraciones de servicio. Por ejemplo, es posible que desee una cadena de conexión local para una configuración de servicio local que tiene un valor de `UseDevelopmentStorage=true`. También puede configurar una configuración de servicio en la nube que utiliza una cuenta de almacenamiento de Azure.

> [!WARNING]
> Cuando escriba la información de clave de cuenta de almacenamiento de Azure para una cadena de conexión de la cuenta de almacenamiento, esta información se almacena localmente en el archivo de configuración de servicio. Sin embargo, esta información actualmente no se almacena como texto cifrado.
> 
> 

Mediante el uso de un valor diferente para cada configuración de servicio, no tiene que utilizar cadenas de conexión diferentes en su servicio en la nube o modificar su código al publicar su servicio en la nube en Azure. Puede usar el mismo nombre para la cadena de conexión en el código y el valor es diferente, según la configuración del servicio que seleccionó al crear el servicio en la nube o al publicarlo.

1. Cree o abra un proyecto de servicio de nube de Azure en Visual Studio.

1. En **el Explorador de soluciones**, expanda el nodo del proyecto. En el **Roles** nodo, haga clic en el rol que desea actualizar y, en el menú contextual, seleccione **propiedades**.

    ![Menú de contextual del rol de Azure en el Explorador de soluciones](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Seleccione el **configuración** ficha.

    ![Pestaña Configuración](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. En el **configuración del servicio** lista, seleccione la configuración del servicio que desea actualizar.

    ![Configuración del servicio](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Para agregar una cadena de conexión, seleccione **Agregar configuración**.

    ![Agregar cadena de conexión](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Una vez agregada la nueva configuración a la lista, actualice la fila en la lista con la información necesaria.

    ![Nueva cadena de conexión](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nombre** -escriba el nombre que desea utilizar para la cadena de conexión.
    - **Tipo** : seleccione **cadena de conexión** en la lista desplegable.
    - **Valor** -puede escribir la cadena de conexión directamente en el **valor** de celda, o seleccione los puntos suspensivos (...) para trabajar el **crear cadena de conexión de almacenamiento** cuadro de diálogo.  

1. En el **crear cadena de conexión de almacenamiento** cuadro de diálogo, seleccione una opción para **conectarse mediante**. A continuación, siga las instrucciones para la opción que seleccione:

    - **Emulador de Microsoft Azure storage** : Si selecciona esta opción, el resto de la configuración en el cuadro de diálogo está deshabilitada cuando se aplican solo a Azure. Seleccione **Aceptar**.
    - **Su suscripción** : Si selecciona esta opción, utilice la lista desplegable para seleccionar e inicie sesión en una cuenta de Microsoft, o agregar una cuenta de Microsoft. Seleccione una cuenta de almacenamiento y la suscripción de Azure. Seleccione **Aceptar**.
    - **Credenciales escritas manualmente** -escriba el nombre de cuenta de almacenamiento y la clave principal o secundaria. Seleccione una opción para **conexión** (se recomienda HTTPS para la mayoría de los escenarios.) Seleccione **Aceptar**.

1. Para eliminar una cadena de conexión, seleccione la cadena de conexión y, a continuación, seleccione **Quitar configuración**.

1. Desde Visual Studio, barra de herramientas, seleccione **guardar**.

## <a name="programmatically-access-a-connection-string"></a>Acceso mediante programación a una cadena de conexión

Los pasos siguientes muestran cómo obtener acceso mediante programación a una cadena de conexión mediante C#.

1. Agregue las siguientes directivas using un C# donde va a usar la configuración del archivo:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. El código siguiente muestra un ejemplo de cómo obtener acceso a una cadena de conexión. Reemplace el &lt;ConnectionStringName > marcador de posición con el valor adecuado. 

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Agregar valores personalizados para usarlos en su servicio de nube de Azure
Configuración personalizada en el archivo de configuración de servicio le permite agregar un nombre y valor de una cadena para una configuración de servicio específico. Puede usar esta opción para configurar una característica en su servicio en la nube leyendo el valor de la configuración y utilizando este valor para controlar la lógica en el código. Puede cambiar estos valores de configuración de servicio sin tener que volver a generar el paquete de servicio o cuando se ejecuta el servicio en la nube. El código puede comprobar las notificaciones de cuando cambia un valor. Consulte [evento RoleEnvironment.Changing](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx).

Puede agregar, quitar o modificar valores personalizados para sus configuraciones de servicio. Es posible que quiera valores diferentes para estas cadenas para distintas configuraciones del servicio.

Mediante el uso de un valor diferente para cada configuración de servicio, no es necesario utilizar cadenas diferentes en su servicio en la nube o modificar el código al publicar su servicio en la nube en Azure. Puede usar el mismo nombre para la cadena en el código y el valor es diferente, según la configuración del servicio que seleccionó al crear el servicio en la nube o al publicarlo.

1. Cree o abra un proyecto de servicio de nube de Azure en Visual Studio.

1. En **el Explorador de soluciones**, expanda el nodo del proyecto. En el **Roles** nodo, haga clic en el rol que desea actualizar y, en el menú contextual, seleccione **propiedades**.

    ![Menú de contextual del rol de Azure en el Explorador de soluciones](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Seleccione el **configuración** ficha.

    ![Pestaña Configuración](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. En el **configuración del servicio** lista, seleccione la configuración del servicio que desea actualizar.

    ![Lista de configuración del servicio](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Para agregar una configuración personalizada, seleccione **Agregar configuración**.

    ![Agregar configuración personalizada](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Una vez agregada la nueva configuración a la lista, actualice la fila en la lista con la información necesaria.

    ![Nueva configuración personalizada](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nombre** -escriba el nombre de la configuración.
    - **Tipo** : seleccione **cadena** en la lista desplegable.
    - **Valor** -escriba el valor de la configuración. Puede escribir el valor directamente en el **valor** de celda, o seleccione los puntos suspensivos (...) para escribir el valor en el **Editar cadena** cuadro de diálogo.  

1. Para eliminar una configuración personalizada, seleccione la configuración y, a continuación, seleccione **Quitar configuración**.

1. Desde Visual Studio, barra de herramientas, seleccione **guardar**.

## <a name="programmatically-access-a-custom-settings-value"></a>Acceso mediante programación el valor de una configuración personalizada
 
Los pasos siguientes muestran cómo obtener acceso mediante programación a un valor personalizado mediante C#.

1. Agregue las siguientes directivas using un C# donde va a usar la configuración del archivo:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. El código siguiente muestra un ejemplo de cómo obtener acceso a una configuración personalizada. Reemplace el &lt;SettingName > marcador de posición con el valor adecuado. 
    
    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Administrar el almacenamiento local para cada instancia de rol
Puede agregar almacenamiento del sistema de archivos local para cada instancia de un rol. Los datos que se almacena en el almacenamiento no es accesible por otras instancias de la función para que los datos se almacenan o por otros roles.  

1. Cree o abra un proyecto de servicio de nube de Azure en Visual Studio.

1. En **el Explorador de soluciones**, expanda el nodo del proyecto. En el **Roles** nodo, haga clic en el rol que desea actualizar y, en el menú contextual, seleccione **propiedades**.

    ![Menú de contextual del rol de Azure en el Explorador de soluciones](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Seleccione el **almacenamiento Local** ficha.

    ![Pestaña almacenamiento local](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. En el **configuración del servicio** lista, asegúrese de que **todas las configuraciones** está seleccionada como la configuración de almacenamiento local se aplica a todas las configuraciones de servicio. Cualquier otro valor da como resultado todos los campos de entrada en la página que se va a deshabilitar. 

    ![Lista de configuración del servicio](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Para agregar una entrada de almacenamiento local, seleccione **agregar almacenamiento Local**.

    ![Agregar almacenamiento local](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Una vez agregada la nueva entrada de almacenamiento local a la lista, actualice la fila en la lista con la información necesaria.

    ![Nueva entrada de almacenamiento local](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Nombre** -escriba el nombre que desea usar para el nuevo almacenamiento local.
    - **Tamaño (MB)** -especifique el tamaño en MB que necesita para el nuevo almacenamiento local.
    - **Limpieza de reciclado de rol** : seleccione esta opción para quitar los datos en el nuevo almacenamiento local cuando se recicla la máquina virtual para el rol.

1. Para eliminar una entrada de almacenamiento local, seleccione la entrada y, a continuación, seleccione **quitar almacenamiento Local**.

1. Desde Visual Studio, barra de herramientas, seleccione **guardar**.

## <a name="programmatically-accessing-local-storage"></a>Acceso mediante programación a almacenamiento local

En esta sección se muestra cómo obtener acceso mediante programación utilizando el almacenamiento local C# escribiendo un archivo de texto de la prueba `MyLocalStorageTest.txt`.  

### <a name="write-a-text-file-to-local-storage"></a>Escribir un archivo de texto en almacenamiento local

El código siguiente muestra un ejemplo de cómo escribir un archivo de texto en el almacenamiento local. Reemplace el &lt;LocalStorageName > marcador de posición con el valor adecuado. 

    ```csharp
    // Retrieve an object that points to the local storage resource
    LocalResource localResource = RoleEnvironment.GetLocalResource("<LocalStorageName>");
    
    //Define the file name and path
    string[] paths = { localResource.RootPath, "MyLocalStorageTest.txt" };
    String filePath = Path.Combine(paths);
    
    using (FileStream writeStream = File.Create(filePath))
    {
        Byte[] textToWrite = new UTF8Encoding(true).GetBytes("Testing Web role storage");
        writeStream.Write(textToWrite, 0, textToWrite.Length);
    }

    ```

### <a name="find-a-file-written-to-local-storage"></a>Buscar un archivo escrito en el almacenamiento local

Para ver el archivo creado por el código en la sección anterior, siga estos pasos:
    
1.  En el área de notificación de Windows, haga clic en el icono de Azure y, en el menú contextual, seleccione **Mostrar IU del emulador de proceso**. 

    ![Mostrar el emulador de proceso de Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Seleccione el rol web.

    ![Emulador de proceso de Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. En el **emulador de Microsoft Azure Compute** menú, seleccione **herramientas** > **Abrir almacén local**.

    ![Elemento de menú Abrir almacén local](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Cuando se abre la ventana del explorador de Windows, escriba "MyLocalStorageTest.txt'' en el **búsqueda** cuadro de texto y seleccione **ENTRAR** para iniciar la búsqueda. 

## <a name="next-steps"></a>Pasos siguientes
Más información sobre proyectos de Azure en Visual Studio mediante la lectura de [configurar un proyecto de Azure](vs-azure-tools-configuring-an-azure-project.md). Más información sobre el esquema del servicio en la nube leyendo [Schema Reference](https://msdn.microsoft.com/library/azure/dd179398).

