---
title: Configuración de diagnósticos para Azure Cloud Services y máquinas virtuales | Microsoft Docs
description: Aprenda a configurar el diagnóstico para depurar los servicios en la nube y las máquinas virtuales (VM) de Azure en Visual Studio.
author: mikejo5000
manager: jillfra
ms.assetid: e70cd7b4-6298-43aa-adea-6fd618414c26
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 06/28/2018
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 45e0eca12ecde6c6ede2e290f109ef04ce2035ff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62556419"
---
# <a name="set-up-diagnostics-for-azure-cloud-services-and-virtual-machines"></a>Configuración de diagnósticos para Azure Cloud Services y máquinas virtuales
Cuando tenga que solucionar problemas de un servicio en la nube o una máquina virtual de Azure, puede usar Visual Studio para configurar más fácilmente Azure Diagnostics. Diagnostics captura los datos del sistema y los datos de registro en las máquinas virtuales y las instancias de máquina virtual que ejecutan el servicio en la nube. Los datos de Diagnostics se transfieren a la cuenta de almacenamiento que elija. Para más información sobre el registro de diagnósticos en Azure, consulte [Habilitación del registro de diagnóstico para Web Apps en Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

En este artículo, le mostramos cómo usar Visual Studio para activar y configurar Azure Diagnostics, tanto antes como después de la implementación. Aprenda a configurar Diagnostics en máquinas virtuales de Azure, además de cómo seleccionar los tipos de información de diagnóstico que se recopilarán y cómo ver la información recopilada.

Puede usar una de las opciones siguientes para configurar Azure Diagnostics:

* Puede cambiar la configuración de diagnóstico a través del cuadro de diálogo **Configuración de diagnósticos** en Visual Studio. La configuración se guarda en un archivo denominado diagnostics.wadcfgx (en Azure SDK 2.4 o versiones anteriores,el archivo se llama diagnostics.wadcfg). También puede modificar directamente el archivo de configuración. Si actualiza manualmente el archivo, los cambios de configuración surten efecto la próxima vez que implementa el servicio en la nube en Azure o que ejecuta el servicio en el emulador.
* Use Cloud Explorer o el Explorador de servidores en Visual Studio para cambiar la configuración de diagnóstico de una máquina virtual o un servicio en la nube en ejecución.

## <a name="azure-sdk-26-diagnostics-changes"></a>Cambios de los diagnósticos de Azure SDK 2.6
Los siguientes cambios son válidos en proyectos de Azure SDK 2.6 y versiones posteriores en Visual Studio:

* El emulador local ahora es compatible con diagnósticos. Esto significa que puede recopilar datos de diagnóstico y asegurarse de que su aplicación crea los seguimientos correctos mientras desarrolla y realiza pruebas en Visual Studio. La cadena de conexión `UseDevelopmentStorage=true` activa la colección de datos de diagnóstico mientras ejecuta el proyecto de servicio en la nube en Visual Studio mediante el emulador de Azure Storage. Todos los datos de diagnóstico se recopilan en la cuenta de Almacenamiento de desarrollo.
* La cadena de conexión de la cuenta de almacenamiento de diagnóstico `Microsoft.WindowsAzure.Plugins.Diagnostics.ConnectionString` se almacena en el archivo de configuración de servicio (.cscfg). En Azure SDK 2.5, la cuenta de almacenamiento de diagnóstico se especificó en el archivo diagnostics.wadcfgx.

La cadena de conexión funciona de manera diferente en algunos aspectos clave en Azure SDK 2.6 y versiones posteriores, en comparación con Azure SDK 2.4 y versiones anteriores:

* En Azure SDK 2.4 y versiones anteriores, la cadena de conexión se usa como sistema de tiempo de ejecución mediante el complemento de diagnóstico para obtener la información de la cuenta de almacenamiento para la transferencia de registros de diagnóstico.
* En Azure SDK 2.6 y versiones posteriores, Visual Studio usa la cadena de conexión de diagnóstico para configurar la extensión de Azure Diagnostics con la información de la cuenta de almacenamiento adecuada durante la publicación. Puede usar la cadena de conexión para definir cuentas de almacenamiento diferentes para distintas configuraciones de servicio que Visual Studio usa durante la publicación. Sin embargo, dado que el complemento de diagnóstico ya no está disponible después de Azure SDK 2.5, el archivo .cscfg por sí solo no puede configurar la extensión de diagnósticos. Debe configurar la extensión por separado mediante herramientas como Visual Studio o PowerShell.
* Para simplificar el proceso de configuración de la extensión de diagnósticos con PowerShell, la salida del paquete de Visual Studio también incluye el XML de configuración pública para la extensión de diagnósticos para cada rol. Visual Studio usa la cadena de conexión de diagnósticos para rellenar la información de la cuenta de almacenamiento en la configuración pública. Los archivos de configuración pública se crean en la carpeta Extensions. Los archivos de configuración pública usan el patrón de nomenclatura PaaSDiagnostics.&lt;nombre de rol\>.PubConfig.xml. Cualquier implementación basada en PowerShell puede usar este patrón para asignar cada configuración a un rol.
* [Azure Portal](http://go.microsoft.com/fwlink/p/?LinkID=525040) usa la cadena de conexión en el archivo .cscfg para tener acceso a los datos de diagnóstico. Los datos aparecen en la pestaña **Supervisión**. La cadena de conexión se requiere a fin de configurar el servicio para que muestre los datos de supervisión detallada en el portal.

## <a name="migrate-projects-to-azure-sdk-26-and-later"></a>Migración de proyectos a Azure SDK 2.6 y versiones posteriores
Al migrar de Azure SDK 2.5 a Azure SDK 2.6 o versiones posteriores, si tenía una cuenta de almacenamiento de diagnósticos especificada en el archivo .wadcfgx, permanece allí. Para aprovechar la flexibilidad del uso de cuentas de almacenamiento diferentes para distintas configuraciones de almacenamiento, agregue manualmente la cadena de conexión al proyecto. Si va a migrar un proyecto de Azure SDK 2.4 o una versión anterior a Azure SDK 2.6, se conservan las cadenas de conexión de diagnóstico. Sin embargo, tenga en cuenta los cambios en el modo en que se tratan las cadenas de conexión en Azure SDK 2.6, que se describen en la sección anterior.

### <a name="how-visual-studio-determines-the-diagnostics-storage-account"></a>Cómo determina Visual Studio la cuenta de almacenamiento de diagnósticos
* Si se especifica una cadena de conexión de diagnóstico en el archivo .cscfg, Visual Studio lo usa para configurar la extensión de diagnósticos durante la publicación y al generar los archivos XML de configuración pública durante el empaquetado.
* Si no se especifica ninguna cadena de conexión de diagnóstico en el archivo .cscfg, Visual Studio recurre a usar la cuenta de almacenamiento especificada en el archivo .wadcfgx para configurar la extensión de diagnósticos para publicar y para generar los archivos XML de configuración pública durante el empaquetado.
* La cadena de conexión de diagnóstico del archivo .cscfg tiene prioridad sobre la cuenta de almacenamiento del archivo .wadcfgx. Si se especifica una cadena de conexión de diagnóstico en el archivo .cscfg, Visual Studio la usa y omite la cuenta de almacenamiento en .wadcfgx.

### <a name="what-does-the-update-development-storage-connection-strings-check-box-do"></a>¿Qué hace la casilla "Actualizar las cadenas de conexión de almacenamiento de..."?
La casilla **Actualizar las cadenas de conexión de almacenamiento de desarrollo para el diagnóstico y el almacenamiento en caché con las credenciales de la cuenta de almacenamiento de Microsoft Azure al publicar en Microsoft Azure** le ofrece una manera cómoda de actualizar cualquier cadena de conexión de cuenta de almacenamiento de desarrollo con la cuenta de almacenamiento de Azure especificada durante la publicación.

Por ejemplo, si activa esta casilla y la cadena de conexión de diagnóstico especifica `UseDevelopmentStorage=true`, al publicar el proyecto en Azure, Visual Studio actualiza automáticamente la cadena de conexión de diagnóstico con la cuenta de almacenamiento que especificó en el Asistente para publicación. Sin embargo, si se especificó una cuenta de almacenamiento real como la cadena de conexión de diagnóstico, se usa esa cuenta en su lugar.

## <a name="diagnostics-functionality-differences-in-azure-sdk-24-and-earlier-vs-azure-sdk-25-and-later"></a>Diferencias de funcionalidad de diagnóstico entre Azure SDK 2.4 y versiones anteriores frente a Azure SDK 2.5 y versiones posteriores
Si va a actualizar su proyecto de Azure SDK 2.4 y versiones anteriores a Azure SDK 2.5 o versiones posteriores, debe tener en cuenta las siguientes diferencias en la funcionalidad de diagnóstico:

* **Las API de configuración están en desuso**. La configuración mediante programación del diagnóstico está disponible en Azure SDK 2.4 y versiones anteriores, pero está en desuso en Azure SDK 2.5 y versiones posteriores. Si la configuración de diagnóstico está definida actualmente en el código, debe volver a definir esa configuración desde el principio en el proyecto migrado para que el diagnóstico siga funcionando. El archivo de configuración de diagnósticos para Azure SDK 2.4 es diagnostics.wadcfg. El archivo de configuración de diagnósticos para Azure SDK 2.5 y versiones posteriores es diagnostics.wadcfg.
* **El diagnóstico para aplicaciones de servicio en la nube se puede configurar en el nivel de rol**. En Azure SDK 2.5 y versiones posteriores, no se pueden configurar los diagnósticos para aplicaciones de servicio en la nube en el nivel de instancia.
* **Cada vez que implementa la aplicación, se actualiza la configuración de diagnóstico**. Esto puede provocar problemas de paridad si cambia la configuración de diagnóstico del Explorador de servidores de Visual Studio y luego vuelve a implementar la aplicación.
* **En Azure SDK 2.5 y versiones posteriores, los volcados de memoria se configuran en el archivo de configuración de diagnóstico y no en el código**. Si tiene volcados de memoria configurados en el código, debe transferir manualmente la configuración del código al archivo de configuración. Los volcados de memoria no se transfieren durante la migración a Azure SDK 2.6.

## <a name="turn-on-diagnostics-in-cloud-service-projects-before-you-deploy-them"></a>Activación de diagnósticos en los proyectos de servicios en la nube antes de implementarlos
En Visual Studio, puede recopilar datos de diagnóstico para roles que se ejecutan en Azure, al ejecutar el servicio en el emulador antes de la implementación. Todos los cambios a la configuración de diagnóstico de Visual Studio se guardan en el archivo de configuración diagnostics.wadcfgx. Esta configuración especifica la cuenta de almacenamiento donde se guardan los datos de diagnóstico cuando implementa el servicio en la nube.

[!INCLUDE [cloud-services-wad-warning](./includes/cloud-services-wad-warning.md)]

### <a name="to-turn-on-diagnostics-in-visual-studio-before-deployment"></a>Activar los diagnósticos en Visual Studio antes de la implementación

1. En el menú contextual para el rol, seleccione **Propiedades**. En el cuadro de diálogo **Propiedades** del rol, seleccione la pestaña **Configuración**.
2. En la sección **Diagnósticos**, asegúrese de que la casilla **Habilitar diagnósticos** está seleccionada.

    ![Acceso a la opción Habilitar diagnósticos](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796660.png)
3. Para especificar la cuenta de almacenamiento para los datos de diagnóstico, seleccione el botón de puntos suspensivos (...).

    ![Especificar la cuenta de almacenamiento que se va a usar](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796661.png)
4. En el cuadro de diálogo **Crear cadena de conexión de almacenamiento**, especifique si quiere conectarse mediante el Emulador de Azure Storage, una suscripción de Azure o credenciales escritas manualmente.

    ![Cuadro de diálogo Cuenta de almacenamiento](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796662.png)

   * Si selecciona **Emulador de Microsoft Azure Storage**, la cadena de conexión se establece en `UseDevelopmentStorage=true`.
   * Si selecciona **Su suscripción**, puede elegir la suscripción de Azure que quiere usar y escribir un nombre de cuenta. Para administrar las suscripciones de Azure, seleccione **Administrar cuentas**.
   * Si selecciona **Credenciales escritas manualmente**, se le pedirá que escriba el nombre y la clave de la cuenta de Azure que quiere usar.
5. Para ver el cuadro de diálogo **Configuración de diagnóstico**, seleccione **Configurar**. Excepto para **General** y **Directorios de registro**, cada pestaña representa un origen de datos de diagnóstico que puede recopilar. La pestaña **General** predeterminada ofrece las siguientes opciones de recopilación de datos de diagnóstico: **Solo errores**, **Toda la información** y **Plan personalizado**. La opción predeterminada **Solo errores** usa la cantidad mínima de almacenamiento porque no transfiere advertencias ni mensajes de seguimiento. La opción **Toda la información** transfiere la mayor parte de la información, usa el máximo almacenamiento y, por tanto, es la opción más cara.

   > [!NOTE]
   > El tamaño mínimo admitido de "Cuota de disco en MB" es de 4 GB. Sin embargo, si va a recopilar volcados de memoria, aumente a un valor superior, como 10 GB.
   >

    ![Habilitar configuración y diagnóstico de Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
6. En este ejemplo, seleccione la opción **Plan personalizado** para que pueda personalizar los datos recopilados.
7. El cuadro **Cuota de disco en MB** especifica la cantidad de espacio que quiere asignar en su cuenta de almacenamiento de datos de diagnóstico. Puede cambiar o aceptar el valor predeterminado.
8. En cada pestaña de datos de diagnóstico que quiera recopilar, active su casilla **Habilitar la transferencia de \<tipo de registro\>**. Por ejemplo, si quiere recopilar registros de aplicación, en la pestaña **Registros de aplicación**, active la casilla **Habilitar la transferencia de registros de aplicación**. Además, especifique cualquier otra información requerida por cada tipo de datos de diagnóstico. Para consultar la información de configuración de cada pestaña, vea la sección **Configuración de orígenes de datos de diagnósticos** más adelante en este artículo.
9. Después de habilitar la recopilación de todos los datos de diagnóstico que quiera, seleccione **Aceptar**.
10. Abra el proyecto del servicio en la nube de Azure en Visual Studio de la manera habitual. Conforme usa la aplicación, la información de registro que habilitó se guarda en la cuenta de almacenamiento de Azure que especificó.

## <a name="turn-on-diagnostics-on-azure-virtual-machines"></a>Activación del diagnóstico en máquinas virtuales de Azure
En Visual Studio, puede recopilar datos de diagnóstico para máquinas virtuales de Azure.

### <a name="to-turn-on-diagnostics-on-azure-virtual-machines"></a>Para activar el diagnóstico en máquinas virtuales de Azure

1. En el Explorador de servidores, elija el nodo de Azure y luego conéctese a su suscripción de Azure, si aún no está conectado.
2. Expanda el nodo **Máquinas virtuales** . Puede crear una nueva máquina virtual o seleccionar una que ya exista.
3. En el menú contextual para la máquina virtual que le interese, seleccione **Configurar**. Aparece el cuadro de diálogo de configuración de la máquina virtual.

    ![Configuración de una máquina virtual de Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796663.png)
4. Si aún no está instalado, agregue la extensión Diagnósticos de Microsoft Monitoring Agent. Con esta extensión, puede recopilar datos de diagnóstico para la máquina virtual de Azure. En **Extensiones instaladas**, en el cuadro de lista desplegable **Seleccionar una extensión disponible**, seleccione **Diagnósticos de Microsoft Monitoring Agent**.

    ![Instalación de una extensión de máquina virtual de Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766024.png)

    > [!NOTE]
   > Hay otras extensiones de diagnóstico disponibles para las máquinas virtuales. Para obtener más información, consulte [Características y extensiones de las máquinas virtuales para Windows](https://docs.microsoft.com/azure/virtual-machines/windows/extensions-features).
   >
   >
5. Para agregar la extensión y ver su cuadro de diálogo **Configuración de diagnóstico**, seleccione **Agregar**.
6. Para especificar una cuenta de almacenamiento, seleccione **Configurar** y, a continuación, **Aceptar**.

    Cada pestaña (excepto para **General** y **Directorios de registro**) representa un origen de datos de diagnóstico que puede recopilar.

    ![Habilitar configuración y diagnóstico de Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)

    La pestaña **General**, que es la predeterminada, ofrece estas opciones de recopilación de datos de diagnóstico: **Solo errores**, **Toda la información** y **Plan personalizado**. La opción predeterminada **Solo errores**toma la cantidad mínima de almacenamiento porque no transfiere advertencias o mensajes de seguimiento. La opción **Toda la información** transfiere la mayoría de la información y, por tanto, es la opción más cara en términos de almacenamiento.
7. En este ejemplo, seleccione la opción **Plan personalizado** para que pueda personalizar los datos recopilados.
8. El cuadro **Cuota de disco en MB** especifica la cantidad de espacio que quiere asignar en su cuenta de almacenamiento de datos de diagnóstico. Puede cambiar el valor predeterminado si lo desea.
9. En cada pestaña de datos de diagnóstico que quiera recopilar, active su casilla **Habilitar la transferencia de \<tipo de registro\>**.

    Por ejemplo, si quiere recopilar registros de aplicación, seleccione la casilla **Habilitar la transferencia de registros de aplicación** en la pestaña **Registros de aplicación**. Además, especifique cualquier otra información requerida por cada tipo de datos de diagnóstico. Para consultar la información de configuración de cada pestaña, vea la sección **Configuración de orígenes de datos de diagnósticos** más adelante en este artículo.
10. Después de habilitar la recopilación de todos los datos de diagnóstico que quiera, seleccione **Aceptar**.
11. Guarde el proyecto actualizado.

    Un mensaje en la ventana **Registro de actividad de Microsoft Azure** indica que la máquina virtual se ha actualizado.

## <a name="set-up-diagnostics-data-sources"></a>Configuración de orígenes de datos de diagnósticos
Cuando habilite la recopilación de datos de diagnóstico, puede elegir exactamente qué orígenes de datos quiere recopilar y qué información se recopila. En las secciones siguientes se describen las pestañas del cuadro de diálogo **Configuración de diagnósticos** y lo que significa cada opción de configuración.

### <a name="application-logs"></a>Registros de aplicación
Los registros de aplicación contienen información de diagnóstico generada por una aplicación web. Si quiere capturar registros de aplicación, active la casilla **Habilitar la transferencia de registros de aplicación** . Para aumentar o disminuir el intervalo entre la transferencia de registros de aplicación a la cuenta de almacenamiento, cambie el valor **Período de transferencia (min)**. También puede cambiar la cantidad de información que se captura en el registro estableciendo el valor **Nivel de registro**. Por ejemplo, seleccione **Detallado** para más información o **Crítico** para capturar solo los errores críticos. Si tiene un proveedor de diagnósticos específico que emite registros de aplicación, puede capturarlos agregando el GUID del proveedor en el cuadro **GUID de proveedor** .

  ![Registros de aplicación](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758145.png)

Para más información sobre los registros de aplicación, vea [Habilitación del registro de diagnóstico para aplicaciones web en Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="windows-event-logs"></a>Registros de eventos de Windows
Para capturar registros de aplicación de Windows, active la casilla **Habilitar la transferencia de registros de eventos de Windows** . Para aumentar o disminuir el intervalo entre la transferencia de registros de eventos a la cuenta de almacenamiento, cambie el valor **Período de transferencia (min)**. Active las casillas para los tipos de eventos de los que quiera realizar un seguimiento.

![Registros de eventos](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796664.png)

Si usa Azure SDK 2.6 o versiones posteriores y quiere especificar un origen de datos personalizado, escríbalo en el cuadro de texto **\<Nombre del origen de datos\>** y luego seleccione **Agregar**. El origen de datos se agrega al archivo diagnostics.cfcfg.

Si usa Azure SDK 2.5 y quiere especificar un origen de datos personalizado, puede agregarlo a la sección `WindowsEventLog` del archivo diagnostics.wadcfgx , como en el ejemplo siguiente:

```xml
<WindowsEventLog scheduledTransferPeriod="PT1M">
   <DataSource name="Application!*" />
   <DataSource name="CustomDataSource!*" />
</WindowsEventLog>
```

### <a name="performance-counters"></a>Contadores de rendimiento
La información del contador de rendimiento puede ayudarle a buscar cuellos de botella del sistema y a optimizar el rendimiento del sistema y de la aplicación. Para más información, vea [Crear y usar contadores de rendimiento en una aplicación de Azure](https://msdn.microsoft.com/library/azure/hh411542.aspx). Para capturar los contadores de rendimiento, active la casilla **Habilitar la transferencia de contadores de rendimiento** . Para aumentar o disminuir el intervalo entre la transferencia de registros de eventos a la cuenta de almacenamiento, cambie el valor **Período de transferencia (min)**. Active las casillas para los contadores de rendimiento de los que quiera realizar un seguimiento.

![Contadores de rendimiento](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758147.png)

Para realizar el seguimiento de un contador de rendimiento que no aparece en la lista, especifíquelo con la sintaxis sugerida. A continuación, seleccione **Agregar**. El sistema operativo de la máquina virtual determina a qué contadores de rendimiento puede realizar el seguimiento. Para más información sobre la sintaxis, vea [Especificación de una ruta de contador](https://msdn.microsoft.com/library/windows/desktop/aa373193.aspx).

### <a name="infrastructure-logs"></a>Registros de infraestructura
Los registros de infraestructura tienen información sobre la infraestructura de diagnóstico de Azure, el módulo RemoteAccess y el módulo RemoteForwarder. Para recopilar información sobre los registros de infraestructura, active la casilla **Habilitar transferencia de registros de infraestructura**. Para aumentar o disminuir el intervalo entre la transferencia de registros de infraestructura a la cuenta de almacenamiento, cambie el valor **Período de transferencia (min)**.

![Registros de infraestructura de diagnóstico](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758148.png)

Para más información, consulte [Recopilar datos de registro mediante Azure Diagnostics](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="log-directories"></a>Directorios de registro
Los directorios de registro tienen datos recopilados para las solicitudes de Internet Information Services (IIS), las solicitudes con error o las carpetas que elija. Para capturar los directorios de registro, active la casilla **Habilitar la transferencia de directorios de registro**. Para aumentar o disminuir el intervalo entre la transferencia de registros a la cuenta de almacenamiento, cambie el valor **Período de transferencia (min)**.

Puede activar las casillas de los registros que quiera recopilar, como **Registros de IIS** y los registros de **Solicitud con error**. Se proporcionan nombres de contenedor de almacenamiento predeterminados, pero puede cambiar los nombres.

Puede capturar registros desde cualquier carpeta. Especifique la ruta de acceso en la sección **Registro del directorio absoluto** y seleccionar **Agregar directorio**. Los registros se capturan en los contenedores especificados.

![Directorios de registro](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796665.png)

### <a name="etw-logs"></a>Registros de ETW
Si usa [Seguimiento de eventos para Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) (ETW) y quiere capturar registros de ETW, active la casilla **Habilitar la transferencia de registros de ETW**. Para aumentar o disminuir el intervalo entre la transferencia de registros a la cuenta de almacenamiento, cambie el valor **Período de transferencia (min)**.

Los eventos se capturan de los orígenes de eventos y manifiestos de eventos que especifique. Para especificar un origen de eventos, en la sección **Orígenes de eventos** escriba un nombre y luego seleccione **Agregar origen de evento**. De forma similar, puede especificar un manifiesto de evento en la sección **Manifiestos de eventos** y luego seleccionar **Agregar manifiesto de evento**.

![Registros de ETW](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766025.png)

El marco de ETW se admite en ASP.NET a través de las clases del espacio de nombres [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)). El espacio de nombres Microsoft.WindowsAzure.Diagnostics, que se hereda de las clases estándar [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)), permite el uso de [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) como plataforma de registro en el entorno de Azure. Para más información, vea [Tome el control de registro y seguimiento en Microsoft Azure](https://msdn.microsoft.com/magazine/ff714589.aspx) y [Habilitación de diagnósticos en Azure Cloud Services y máquinas virtuales](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="crash-dumps"></a>Volcados de memoria
Para capturar información sobre cuándo se bloquea una instancia de rol, active la casilla **Habilitar la transferencia de volcados de memoria**. (Puesto que ASP.NET controla la mayoría de las excepciones, normalmente solo es útil para roles de trabajo.) Para aumentar o disminuir el porcentaje del espacio de almacenamiento dedicado a los volcados de memoria, cambie el valor **Cuota de directorio (%)**. Puede cambiar el contenedor de almacenamiento donde se almacenan los volcados de memoria y seleccionar si quiere capturar un volcado **Completo** o **Mini**.

En la captura de pantalla siguiente, se muestran los procesos de los que se está realizando un seguimiento actualmente. Active las casillas para los procesos que quiera capturar. Para agregar otro proceso a la lista, escriba el nombre del proceso y luego seleccione **Agregar proceso** .

![Volcados de memoria](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766026.png)

Para más información, vea [Tome el control de registro y seguimiento en Windows Azure](https://msdn.microsoft.com/magazine/ff714589.aspx) y [Microsoft Azure Diagnostics. Parte 4: Componentes de registro personalizados y cambios de Azure Dignostics 1.3](http://justazure.com/microsoft-azure-diagnostics-part-4-custom-logging-components-azure-diagnostics-1-3-changes/).

## <a name="view-the-diagnostics-data"></a>Ver los datos de diagnóstico
Cuando haya recopilado los datos de diagnóstico para un servicio en la nube o una máquina virtual, podrá verlos.

### <a name="to-view-cloud-service-diagnostics-data"></a>Para ver los datos de diagnóstico del servicio en la nube
1. Implemente su servicio en la nube como de costumbre y luego ejecútelo.
2. Puede ver los datos de diagnóstico en un informe que Visual Studio genera o en tablas de su cuenta de almacenamiento. Para ver los datos en un informe, abra Cloud Explorer o el Explorador de servidores, abra el menú contextual del nodo para el rol que le interesa y luego seleccione **Ver datos de diagnóstico**.

    ![Ver datos de diagnóstico](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748912.png)

    Aparece un informe que muestra los datos disponibles.

    ![Informe de Microsoft Azure Diagnostics en Visual Studio](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796666.png)

    Si no se muestran los datos más recientes, puede que tenga que esperar a que transcurra el período de transferencia.

    Para actualizar inmediatamente los datos, seleccione el vínculo **Actualizar**. Para que los datos se actualicen automáticamente, seleccione un intervalo en el cuadro de lista desplegable **Actualizar automáticamente**. Para exportar los datos de error, seleccione el botón **Exportar a CSV** para crear un archivo de valores separados por comas que se pueda abrir en una hoja de cálculo de Excel.

    En Cloud Explorer o en el Explorador de servidores, abra la cuenta de almacenamiento asociada a la implementación.
3. Abra las tablas de diagnósticos en el visor de tablas y luego revise los datos que ha recopilado. Para los registros de IIS y los registros personalizados, puede abrir un contenedor de blobs. En la tabla siguiente se enumeran las tablas o contenedores de blobs que contienen los datos para los diferentes archivos de registro. Además de los datos para ese archivo de registro, las entradas de tabla contienen **EventTickCount**, **DeploymentId**, **Role** y **RoleInstance** para ayudarle a identificar qué máquina virtual y rol generó los datos y cuándo.

   | Datos de diagnóstico | DESCRIPCIÓN | Ubicación |
   | --- | --- | --- |
   | Registros de aplicación |Registros que su código genera llamando a métodos de la clase **System.Diagnostics.Trace**. |WADLogsTable |
   | Registros de eventos |Datos que proceden de los registros de eventos de Windows en las máquinas virtuales. Windows almacena información en estos registros, pero las aplicaciones y los servicios también los usan para informar de errores o información de registro. |WADWindowsEventLogsTable |
   | Contadores de rendimiento |Puede recopilar datos sobre cualquier contador de rendimiento que esté disponible en la máquina virtual. El sistema operativo ofrece contadores de rendimiento, que incluyen muchas estadísticas, como el tiempo del procesador y el uso de la memoria. |WADPerformanceCountersTable |
   | Registros de infraestructura |Registros que se generan desde la propia infraestructura de diagnóstico. |WADDiagnosticInfrastructureLogsTable |
   | Registros IIS |Registros que guardan solicitudes web. Si el servicio en la nube recibe una gran cantidad de tráfico, estos registros pueden ser largos. Es recomendable recopilar y almacenar estos datos solo cuando sea necesario. |Puede encontrar registros de solicitudes con error en el contenedor de blobs debajo de wad-iis-failedreqlogs en una ruta de acceso para esa implementación, rol e instancia. Puede encontrar registros completos en wad-iis-logfiles. Se crean entradas para cada archivo en la tabla WADDirectories. |
   | Volcados de memoria |Ofrece imágenes binarias del proceso del servicio en la nube (normalmente un rol de trabajo). |contenedor de blobs de wad-crush-dumps |
   | Archivos de registro personalizados |Registros de datos que ha predefinido. |Puede especificar en código la ubicación de archivos de registro personalizados en su cuenta de almacenamiento. Por ejemplo, puede especificar un contenedor de blobs personalizado. |
4. Si se truncan los datos de cualquier tipo, puede intentar aumentar el búfer para este tipo de datos o acortar el intervalo entre las transferencias de datos desde la máquina virtual a su cuenta de almacenamiento.
5. (Opcional) Purgar los datos de la cuenta de almacenamiento ocasionalmente para reducir los costos de almacenamiento generales.
6. Al realizar una implementación completa, se actualizará el archivo diagnostics.cscfg (.wadcfgx para Azure SDK 2.5) en Azure y su servicio en la nube recogerá cualquier cambio en la configuración de diagnóstico. Si en su lugar actualiza una implementación existente, no se actualizará el archivo .cscfg en Azure. No obstante, todavía puede cambiar la configuración de diagnóstico, siguiendo los pasos descritos en la siguiente sección. Para obtener más información sobre cómo realizar una implementación completa y actualizar una implementación existente, vea [Asistente Publicar aplicaciones de Azure](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-view-virtual-machine-diagnostics-data"></a>Para ver los datos de diagnóstico de máquina virtual
1. En el menú contextual para la máquina virtual, seleccione **Ver datos de diagnóstico**.

    ![Visualización de datos de diagnóstico en la máquina virtual de Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766027.png)

    Aparece el cuadro de diálogo **resumen de diagnóstico**.

    ![Resumen de diagnóstico de máquina virtual de Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796667.png)

    Si no se muestran los datos más recientes, puede que tenga que esperar a que transcurra el período de transferencia.

    Para actualizar inmediatamente los datos, seleccione el vínculo **Actualizar**. Para que los datos se actualicen automáticamente, seleccione un intervalo en el cuadro de lista desplegable **Actualizar automáticamente**. Para exportar los datos de error, seleccione el botón **Exportar a CSV** para crear un archivo de valores separados por comas que se pueda abrir en una hoja de cálculo de Excel.

## <a name="set-up-cloud-service-diagnostics-after-deployment"></a>Configuración del diagnóstico de servicio en la nube después de la implementación
Si está investigando un problema con un servicio en la nube que ya se está ejecutando, es posible que quiera recopilar datos que no ha especificado antes de implementar originalmente el rol. En este caso, puede comenzar a recopilar esos datos cambiando la configuración en el Explorador de servidores. Puede configurar el diagnóstico para una sola instancia o para todas las instancias de un rol, en función de si abre el cuadro de diálogo **Configuración de diagnóstico** en el menú contextual para la instancia o el rol. Si configura el nodo de rol, los cambios se aplicarán a todas las instancias. Si configura el nodo de instancia, los cambios que haga se aplican a esa instancia.

### <a name="to-set-up-diagnostics-for-a-running-cloud-service"></a>Para configurar los diagnósticos para un servicio en la nube en ejecución
1. En el Explorador de servidores, expanda el nodo **Cloud Services** y luego expanda la lista de nodos para buscar el rol o la instancia (o ambos) que quiere investigar.

    ![Configuración de diagnóstico](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748913.png)
2. En el menú contextual para un nodo de instancia o un nodo de rol, seleccione **Actualizar configuración de diagnóstico** y luego seleccione la configuración de diagnóstico que quiere recopilar.

    Para más información acerca de las opciones de configuración, consulte la sección **Configuración de orígenes de datos de diagnósticos** en este artículo. Para más información sobre cómo ver los datos de diagnósticos, consulte la sección **Visualización de los datos de diagnóstico** en este artículo.

    Si cambia la recopilación de datos en el Explorador de servidores, los cambios permanecen en vigor hasta que vuelve a implementar totalmente su servicio en la nube. Si utiliza la configuración de publicación predeterminada, los cambios no se sobrescriben. La configuración de publicación predeterminada es actualizar la implementación existente, en lugar de hacer de nuevo una implementación completa. Para asegurarse de que la configuración se borra durante la implementación, vaya a la pestaña **Configuración avanzada** del Asistente para publicación y desactive la casilla **Actualización de implementación**. Cuando vuelva a implementar con esa casilla desactivada, la configuración se revertirá a la del archivo .wadcfgx (o .wadcfg) según se establece a través del editor de **Propiedades** para el rol. Si actualiza su implementación, Azure conserva la configuración anterior.

## <a name="troubleshoot-azure-cloud-service-issues"></a>Solucionar problemas del servicio en la nube de Azure
Si experimenta problemas con sus proyectos de servicio en la nube, como un rol que se atasca en un estado "ocupado", recicla de manera repetida o genera un error de servidor interno, existen herramientas y técnicas que puede usar para diagnosticar y corregir el problema. Para ver ejemplos específicos de problemas comunes y soluciones, así como para obtener información general sobre los conceptos y herramientas que se usan para diagnosticar y corregir estos errores, vea [Datos de diagnóstico de proceso de PaaS de Azure](http://blogs.msdn.com/b/kwill/archive/2013/08/09/windows-azure-paas-compute-diagnostics-data.aspx).

## <a name="q--a"></a>Preguntas y respuestas
**¿Cuál es el tamaño del búfer y cuál debería ser?**

En cada instancia de máquina virtual, las cuotas limitan cuántos datos de diagnósticos se pueden almacenar en el sistema de archivos local. Además, especifique un tamaño de búfer para cada tipo de datos de diagnóstico que está disponible. Este tamaño de búfer actúa como una cuota individual para ese tipo de datos. Para determinar la cuota global y la cantidad de memoria que permanece, vea la parte inferior del cuadro de diálogo correspondiente al tipo de datos de diagnóstico. Si especifica búferes mayores o más tipos de datos, alcanzará la cuota global. Puede cambiar la cuota global modificando el archivo de configuración diagnostics.wadcfg o .wadcfgx. Los datos de diagnóstico se almacenan en el mismo sistema de archivos que los datos de la aplicación. Si la aplicación utiliza una gran cantidad de espacio en disco, no debería aumentar la cuota de diagnóstico total.

**¿Cuál es el período de transferencia y cuál debería ser?**

El período de transferencia es el tiempo que transcurre entre las capturas de datos. Tras cada período de transferencia, los datos se mueven desde el sistema de archivos local de una máquina virtual a las tablas de su cuenta de almacenamiento. Si la cantidad de datos que se recopilan supera la cuota antes del final de un período de transferencia, se descartarán los datos más antiguos. Si pierde datos porque superan el tamaño del búfer o la cuota global, puede ser aconsejable reducir el período de transferencia.

**¿En qué zona horaria están las marcas de tiempo?**

Las marcas de tiempo se encuentran en la zona horaria local del centro de datos que hospeda el servicio en la nube. Se usan las siguientes tres columnas de marca de tiempo en las tablas de registro:

* **PreciseTimeStamp**: marca de tiempo de ETW del evento. Es decir, el tiempo en que se registra el evento del cliente.
* **TIMESTAMP**: valor de **PreciseTimeStamp** redondeado a la baja hasta el límite de la frecuencia de carga. Por ejemplo, si su frecuencia de carga es de 5 minutos y la hora del evento es 00:17:12, TIMESTAMP es 00:15:00.
* **Timestamp**: marca de tiempo en que se creó la entidad en la tabla de Azure.

**¿Cómo administrar los costos al recopilar información de diagnóstico?**

La configuración predeterminada (**Nivel de registro** establecido en **Error** y **Período de transferencia** establecido en **1 minuto**) está diseñada para minimizar los costos. Los costos de proceso aumentarán si recopila más datos de diagnóstico o disminuye el período de transferencia. No recopile más datos de los que necesite y no olvide deshabilitar la colección de datos cuando ya no la necesite. Siempre puede habilitarlo de nuevo, incluso en tiempo de ejecución, como se ha descrito anteriormente en este artículo.

**¿Cómo recopilo registros de solicitudes con error de IIS?**

De forma predeterminada, IIS no recopila registros de solicitud con error. Puede configurar IIS para recopilar registros de solicitudes con error editando el archivo web.config para su rol web.

**No estoy obteniendo información de seguimiento desde métodos RoleEntryPoint como OnStart. ¿Qué ocurre?**

A los métodos de **RoleEntryPoint** se les llama en el contexto de WAIISHost.exe, no en IIS. No se aplica la información de configuración de archivo web.config que normalmente habilita el seguimiento. Para resolver este problema, agregue un archivo .config a su proyecto de rol web y asigne un nombre al archivo que coincida con el ensamblado de salida que contiene el código **RoleEntryPoint**. En el proyecto de rol web predeterminado, el nombre del archivo .config debería ser WAIISHost.exe.config. Agregue las líneas siguientes a este archivo:

```xml
<system.diagnostics>
  <trace>
      <listeners>
          <add name “AzureDiagnostics” type=”Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener”>
              <filter type=”” />
          </add>
      </listeners>
  </trace>
</system.diagnostics>
```

En la ventana **Propiedades**, establezca la propiedad **Copiar en el directorio de salida** en **Copiar siempre**.

## <a name="next-steps"></a>Pasos siguientes
Para más información sobre el registro de diagnósticos de Azure, consulte [Habilitación de diagnósticos en Azure Cloud Services y máquinas virtuales](/azure/cloud-services/cloud-services-dotnet-diagnostics) y [Habilitación del registro de diagnóstico para Web Apps en Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).
