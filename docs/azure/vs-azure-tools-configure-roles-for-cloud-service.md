---
title: Configuración de los roles para un servicio en la nube de Azure
description: Aprenda a instalar y a configurar roles para Azure Cloud Services con Visual Studio.
author: ghogen
manager: jillfra
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 86a86a097bc5e9d3cd567502ec94aae3cbafd324
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62552451"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Configuración de los roles para un servicio de Azure con Visual Studio
Un servicio en la nube de Azure puede tener uno o más roles web o de trabajo. Para cada rol, debe definir cómo se configura ese rol y cómo se ejecuta. Para obtener más información sobre los roles en servicios en la nube, vea el vídeo [Introducción a Azure Cloud Services](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services).

La información para su servicio en la nube se almacena en los siguientes archivos:

- **ServiceDefinition.csdef**: el archivo de definición de servicio define la configuración del tiempo de ejecución de su servicio en la nube, incluidos los roles que se requieren, los puntos de conexión y el tamaño de la máquina virtual. Ninguno de los datos almacenados en `ServiceDefinition.csdef` se puede cambiar cuando se ejecuta el rol.
- **ServiceConfiguration.cscfg**: el archivo de configuración de servicio configura el número de instancias de un rol que se ejecutan y los valores de la configuración definida para un rol. Los datos almacenados en `ServiceConfiguration.cscfg` se pueden cambiar mientras se ejecuta el rol.

Para almacenar diferentes valores de la configuración que controlan el funcionamiento de su rol, puede tener varias configuraciones del servicio. Puede usar una configuración de servicio diferente para cada entorno de implementación. Por ejemplo, puede establecer su cadena de conexión de la cuenta de almacenamiento para usar el Emulador de Azure Storage local en una configuración de servicio local y crear otra configuración del servicio para usar Azure Storage en la nube.

Al crear un servicio en la nube de Azure en Visual Studio, se crean y se agregan al proyecto de Azure dos configuraciones de servicio automáticamente:

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Configurar un servicio en la nube de Azure
Puede configurar un servicio en la nube de Azure desde el Explorador de soluciones en Visual Studio, como se muestra en los siguientes pasos:

