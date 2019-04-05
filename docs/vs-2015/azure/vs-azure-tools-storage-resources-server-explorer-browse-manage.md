---
title: Exploración y administración de recursos de almacenamiento mediante el Explorador de servidores | Microsoft Docs
description: Exploración y administración de recursos de almacenamiento mediante el Explorador de servidores
author: ghogen
manager: jillfra
assetId: 658dc064-4a4e-414b-ae5a-a977a34c930d
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 8f7044c44278410e1fc800e0e974847c090da0e3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "59002652"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Examen y administración de los recursos de almacenamiento mediante el Explorador de servidores

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Información general

Si ha instalado Azure Tools para Microsoft Visual Studio, puede ver datos de blob, cola y tabla desde las cuentas de almacenamiento de Azure. El nodo de Azure **Storage** en el Explorador de servidores muestra datos que están en la cuenta del emulador de almacenamiento local y las otras cuentas de Azure Storage.

Para ver el Explorador de servidores en Visual Studio, en la barra de menús, elija **Ver** > **Explorador de servidores**. El nodo **Storage** muestra todas las cuentas de almacenamiento que existen en cada suscripción o certificado de Azure a los que está conectado. Si no aparece la cuenta de almacenamiento, puede agregarla siguiendo las instrucciones proporcionadas [más adelante en este artículo](#add-storage-accounts-by-using-server-explorer).

A partir del SDK de Azure 2.7, también puede usar Cloud Explorer para ver y administrar los recursos de Azure. Para más información, consulte [Administración de recursos de Azure con Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md).

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Visualización y administración de recursos de almacenamiento en Visual Studio

El Explorador de servidores muestra automáticamente una lista de blobs, colas y tablas en la cuenta del emulador de almacenamiento. La cuenta del emulador de almacenamiento aparece en el Explorador de servidores bajo el nodo **Storage** como el nodo **Desarrollo**.

Para ver los recursos de la cuenta del emulador de almacenamiento, expanda el nodo **Desarrollo** . Si el emulador de almacenamiento aún no está iniciado cuando expanda el nodo **Desarrollo**, se inicia automáticamente. Este proceso puede tardar varios segundos. Puede continuar trabajando en otras zonas de Visual Studio mientras se inicia el emulador de almacenamiento.

Para ver los recursos en una cuenta de almacenamiento, expanda el nodo de la cuenta de almacenamiento en el Explorador de servidores, donde puede ver los nodos de **blobs**, **colas** y **tablas**.

## <a name="work-with-blob-resources"></a>Uso de recursos de blob

El nodo **Blobs** muestra una lista de contenedores para la cuenta de almacenamiento seleccionada. Los contenedores de blobs incluyen archivos de blob, y puede organizar estos blobs en carpetas y subcarpetas. Para más información, consulte [Uso de Blob Storage de .NET](/azure/storage/blobs/storage-dotnet-how-to-use-blobs).

### <a name="to-create-a-blob-container"></a>Para crear un contenedor de blobs

1. Abra el menú contextual del nodo **Blobs** y seleccione **Crear contenedor de blobs**.
1. Escriba el nombre del contenedor nuevo en el cuadro de diálogo **Crear contenedor de blobs**.  
1. Presione Entrar en el teclado o haga clic o pulse fuera del campo de nombre para guardar el contenedor de blobs.

   > [!NOTE]
   > El nombre del contenedor de blobs debe comenzar con una letra minúscula (a–z) o un número (0-9).

### <a name="to-delete-a-blob-container"></a>Para eliminar un contenedor de blobs

Abra el menú contextual del contenedor de blobs que quiere quitar y elija **Eliminar**.

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Para mostrar una lista de los elementos de un contenedor de blobs, siga estos pasos:

Abra el menú contextual de un nombre de contenedor de blobs de la lista y seleccione **Abrir**.

Cuando se ve el contenido de un contenedor de blobs, aparece en una pestaña conocida como vista del contenedor de blobs.

![Vista del contenedor de blobs](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

Puede realizar las siguientes operaciones en blobs mediante los botones de la esquina superior derecha de la vista del contenedor de blobs:

* Escribir un valor de filtro y aplicarlo.
* Actualizar la lista de blobs del contenedor.
* Cargar un archivo.
* Eliminar un blob. (Al eliminar un archivo de un contenedor de blobs, no se elimina el archivo subyacente. Solo se quita del contenedor de blobs).
* Abrir un blob.
* Guardar un blob en el equipo local.

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Para crear una carpeta o una subcarpeta en un contenedor de blobs

1. Elija el contenedor de blobs en Cloud Explorer. En la ventana del contenedor, seleccione el botón **Cargar blob**.

1. En el cuadro de diálogo **Cargar nuevo archivo**, seleccione el botón **Examinar** para especificar el archivo que quiere cargar y escriba luego un nombre de carpeta en el cuadro **Carpeta (opcional)**.

   ![Cargar un archivo en una carpeta de blob](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   Puede agregar subcarpetas en carpetas de contenedor siguiendo el mismo paso. Si no especifica un nombre de carpeta, el archivo se carga en el nivel superior del contenedor de blobs. El archivo aparece en la carpeta especificada en el contenedor.

   ![Carpeta agregada a un contenedor de blobs](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. Haga doble clic en la carpeta o presione Entrar para ver el contenido de la carpeta. Cuando esté en la carpeta del contenedor, puede volver a la raíz del contenedor mediante la selección del botón **Abrir directorio primario** (flecha arriba).

### <a name="to-delete-a-container-folder"></a>Para eliminar una carpeta de contenedor

Elimine todos los archivos de la carpeta.

Dado que las carpetas de los contenedores de blobs son carpetas virtuales, no se puede crear una carpeta vacía. Tampoco puede eliminar una carpeta para eliminar el contenido de los archivos, sino que, en su lugar, debe eliminar todo el contenido de una carpeta para poder eliminar la carpeta.

### <a name="to-filter-blobs-in-a-container"></a>Para filtrar los blobs de un contenedor

Puede filtrar los blobs que se muestran especificando un prefijo común.

Por ejemplo, si escribe el prefijo **hello** en el cuadro de texto del filtro y hace clic en el botón **Ejecutar** (**!**), solo aparecen los blobs que comienzan con "hello".

![Cuadro de texto de filtro](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

El cuadro de texto de filtro distingue mayúsculas de minúsculas y no admite el filtrado con caracteres comodín. Los blobs solo se pueden filtrar por prefijo. El prefijo puede incluir un delimitador si usa uno para organizar los blobs en una jerarquía virtual. Por ejemplo, el filtrado por el prefijo "HelloFabric/" devuelve todos los blobs que comienzan con esa cadena.

### <a name="to-download-blob-data"></a>Para descargar datos de blob

En Cloud Explorer, use cualquiera de los métodos siguientes:

* Abra el menú contextual de uno o varios blobs y, luego, seleccione **Abrir**.
* Elija el nombre del blob y luego seleccione el botón **Abrir**.
* Haga doble clic en el nombre del blob.

Puede ver el progreso de la descarga del blob en la ventana **Registro de actividad de Microsoft Azure** .

El blob se abre en el editor predeterminado para ese tipo de archivo. Si el sistema operativo reconoce el tipo de archivo, el archivo se abre en una aplicación instalada localmente. En caso contrario, se le pedirá que elija una aplicación que sea adecuada para el tipo de archivo del blob. El archivo local que se crea cuando descarga un blob está marcado como de solo lectura.

Los datos de blob se almacenan en caché localmente y se cotejan con la hora de la última modificación del blob en Azure Blob Storage. Si el blob se ha actualizado desde que se descargó por última vez, se descarga de nuevo. En caso contrario, se carga desde el disco local.

De forma predeterminada, el blob se descarga en un directorio temporal. Para descargar blobs en un directorio específico, abra el menú contextual de los nombres de blob seleccionados y elija **Guardar como**. Cuando se guarda un blob de esta manera, no se abre el archivo de blob y el archivo local se crea con atributos de lectura y escritura.

### <a name="to-upload-blobs"></a>Para cargar blobs

Para cargar blobs, seleccione el botón **Cargar blob** cuando el contenedor esté abierto para verlo en la vista del contenedor de blobs.

Puede elegir uno o varios archivos para cargar, así como cargar archivos de cualquier tipo. En la ventana **Registro de actividad de Azure** se muestra el progreso de la carga. Para más información sobre cómo trabajar con datos de blob, consulte [Uso de Azure Blob Storage en .NET](http://go.microsoft.com/fwlink/p/?LinkId=267911).

### <a name="to-view-logs-transferred-to-blobs"></a>Para ver los registros transferidos a blobs

Si usa Azure Diagnostics para registrar los datos de la aplicación de Azure y ha transferido los registros a la cuenta de almacenamiento, verá los contenedores creados por Azure para estos registros. Ver estos registros en el Explorador de servidores es una manera fácil de identificar los problemas de la aplicación, especialmente si se ha implementado en Azure.

Para obtener más información sobre Diagnósticos de Azure, vea [Recopilar datos de registro mediante Diagnósticos de Azure](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="to-get-the-url-for-a-blob"></a>Para obtener la dirección URL de un blob

Abra el menú contextual del blob y después seleccione **Copiar dirección URL**.

### <a name="to-edit-a-blob"></a>Para editar un blob

Seleccione el blob y después elija el botón **Abrir blob**.

El archivo se descarga en una ubicación temporal y se abre en el equipo local. Vuelva a cargar el blob después de realizar cambios.

## <a name="work-with-queue-resources"></a>Uso de recursos de cola

Las colas de servicios de almacenamiento se hospedan en una cuenta de Azure Storage. Puede usarlas para permitir que los roles de servicio en la nube se comuniquen entre sí y con otros servicios mediante un mecanismo de paso de mensajes. Puede acceder a la cola mediante programación a través de un servicio en la nube y a través de un servicio web para los clientes externos. También puede acceder a la cola directamente mediante el Explorador de servidores en Visual Studio.

Cuando se desarrolla un servicio en la nube que use colas, es recomendable usar Visual Studio para crear colas y trabajar con ellas de forma interactiva mientras desarrolla y prueba el código.

En el Explorador de servidores, puede ver las colas de una cuenta de almacenamiento, crear y eliminar colas, abrir una cola para ver sus mensajes y agregar mensajes a una cola. Cuando se abre una cola para verla, puede ver los mensajes individuales y puede realizar las siguientes acciones en la cola mediante los botones de la esquina superior izquierda:

* Actualizar la vista de la cola.
* Agregue un mensaje a la cola.
* Quitar el primer mensaje de la cola
* Borrar la cola completa.

En la siguiente imagen se muestra una cola que contiene dos mensajes:

![Visualización de una cola](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

Para más información sobre las colas de servicios de almacenamiento, consulte [Introducción a Azure Queue Storage mediante .NET](http://go.microsoft.com/fwlink/?LinkID=264702). Para obtener información sobre el servicio web para colas de servicios de almacenamiento, vea [Conceptos del servicio Cola](http://go.microsoft.com/fwlink/?LinkId=264788). Para obtener información acerca de cómo enviar mensajes a una cola de servicios de almacenamiento mediante Visual Studio, vea [Enviar mensajes a una cola de servicios de almacenamiento](/azure/visual-studio/vs-storage-cloud-services-getting-started-queues).

> [!NOTE]
> Las colas de servicios de almacenamiento son distintas de las colas de Azure Service Bus. Para más información sobre las colas de Service Bus, consulte [Colas, temas y suscripciones de Service Bus](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions).

## <a name="work-with-table-resources"></a>Uso de recursos de tabla

Azure Table Storage permite almacenar una gran cantidad de datos estructurados. El servicio es un almacén de datos NoSQL que acepta llamadas autenticadas desde dentro y fuera de la nube de Azure. Las tablas de Azure son ideales para el almacenamiento de datos estructurados no relacionales.

### <a name="to-create-a-table"></a>Para crear una tabla

1. En Cloud Explorer, seleccione el nodo **Tablas** de la cuenta de almacenamiento y, luego, seleccione **Crear tabla**.
1. En el cuadro de diálogo **Crear tabla** , escriba un nombre para la tabla.

### <a name="to-view-table-data"></a>Para ver los datos de tabla

1. En Cloud Explorer, abra el nodo **Azure** y después el nodo **Almacenamiento**.
1. Abra el nodo de la cuenta de almacenamiento que le interese y después abra el nodo **Tablas** para ver una lista de tablas para la cuenta de almacenamiento.
1. Abra el menú contextual de una tabla y después elija **Ver tabla**.

    ![Una tabla de Azure en el Explorador de soluciones](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

La tabla se organiza por entidades (mostradas en filas) y propiedades (mostradas en columnas). Por ejemplo, en la siguiente ilustración se muestran las entidades que aparecen en el Diseñador de tablas.

### <a name="to-edit-table-data"></a>Para editar los datos de tabla

En el Diseñador de tablas, abra el menú contextual de una entidad (una sola fila) o una propiedad (una sola celda) y seleccione **Editar**.

    ![Add or edit a table entity](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

No es necesario que las entidades de una sola tabla compartan el mismo conjunto de propiedades (columnas). Tenga en cuenta las siguientes restricciones sobre la visualización y la edición de los datos de tabla:

* No se pueden ver ni editar datos binarios (`type byte[]`), pero se pueden almacenar en una tabla.
* No se pueden editar los valores **PartitionKey** ni **RowKey**, porque el servicio Table Storage de Azure no admite esa operación.
* No se puede crear una propiedad denominada **Timestamp**. Los servicios de almacenamiento de Azure usan una propiedad con ese nombre.
* Si escribe un valor **DateTime**, debe seguir un formato que sea adecuado para la configuración regional y de idioma del equipo (por ejemplo, MM/DD/AAAA HH:MM:SS [AM|PM] en el caso de Inglés de Estados Unidos).

### <a name="to-add-entities"></a>Para agregar entidades

1. En el Diseñador de tablas, seleccione el botón **Agregar entidad**.

    ![Botón Agregar entidad](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. En el cuadro de diálogo **Agregar entidad**, escriba los valores de las propiedades **PartitionKey** y **RowKey**.

    ![Cuadro de diálogo Agregar entidad](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    Escriba los valores con cuidado. No los puede cambiar después de cerrar el cuadro de diálogo a menos que elimine la entidad y la agregue de nuevo.

### <a name="to-filter-entities"></a>Para filtrar entidades

Puede personalizar el conjunto de entidades que aparecen en una tabla si usa el generador de consultas.

1. Para abrir el generador de consultas, abra una tabla para su visualización.
1. Seleccione el botón **Generador de consultas** en la barra de herramientas de la vista de tabla.

    Aparece el cuadro de diálogo **Generador de consultas** . En la siguiente ilustración, se muestra una consulta que se está generando en el generador de consultas.

    ![Generador de consultas](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. Cuando haya terminado de generar la consulta, cierre el cuadro de diálogo. El formato de texto de la consulta resultante aparece en un cuadro de texto como un filtro de WCF Data Services.
1. Para ejecutar la consulta, seleccione el icono de triángulo verde.

También puede filtrar los datos de la entidad que aparece en el Diseñador de tablas si escribe una cadena de filtro de WCF Data Services directamente en el cuadro de texto de filtro. Este tipo de cadena es similar a una cláusula WHERE de SQL, pero se envía al servidor como solicitud HTTP. Para obtener información acerca de cómo construir cadenas de filtro, consulte [Crear cadenas de filtro para el Diseñador de tablas](/azure/vs-azure-tools-table-designer-construct-filter-strings).

En la siguiente ilustración se muestra un ejemplo de una cadena de filtro válida:

![Cadena de filtro](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Actualización de los datos de almacenamiento

Cuando el Explorador de servidores se conecta a una cuenta de almacenamiento u obtiene datos de ella, la operación puede tardar hasta un minuto en completarse. Si el Explorador de servidores no se puede conectar, la operación puede agotar el tiempo de espera. Mientras se recuperan datos, puede continuar trabajando en otras zonas de Visual Studio. Para cancelar la operación si está tardando demasiado, seleccione el botón **Detener actualización** en la barra de herramientas del Explorador de servidores.

### <a name="to-refresh-blob-container-data"></a>Para actualizar los datos del contenedor de blobs

* Seleccione el nodo **Blobs** bajo **Storage** y elija el botón **Actualizar** en la barra de herramientas del Explorador de servidores.
* Para actualizar la lista de blobs que se muestra, seleccione el botón **Ejecutar**.

### <a name="to-refresh-table-data"></a>Para actualizar los datos de tabla

* Seleccione el nodo **Blobs** bajo **Storage** y luego seleccione el botón **Actualizar** en la barra de herramientas del Explorador de servidores.
* Para actualizar la lista de entidades que se muestra en el Diseñador de tablas, seleccione el botón **Ejecutar** en el Diseñador de tablas.

### <a name="to-refresh-queue-data"></a>Para actualizar los datos de cola

Seleccione el nodo **Colas** bajo **Storage** y luego seleccione el botón **Actualizar** en la barra de herramientas del Explorador de servidores.

### <a name="to-refresh-all-items-in-a-storage-account"></a>Para actualizar todos los elementos de una cuenta de almacenamiento

Elija el nombre de la cuenta y después seleccione el botón **Actualizar** en la barra de herramientas del Explorador de servidores.

## <a name="add-storage-accounts-by-using-server-explorer"></a>Adición de cuentas de almacenamiento mediante el Explorador de servidores

Existen dos formas de agregar cuentas de almacenamiento mediante el Explorador de servidores. Puede crear una nueva cuenta de almacenamiento en su suscripción de Azure o puede asociar una cuenta de almacenamiento existente.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>Para crear una nueva cuenta de almacenamiento mediante el Explorador de servidores, siga estos pasos:

1. En el Explorador de servidores, abra el menú contextual del nodo **Storage** y después elija **Crear cuenta de almacenamiento**.

1. En el cuadro de diálogo **Crear cuenta de almacenamiento**, seleccione o escriba la información siguiente:

   * Suscripción de Azure a la que desee agregar la cuenta de almacenamiento.
   * Nombre que quiere usar para la nueva cuenta de almacenamiento.
   * La región o el grupo de afinidad (por ejemplo, Oeste de EE. UU. o Asia oriental).
   * El tipo de replicación que quiere usar para la cuenta de almacenamiento, por ejemplo, redundancia local.

   ![Creación de una cuenta de Azure Storage](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. Seleccione **Crear**.

La nueva cuenta de almacenamiento aparecerá en la lista **Almacenamiento** del Explorador de soluciones.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>Para asociar una nueva cuenta de almacenamiento mediante el Explorador de servidores

1. En el Explorador de servidores, abra el menú contextual del nodo **Storage** de Azure y después seleccione **Asociar almacenamiento externo**.

    ![Agregar una cuenta de almacenamiento existente](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. En el cuadro de diálogo **Crear cuenta de almacenamiento**, seleccione o escriba la información siguiente:

   * El nombre de la cuenta de almacenamiento existente que quiere asociar.
   * La clave para la cuenta de almacenamiento seleccionada. Este valor normalmente se proporciona automáticamente cuando se selecciona una cuenta de almacenamiento. Si desea que Visual Studio recuerde la clave de la cuenta de almacenamiento, active la casilla **Recordar clave de cuenta**.
   * El protocolo que se va a usar para conectarse a la cuenta de almacenamiento, como HTTP, HTTPS o un extremo personalizado. Consulte [Configuración de las cadenas de conexión de Azure Storage](https://msdn.microsoft.com/library/azure/ee758697.aspx) para más información sobre los puntos de conexión personalizados.

### <a name="to-view-the-secondary-endpoints"></a>Para ver los extremos secundarios

Si ha creado una cuenta de almacenamiento con la opción de replicación **Redundancia geográfica con acceso de lectura**, puede ver sus puntos de conexión secundarios si abre el menú contextual del nombre de la cuenta y después selecciona **Propiedades**.

![Extremos secundarios de almacenamiento](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>Para quitar una cuenta de almacenamiento del Explorador de servidores

En el Explorador de servidores, abra el menú contextual del nombre de cuenta y elija **Eliminar**. 

Si elimina una cuenta de almacenamiento, también se quita cualquier información de clave guardada para esa cuenta.

Si elimina una cuenta de almacenamiento del Explorador de servidores, ni la cuenta de almacenamiento, ni ninguno de los datos, se verán afectados. Simplemente se quita la referencia del Explorador de servidores. Para eliminar de forma permanente una cuenta de almacenamiento, use [Azure Portal](https://portal.azure.com/).

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información acerca de cómo usar servicios de Azure storage, consulte [Introducción a Azure Storage](/azure/storage/common/storage-introduction).
