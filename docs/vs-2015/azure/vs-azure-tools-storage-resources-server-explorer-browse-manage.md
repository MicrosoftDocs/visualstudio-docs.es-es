---
title: Examinar y administrar los recursos de almacenamiento mediante el Explorador de servidores | Microsoft Docs
description: Exploración y administración de recursos de almacenamiento mediante el Explorador de servidores
author: ghogen
manager: douge
assetId: 658dc064-4a4e-414b-ae5a-a977a34c930d
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 00229cd88ddcab4d2d59ae40202620c374415e4b
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003046"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Examen y administración de los recursos de almacenamiento mediante el Explorador de servidores

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Información general

Si ha instalado Azure Tools para Microsoft Visual Studio, puede ver datos de la tabla, cola y blob desde cuentas de almacenamiento para Azure. Azure **almacenamiento** nodo en el Explorador de servidores muestra datos que se están en la cuenta del emulador de almacenamiento local y las otras cuentas de almacenamiento de Azure.

Para ver el Explorador de servidores en Visual Studio, en la barra de menús, seleccione **vista** > **Explorador de servidores**. El **almacenamiento** nodo muestra todas las cuentas de almacenamiento que existen en cada suscripción de Azure o el certificado que está conectado. Si no aparece la cuenta de almacenamiento, puede agregarlo siguiendo las instrucciones [más adelante en este artículo](#add-storage-accounts-by-using-server-explorer).

A partir de Azure SDK 2.7, también puede usar Cloud Explorer para ver y administrar los recursos de Azure. Para obtener más información, consulte [recursos de administración de Azure con Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md).

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Ver y administrar los recursos de almacenamiento en Visual Studio

Explorador de servidores muestra automáticamente una lista de blobs, colas y tablas en la cuenta del emulador de almacenamiento. La cuenta del emulador de almacenamiento aparece en el Explorador de servidores bajo el **almacenamiento** nodo como la **desarrollo** nodo.

Para ver los recursos de la cuenta del emulador de almacenamiento, expanda el **desarrollo** nodo. Si no se ha iniciado el emulador de almacenamiento al expandir el **desarrollo** nodo, se inicia automáticamente. Este proceso puede tardar varios segundos. Puede continuar trabajando en otras áreas de Visual Studio mientras se inicia el emulador de almacenamiento.

Para ver los recursos en una cuenta de almacenamiento, expanda el nodo de la cuenta de almacenamiento en el Explorador de servidores, donde verá **Blobs**, **colas**, y **tablas** nodos.

## <a name="work-with-blob-resources"></a>Trabajar con recursos de blob

El **Blobs** nodo muestra una lista de contenedores para la cuenta de almacenamiento seleccionada. Contenedores de blobs incluyen archivos de blob, y puede organizar estos blobs en carpetas y subcarpetas. Para obtener más información, consulte [cómo usar Blob storage en .NET](/azure/storage/blobs/storage-dotnet-how-to-use-blobs).

### <a name="to-create-a-blob-container"></a>Para crear un contenedor de blobs

1. Abra el menú contextual para el **Blobs** nodo y, a continuación, seleccione **crear contenedor de blobs**.
1. En el **crear contenedor de blobs** diálogo cuadro, escriba el nombre del nuevo contenedor.  
1. Presione ENTRAR en el teclado, o bien puede haga clic o pulse fuera del campo de nombre para guardar el contenedor de blobs.

   > [!NOTE]
   > El nombre del contenedor de blobs debe comenzar con una letra minúscula (a – z) o un número (0-9).

### <a name="to-delete-a-blob-container"></a>Para eliminar un contenedor de blobs

Abra el menú contextual para el contenedor de blobs que desea quitar y, a continuación, seleccione **eliminar**.

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Para mostrar una lista de los elementos en un contenedor de blobs

Abra el menú contextual para un nombre de contenedor de blobs de la lista y, a continuación, seleccione **abierto**.

Al ver el contenido de un contenedor de blobs, aparece en una pestaña conocida como la vista del contenedor de blobs.

![Vista del contenedor de blobs](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

Puede realizar las siguientes operaciones en blobs mediante los botones en la esquina superior derecha de la vista del contenedor de blobs:

* Escriba un valor de filtro y aplicarlo.
* Actualizar la lista de blobs del contenedor.
* Cargar un archivo.
* Eliminar un blob. (Eliminar un archivo desde un contenedor de blobs no elimina el archivo subyacente. Solo se quita del contenedor de blobs.)
* Abrir un blob.
* Guardar un blob en el equipo local.

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Para crear una carpeta o subcarpeta en un contenedor de blobs

1. Elija el contenedor de blobs en Cloud Explorer. En la ventana del contenedor, seleccione la **cargar Blob** botón.

1. En el **cargar nuevo archivo** cuadro de diálogo, seleccione el **examinar** botón para especificar el archivo que desea cargar y, a continuación, escriba un nombre de carpeta en el **carpeta (opcional)** cuadro.

   ![Cargar un archivo en una carpeta de blob](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   Puede agregar subcarpetas en carpetas de contenedor siguiendo el mismo paso. Si no especifica un nombre de carpeta, el archivo se carga en el nivel superior del contenedor de blobs. El archivo aparece en la carpeta especificada en el contenedor.

   ![Carpeta agregada a un contenedor de blobs](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. Haga doble clic en la carpeta o presione ENTRAR para ver el contenido de la carpeta. Cuando esté en la carpeta del contenedor, puede volver a la raíz del contenedor activando el **Abrir directorio primario** botón (flecha).

### <a name="to-delete-a-container-folder"></a>Para eliminar una carpeta de contenedor

Elimine todos los archivos en la carpeta.

Dado que las carpetas en contenedores de blobs son carpetas virtuales, no se puede crear una carpeta vacía. También se no se puede eliminar una carpeta para eliminar su contenido del archivo, pero en su lugar, debe eliminar todo el contenido de una carpeta para eliminar la carpeta.

### <a name="to-filter-blobs-in-a-container"></a>Para filtrar los blobs en un contenedor

Puede filtrar los blobs que se muestran especificando un prefijo común.

Por ejemplo, si escribe el prefijo **hello** en el cuadro de texto de filtro y, a continuación, seleccione el **Execute** (**!**) botón, solo aparecen los blobs que comienzan con "hello".

![Cuadro de texto de filtro](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

El cuadro de texto de filtro distingue mayúsculas de minúsculas y no admite el filtrado con caracteres comodín. Los blobs se pueden filtrar por el prefijo. El prefijo puede incluir un delimitador si usa un delimitador para organizar los blobs en una jerarquía virtual. Por ejemplo, filtrado por el prefijo "HelloFabric /" devuelve todos los blobs que comienzan con esa cadena.

### <a name="to-download-blob-data"></a>Para descargar los datos de blob

En el explorador en la nube, use cualquiera de los métodos siguientes:

* Abra el menú contextual para uno o más blobs y, a continuación, seleccione **abierto**.
* Elija el nombre del blob y, a continuación, seleccione el **abierto** botón.
* Haga doble clic en el nombre del blob.

Aparecerá el progreso de descarga de un blob en el **Azure Activity Log** ventana.

El blob se abre en el editor predeterminado para ese tipo de archivo. Si el sistema operativo reconoce el tipo de archivo, el archivo se abre en una aplicación instalada localmente. En caso contrario, se le pedirá que elija una aplicación que sea adecuada para el tipo de archivo del blob. El archivo local que se crea cuando se descarga un blob está marcado como de solo lectura.

Datos BLOB se almacena en caché localmente y se comprueban con respecto a la hora de última modificación del blob en Azure Blob storage. Si el blob se ha actualizado desde que se descargó por última vez, se descarga de nuevo. En caso contrario, el blob se carga desde el disco local.

De forma predeterminada, se descarga un blob en un directorio temporal. Para descargar los blobs en un directorio específico, abra el menú contextual para los nombres de blob seleccionados y seleccione **Guardar como**. Cuando se guarda un blob de esta manera, no se abre el archivo de blob y el archivo local se crea con atributos de lectura/escritura.

### <a name="to-upload-blobs"></a>Para cargar blobs

Para cargar blobs, seleccione el **cargar Blob** cuando el contenedor esté abierto para verlo en la vista del contenedor de blobs.

Puede elegir uno o varios archivos para cargar y puede cargar archivos de cualquier tipo. El **Azure Activity Log** ventana muestra el progreso de la carga. Para obtener más información sobre cómo trabajar con datos de blob, consulte [cómo usar Azure Blob storage en .NET](http://go.microsoft.com/fwlink/p/?LinkId=267911).

### <a name="to-view-logs-transferred-to-blobs"></a>Para ver los registros transferidos a blobs

Si usa diagnósticos de Azure para registrar los datos de la aplicación de Azure y ha transferido los registros a su cuenta de almacenamiento, verá los contenedores creados por estos registros de Azure. Ver estos registros en el Explorador de servidores es una manera fácil de identificar los problemas con la aplicación, especialmente si se haya implementado en Azure.

Para obtener más información sobre diagnósticos de Azure, consulte [recopilar datos de registro mediante Diagnósticos de Azure](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="to-get-the-url-for-a-blob"></a>Para obtener la dirección URL para un blob

Abra el menú contextual del blob y, a continuación, seleccione **copiar la dirección URL**.

### <a name="to-edit-a-blob"></a>Para editar un blob

Seleccione el blob y, a continuación, seleccione el **abrir Blob** botón.

El archivo se descarga en una ubicación temporal y abrir en el equipo local. Vuelva a cargar el blob después de realizar cambios.

## <a name="work-with-queue-resources"></a>Trabajar con recursos de cola

Las colas de servicios de almacenamiento se hospedan en una cuenta de almacenamiento de Azure. Puede usarlos para permitir que la nube los roles de servicio para comunicarse entre sí y con otros servicios mediante un mecanismo de paso de mensajes. Puede tener acceso a la cola mediante programación a través de un servicio en la nube y a través de un servicio web para los clientes externos. También puede tener acceso a la cola directamente mediante explorador de servidores en Visual Studio.

Al desarrollar un servicio en la nube que usa colas, puede usar Visual Studio para crear colas y trabajar con ellos de forma interactiva mientras desarrolla y probar el código.

En el Explorador de servidores, puede ver las colas de una cuenta de almacenamiento, crear y eliminar colas, abrir una cola para ver sus mensajes y agregar mensajes a una cola. Cuando se abre una cola para su visualización, puede ver los mensajes individuales, y puede realizar las siguientes acciones en la cola mediante los botones en la esquina superior izquierda:

* Actualice la vista de la cola.
* Agregar un mensaje a la cola.
* Quitar el primer mensaje de la cola.
* Borrar la cola completa.

La siguiente imagen muestra una cola que contiene dos mensajes:

![Visualización de una cola](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

Para obtener más información sobre el almacenamiento de colas de servicios, consulte [Introducción a Azure Queue storage mediante .NET](http://go.microsoft.com/fwlink/?LinkID=264702). Para obtener información sobre el servicio web para colas de servicios de almacenamiento, consulte [conceptos del servicio cola](http://go.microsoft.com/fwlink/?LinkId=264788). Para obtener información acerca de cómo enviar mensajes a una cola de servicios de almacenamiento mediante Visual Studio, consulte [enviar mensajes a una cola de servicios de almacenamiento](https://docs.microsoft.com/azure/visual-studio/vs-storage-cloud-services-getting-started-queues).

> [!NOTE]
> Las colas de servicios de almacenamiento son distintas de las colas de Azure Service Bus. Para obtener más información acerca de las colas de Service Bus, consulte [colas de Service Bus, temas y suscripciones](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-queues-topics-subscriptions).

## <a name="work-with-table-resources"></a>Trabajar con recursos de tabla

Azure Table storage almacena grandes cantidades de datos estructurados. El servicio es un almacén de datos NoSQL que acepta llamadas autenticadas desde dentro y fuera de la nube de Azure. Las tablas de Azure son ideales para almacenar datos estructurados y no relacionales.

### <a name="to-create-a-table"></a>Para crear una tabla

1. En Cloud Explorer, seleccione el **tablas** nodo de la cuenta de almacenamiento y, a continuación, seleccione **Create Table**.
1. En el **Create Table** diálogo cuadro, escriba un nombre para la tabla.

### <a name="to-view-table-data"></a>Para ver los datos de tabla

1. En Cloud Explorer, abra el **Azure** nodo y, a continuación, abra el **almacenamiento** nodo.
1. Abra el nodo de la cuenta de almacenamiento que está interesado y, a continuación, abra el **tablas** nodo para ver una lista de tablas para la cuenta de almacenamiento.
1. Abra el menú contextual para una tabla y, a continuación, seleccione **ver tabla**.

    ![Una tabla de Azure en el Explorador de soluciones](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

La tabla se organiza por entidades (mostradas en filas) y propiedades (que se muestran en columnas). Por ejemplo, la ilustración siguiente muestra las entidades que aparecen en el Diseñador de tablas.

### <a name="to-edit-table-data"></a>Para editar los datos de la tabla

En el Diseñador de tablas, abra el menú contextual de una entidad (una sola fila) o una propiedad (una sola celda) y, a continuación, seleccione **editar**.

    ![Add or edit a table entity](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

Las entidades en una única tabla no están necesarias tener el mismo conjunto de propiedades (columnas). Tenga en cuenta las restricciones de visualización y edición de datos de la tabla siguientes:

* No se puede ver ni editar datos binarios (`type byte[]`), pero se pueden almacenar en una tabla.
* No puede editar el **PartitionKey** o **RowKey** valores, porque el almacenamiento de tablas en Azure no admite esa operación.
* No se puede crear una propiedad denominada **Timestamp**. Servicios de Azure storage usan una propiedad con ese nombre.
* Si escribe un **DateTime** valor, debe seguir un formato que sea adecuado para la configuración regional y de idioma del equipo (por ejemplo, MM/DD/AAAA HH: mm: [AM | PM] para inglés de Estados Unidos).

### <a name="to-add-entities"></a>Para agregar entidades

1. En el Diseñador de tablas, seleccione el **Agregar entidad** botón.

    ![Botón Agregar entidad](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. En el **Agregar entidad** diálogo cuadro, escriba los valores de la **PartitionKey** y **RowKey** propiedades.

    ![Agregar cuadro de diálogo entidad](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    Escriba los valores con cuidado. No se pueden cambiar después de cerrar el cuadro de diálogo a menos que elimine la entidad y agregarla de nuevo.

### <a name="to-filter-entities"></a>Para filtrar entidades

Puede personalizar el conjunto de entidades que aparecen en una tabla si utiliza el generador de consultas.

1. Para abrir el generador de consultas, abra una tabla para su visualización.
1. Seleccione el **generador de consultas** botón de barra de herramientas de la vista de tabla.

    El **generador de consultas** aparece el cuadro de diálogo. La siguiente ilustración muestra una consulta que se está compilando en el generador de consultas.

    ![Generador de consultas](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. Cuando haya terminado la creación de la consulta, cierre el cuadro de diálogo. El formato de texto de la consulta resultante aparece en un cuadro de texto como un filtro de WCF Data Services.
1. Para ejecutar la consulta, seleccione el icono de triángulo verde.

También puede filtrar los datos de la entidad que aparece en el Diseñador de tablas si escribe una cadena de filtro de WCF Data Services directamente en el cuadro de texto de filtro. Este tipo de cadena es similar a una cláusula WHERE de SQL, pero se envía al servidor como una solicitud HTTP. Para obtener información acerca de cómo construir cadenas de filtro, vea [Constructing cadenas de filtro para el Diseñador de tablas](https://docs.microsoft.com/azure/vs-azure-tools-table-designer-construct-filter-strings).

En la siguiente ilustración se muestra un ejemplo de una cadena de filtro válidas:

![Cadena de filtro](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Actualizar los datos de almacenamiento

Al explorador de servidores se conecta a u obtiene datos de una cuenta de almacenamiento, la operación podría tardar un minuto en Finalizar. Si no se puede conectar el Explorador de servidores, la operación podría expirar. Mientras se recuperan datos, puede continuar trabajando en otras partes de Visual Studio. Para cancelar la operación si está tardando demasiado, seleccione el **Detener actualización** en la barra de herramientas del explorador de servidores.

### <a name="to-refresh-blob-container-data"></a>Para actualizar los datos del contenedor de blob

* Seleccione el **Blobs** nodo situado debajo de **almacenamiento**y, a continuación, seleccione el **actualizar** en la barra de herramientas del explorador de servidores.
* Para actualizar la lista de blobs que se muestra, seleccione el **Execute** botón.

### <a name="to-refresh-table-data"></a>Para actualizar los datos de tabla

* Seleccione el **tablas** nodo situado debajo de **almacenamiento**y, a continuación, seleccione el **actualizar** en la barra de herramientas del explorador de servidores.
* Para actualizar la lista de entidades que se muestra en el Diseñador de tablas, seleccione el **Execute** botón en el Diseñador de tablas.

### <a name="to-refresh-queue-data"></a>Para actualizar los datos de la cola

Seleccione el **colas** nodo situado debajo de **almacenamiento**y, a continuación, seleccione el **actualizar** en la barra de herramientas del explorador de servidores.

### <a name="to-refresh-all-items-in-a-storage-account"></a>Para actualizar todos los elementos de una cuenta de almacenamiento

Elija el nombre de cuenta y, a continuación, seleccione el **actualizar** en la barra de herramientas del explorador de servidores.

## <a name="add-storage-accounts-by-using-server-explorer"></a>Agregar cuentas de almacenamiento mediante el Explorador de servidores

Hay dos maneras de agregar cuentas de almacenamiento mediante el Explorador de servidores. Puede crear una cuenta de almacenamiento en su suscripción de Azure, o puede asociar una cuenta de almacenamiento.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>Para crear una cuenta de almacenamiento mediante el Explorador de servidores

1. En el Explorador de servidores, abra el menú contextual para el **almacenamiento** nodo y, a continuación, seleccione **crear cuenta de almacenamiento**.

1. En el **crear cuenta de almacenamiento** diálogo cuadro, seleccione o escriba la siguiente información:

   * La suscripción de Azure a la que desea agregar la cuenta de almacenamiento.
   * El nombre que desea usar para la nueva cuenta de almacenamiento.
   * La región o grupo de afinidad (por ejemplo, oeste de Estados Unidos o Asia oriental).
   * El tipo de replicación que desea usar para la cuenta de almacenamiento, como con redundancia local.

   ![Crear una cuenta de almacenamiento de Azure](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. Seleccione **Crear**.

La nueva cuenta de almacenamiento aparece en el **almacenamiento** lista en el Explorador de soluciones.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>Para conectar una cuenta de almacenamiento mediante el Explorador de servidores

1. En el Explorador de servidores, abra el menú contextual para el Azure **almacenamiento** nodo y, a continuación, seleccione **asociar almacenamiento externo**.

    ![Agregar una cuenta de almacenamiento existente](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. En el **crear cuenta de almacenamiento** diálogo cuadro, seleccione o escriba la siguiente información:

   * El nombre de la cuenta de almacenamiento existente que desea adjuntar.
   * La clave para la cuenta de almacenamiento seleccionada. Este valor normalmente se proporciona automáticamente cuando se selecciona una cuenta de almacenamiento. Si desea que Visual Studio recuerde la clave de cuenta de almacenamiento, seleccione el **recordar clave de cuenta** casilla de verificación.
   * El protocolo a utilizar para conectarse a la cuenta de almacenamiento, como HTTP, HTTPS o un punto de conexión personalizado. Para obtener más información sobre los extremos personalizados, consulte [cómo configurar cadenas de conexión](https://msdn.microsoft.com/library/azure/ee758697.aspx).

### <a name="to-view-the-secondary-endpoints"></a>Para ver los puntos de conexión secundaria

Si ha creado una cuenta de almacenamiento mediante el **redundancia geográfica con acceso de lectura** opción de replicación, puede ver sus extremos secundarios abriendo el menú contextual para el nombre de cuenta y, a continuación, seleccione **propiedades**.

![Puntos de conexión de almacenamiento secundaria](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>Para quitar una cuenta de almacenamiento del explorador de servidores

En el Explorador de servidores, abra el menú contextual del nombre de cuenta y, a continuación, seleccione **eliminar**. 

Si elimina una cuenta de almacenamiento, también se quita cualquier información de clave guardada para esa cuenta.

Si elimina una cuenta de almacenamiento del explorador de servidores, no afecta a la cuenta de almacenamiento ni los datos que contiene. Simplemente se quita la referencia del explorador de servidores. Para eliminar permanentemente una cuenta de almacenamiento, use la [portal Azure](https://portal.azure.com/).

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información acerca de cómo usar servicios de Azure storage, consulte [acceso a los servicios de almacenamiento de Azure](https://msdn.microsoft.com/library/azure/ee405490.aspx).