1. Cree o abra un proyecto de servicio en la nube de Azure en Visual Studio.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto y, en el menú contextual, seleccione **Propiedades**.

    ![Menú contextual del proyecto en el Explorador de soluciones](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. En la página de propiedades del proyecto, seleccione la pestaña **Desarrollo**.

    ![Página de propiedades del proyecto: pestaña Desarrollo](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. En la lista **Configuración del servicio**, seleccione el nombre de la configuración del servicio que desea modificar. (si desea realizar cambios en todas las configuraciones del servicio para este rol, seleccione **Todas las configuraciones**).

    > [!IMPORTANT]
    > Si elige una configuración de servicio específica, algunas propiedades están deshabilitadas porque solo se pueden establecer para todas las configuraciones. Para modificar estas propiedades, debe seleccionar **Todas las configuraciones**.
    >
    >

    ![Lista Configuración del servicio para un servicio en la nube de Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Cambiar el número de instancias de rol
Para mejorar el rendimiento de su servicio en la nube, puede cambiar el número de instancias de un rol que se están ejecutando, en función del número de usuarios o de la carga esperada para un rol concreto. Se crea una máquina virtual independiente para cada instancia de un rol cuando se ejecuta el servicio en la nube en Azure. Esto afecta a la facturación de la implementación de este servicio en la nube. Para más información sobre la facturación, consulte [Comprender la factura de Microsoft Azure](/azure/billing/billing-understand-your-bill).

1. Cree o abra un proyecto de servicio en la nube de Azure en Visual Studio.

1. En el **Explorador de soluciones**, expanda el nodo del proyecto. En el nodo **Roles**, haga clic con el botón derecho en el rol que desea actualizar y, en el menú contextual, seleccione **Propiedades**.

    ![Menú contextual del rol de Azure en el Explorador de soluciones](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Seleccione la pestaña **Configuración**.

    ![Pestaña Configuración](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. En la lista **Configuración del servicio**, seleccione la configuración del servicio que quiera actualizar.

    ![Lista Configuración de servicio](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. En el cuadro de texto **Recuento de instancias** , escriba el número de instancias que quiere iniciar para este rol. Cada instancia se ejecuta en una máquina virtual independiente al publicar el servicio en la nube en Azure.

    ![Actualizar el recuento de instancias](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. En la barra de herramientas de Visual Studio, seleccione **Guardar**.

## <a name="manage-connection-strings-for-storage-accounts"></a>Administrar cadenas de conexión para cuentas de almacenamiento
Puede agregar, quitar o modificar cadenas de conexión para sus configuraciones de servicio. Por ejemplo, es posible que quiera una cadena de conexión local para una configuración de servicio local que tiene un valor de `UseDevelopmentStorage=true`. También puede que desee configurar una configuración de servicio en la nube que use una cuenta de almacenamiento de Azure.

> [!WARNING]
> Al especificar la información de la clave de la cuenta de almacenamiento de Azure para una cadena de conexión de la cuenta de almacenamiento, esta información se almacena localmente en el archivo de configuración de servicio. Sin embargo, esta información no se almacena actualmente como texto cifrado.
>
>

Si usa un valor diferente para cada configuración de servicio, no tendrá que usar cadenas de conexión diferentes en su servicio en la nube ni modificar su código al publicar su servicio en la nube en Azure. Puede usar el mismo nombre para la cadena de conexión en el código y el valor será diferente, en función de la configuración del servicio que selecciona al crear su servicio en la nube o al publicarlo.

1. Cree o abra un proyecto de servicio en la nube de Azure en Visual Studio.

1. En el **Explorador de soluciones**, expanda el nodo del proyecto. En el nodo **Roles**, haga clic con el botón derecho en el rol que desea actualizar y, en el menú contextual, seleccione **Propiedades**.

    ![Menú contextual del rol de Azure en el Explorador de soluciones](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Seleccione la pestaña **Configuración**.

    ![Pestaña Settings](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. En la lista **Configuración del servicio**, seleccione la configuración del servicio que quiera actualizar.

    ![Configuración de servicio](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Para agregar una cadena de conexión, seleccione **Agregar configuración**.

    ![Agregar cadena de conexión](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Una vez agregada la nueva configuración a la lista, actualice la fila de la lista con la información necesaria.

    ![New connection string](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nombre**: escriba el nombre que desea utilizar para la cadena de conexión.
    - **Tipo**: seleccione **Cadena de conexión** en la lista desplegable.
    - **Valor**: puede escribir la cadena de conexión directamente en la celda **Valor** o seleccionar los puntos suspensivos (...) para trabajar en el cuadro de diálogo **Crear cadena de conexión de almacenamiento**.

1. En el cuadro de diálogo **Crear cadena de conexión de almacenamiento**, seleccione una opción en **Conectar utilizando**. A continuación, siga las instrucciones para la opción que seleccione:

    - **Emulador de Microsoft Azure Storage**: si selecciona esta opción, las demás opciones del cuadro de diálogo están deshabilitadas cuando afectan solo a Azure. Seleccione **Aceptar**.
    - **Su suscripción**: si selecciona esta opción, utilice la lista desplegable para seleccionar e iniciar sesión en una cuenta de Microsoft, o bien agregue una cuenta de Microsoft. Seleccione una suscripción de Azure y una cuenta de almacenamiento. Seleccione **Aceptar**.
    - **Credenciales especificadas manualmente**: escriba el nombre de la cuenta de almacenamiento y la clave principal o secundaria. Seleccione una opción en **Conexión** (se recomienda HTTPS en la mayoría de los escenarios). Seleccione **Aceptar**.

1. Para eliminar una cadena de conexión, selecciónela y seleccione **Quitar configuración**.

1. En la barra de herramientas de Visual Studio, seleccione **Guardar**.

## <a name="programmatically-access-a-connection-string"></a>Acceso mediante programación a una cadena de conexión

En los pasos siguientes se muestra cómo acceder mediante programación a una cadena de conexión con C#.

1. Agregue las siguientes directivas de uso en un archivo de C# donde va a usar la configuración:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. En el código siguiente se muestra un ejemplo de cómo acceder a una cadena de conexión. Reemplace el marcador de posición &lt;ConnectionStringName> por el valor adecuado.

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Agregar valores personalizados para usarlos en su servicio en la nube de Azure
La configuración personalizada del archivo de configuración de servicio le permite agregar un nombre y un valor para una cadena de una configuración de servicio específico. Puede elegir usar esta configuración para definir una característica en su servicio en la nube leyendo el valor de la configuración y usando este valor para controlar la lógica de su código. Puede cambiar estos valores de configuración de servicio sin tener que volver a generar el paquete de servicio o cuando se ejecuta el servicio en la nube. Su código puede buscar las notificaciones de cuando cambia un valor. Vea [RoleEnvironment.Changing Event](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx).

Puede agregar, quitar o modificar valores personalizados para sus configuraciones de servicio. Es posible que quiera valores diferentes para estas cadenas para distintas configuraciones del servicio.

Al usar un valor diferente para cada configuración de servicio, no tendrá que usar distintas cadenas en su servicio en la nube ni modificar su código al publicar su servicio en la nube en Azure. Puede usar el mismo nombre para la cadena en el código y el valor será diferente, en función de la configuración del servicio que selecciona al crear su servicio en la nube o al publicarlo.

1. Cree o abra un proyecto de servicio en la nube de Azure en Visual Studio.

1. En el **Explorador de soluciones**, expanda el nodo del proyecto. En el nodo **Roles**, haga clic con el botón derecho en el rol que desea actualizar y, en el menú contextual, seleccione **Propiedades**.

    ![Menú contextual del rol de Azure en el Explorador de soluciones](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Seleccione la pestaña **Configuración**.

    ![Pestaña Settings](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. En la lista **Configuración del servicio**, seleccione la configuración del servicio que quiera actualizar.

    ![Lista Configuración de servicio](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Para agregar una configuración personalizada, seleccione **Agregar configuración**.

    ![Agregar configuración personalizada](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Una vez agregada la nueva configuración a la lista, actualice la fila de la lista con la información necesaria.

    ![Nueva configuración personalizada](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nombre**: escriba el nombre de la configuración.
    - **Tipo de**: seleccione **Cadena** en la lista desplegable.
    - **Valor**: escriba el valor de la configuración. Puede especificar el valor directamente en la celda **Valor** o seleccionar los puntos suspensivos (...) para escribir el valor en el cuadro de diálogo **Editar cadena**.

1. Para eliminar una configuración personalizada, selecciónela y elija **Quitar configuración**.

1. En la barra de herramientas de Visual Studio, seleccione **Guardar**.

## <a name="programmatically-access-a-custom-settings-value"></a>Acceso mediante programación al valor de una configuración personalizada

En los pasos siguientes se muestra cómo acceder mediante programación a una configuración personalizada con C#.

1. Agregue las siguientes directivas de uso en un archivo de C# donde va a usar la configuración:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. En el código siguiente se muestra un ejemplo de cómo acceder a una configuración personalizada. Reemplace el marcador de posición &lt;SettingName> por el valor adecuado.

    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Administrar el almacenamiento local para cada instancia de rol
Puede agregar almacenamiento del sistema de archivos local para cada instancia de un rol. Otras instancias del rol para las que están almacenados los datos u otros roles no pueden acceder a los datos almacenados.

1. Cree o abra un proyecto de servicio en la nube de Azure en Visual Studio.

1. En el **Explorador de soluciones**, expanda el nodo del proyecto. En el nodo **Roles**, haga clic con el botón derecho en el rol que desea actualizar y, en el menú contextual, seleccione **Propiedades**.

    ![Menú contextual del rol de Azure en el Explorador de soluciones](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Seleccione la pestaña **Almacenamiento local**.

    ![Pestaña Almacenamiento local](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. En la lista **Configuración del servicio**, asegúrese de que está seleccionada la opción **Todas las configuraciones**, ya que la configuración de almacenamiento local afecta a todas las configuraciones del servicio. Cualquier otro valor hará que todos los campos de entrada en la página se deshabiliten.

    ![Lista Configuración de servicio](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Para agregar una entrada de almacenamiento local, seleccione **Agregar almacenamiento local**.

    ![Agregar almacenamiento local](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Una vez agregada la nueva entrada de almacenamiento local a la lista, actualice la fila de la lista con la información necesaria.

    ![Nueva entrada de almacenamiento local](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Nombre**: escriba el nombre que desea utilizar para el nuevo almacenamiento local.
    - **Tamaño (MB)**: especifique el tamaño en MB que necesita para el nuevo almacenamiento local.
    - **Limpiar al reciclar rol**: seleccione esta opción para quitar los datos del almacenamiento local cuando se recicla la máquina virtual para este rol.

1. Para eliminar una entrada de almacenamiento local, selecciónela y active **Remove Local Storage** (Quitar almacenamiento local).

1. En la barra de herramientas de Visual Studio, seleccione **Guardar**.

## <a name="programmatically-accessing-local-storage"></a>Acceso mediante programación al almacenamiento local

En esta sección se indica cómo acceder mediante programación al almacenamiento local con C# mediante la escritura de un archivo de texto de prueba: `MyLocalStorageTest.txt`.

### <a name="write-a-text-file-to-local-storage"></a>Escritura de un archivo de texto en el almacenamiento local

En el código siguiente se muestra un ejemplo de cómo escribir un archivo de texto en el almacenamiento local. Reemplace el marcador de posición &lt;LocalStorageName> por el valor adecuado.

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

### <a name="find-a-file-written-to-local-storage"></a>Búsqueda de un archivo escrito en el almacenamiento local

Para ver el archivo creado por el código de la sección anterior, siga estos pasos:

1. En el área de notificación de Windows, haga clic con el botón derecho en el icono de Azure y, en el menú contextual, seleccione **Show Compute Emulator UI** (Mostrar la interfaz de usuario del emulador de proceso).

    ![Mostrar el emulador de proceso de Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Seleccione el rol web.

    ![Emulador de proceso de Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. En el menú **Microsoft Azure Compute Emulator** (Emulador de proceso de Microsoft Azure), seleccione **Herramientas** > **Open local store** (Abrir almacén local).

    ![Opción de menú Open local store (Abrir almacén local)](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Cuando se abra la ventana Explorador de Windows, escriba "MyLocalStorageTest.txt" en el cuadro de texto **Buscar** y pulse **Entrar** para iniciar la búsqueda.

## <a name="next-steps"></a>Pasos siguientes
Para obtener más información sobre los proyectos de Azure en Visual Studio, consulte [Configurar un proyecto de Azure](vs-azure-tools-configuring-an-azure-project.md). Para obtener más información sobre el esquema del servicio en la nube, consulte [Referencia de esquema](https://msdn.microsoft.com/library/azure/dd179398).
