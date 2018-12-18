---
title: Configuración de diagnósticos para Azure Cloud Services y virtual machines | Microsoft Docs
description: Obtenga información sobre cómo configurar diagnósticos para depurar los servicios de Azure en la nube y máquinas virtuales (VM) en Visual Studio.
author: mikejo5000
manager: douge
ms.assetid: e70cd7b4-6298-43aa-adea-6fd618414c26
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 06/28/2018
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 4448825c5d443887833a405aab14d2243a0e5216
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003075"
---
# <a name="set-up-diagnostics-for-azure-cloud-services-and-virtual-machines"></a>Configuración de diagnósticos para Azure Cloud Services y máquinas virtuales
Si necesita solucionar problemas de una máquina virtual o un servicio de nube de Azure, puede usar Visual Studio para configurar más fácilmente diagnósticos de Azure. Diagnósticos de capturan de datos del sistema y datos de registro en las máquinas virtuales y las instancias de máquinas virtuales que ejecutan el servicio en la nube. Datos de diagnóstico se transfieren a una cuenta de almacenamiento que elija. Para obtener más información sobre los diagnósticos de registro en Azure, consulte [habilitar el registro de diagnóstico para aplicaciones Web en Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

En este artículo, se muestra cómo usar Visual Studio para activar y configurar Azure Diagnostics, tanto antes como después de la implementación. Obtenga información sobre cómo ver la información que se recopila, cómo seleccionar los tipos de información de diagnóstico para recopilar y cómo configurar diagnósticos en Azure virtual machines.

Puede usar una de las opciones siguientes para configurar diagnósticos de Azure:

* Cambiar la configuración de diagnóstico en el **configuración de diagnóstico** cuadro de diálogo de Visual Studio. La configuración se guarda en un archivo denominado diagnostics.wadcfgx (en Azure SDK 2.4 y versiones anteriores, el archivo se llama diagnostics.wadcfg). También puede modificar directamente el archivo de configuración. Si actualiza manualmente el archivo, lo cambios de configuración surten efecto la próxima vez que implemente la nube de servicio en Azure o ejecutar el servicio en el emulador.
* Use Cloud Explorer o el Explorador de servidores en Visual Studio para cambiar la configuración de diagnósticos para un servicio en la nube o máquina virtual que se está ejecutando.

## <a name="azure-sdk-26-diagnostics-changes"></a>Cambios de diagnóstico de Azure SDK 2.6
Los siguientes cambios se aplican a Azure SDK 2.6 y versiones posteriores proyectos en Visual Studio:

* El emulador local ahora es compatible con los diagnósticos. Esto significa que puede recopilar datos de diagnóstico y asegurarse de que la aplicación crea los seguimientos correctos mientras desarrolla y prueba en Visual Studio. La cadena de conexión `UseDevelopmentStorage=true` activa de recopilación de datos de diagnóstico mientras se ejecuta el proyecto de servicio en la nube en Visual Studio mediante el emulador de almacenamiento de Azure. Todos los datos de diagnóstico se recopilan en la cuenta de almacenamiento de almacenamiento de desarrollo.
* La cadena de conexión de cuenta de almacenamiento de diagnóstico `Microsoft.WindowsAzure.Plugins.Diagnostics.ConnectionString` se almacena en el archivo de configuración (.cscfg) de servicio. En Azure SDK 2.5, la cuenta de almacenamiento de diagnóstico se especifica en el archivo diagnostics.wadcfgx.

La cadena de conexión funciona de forma distinta en algunos aspectos clave en Azure SDK 2.6 y versiones posteriores, en comparación con Azure SDK 2.4 y versiones anteriores:

* En Azure SDK 2.4 y versiones anteriores, la cadena de conexión se utiliza como tiempo de ejecución mediante el complemento de diagnóstico para obtener la información de cuenta de almacenamiento para la transferencia de registros de diagnóstico.
* En Azure SDK 2.6 y versiones posteriores, Visual Studio utiliza la cadena de conexión de diagnóstico para configurar la extensión de diagnósticos de Azure con la información de cuenta de almacenamiento adecuada durante la publicación. Puede usar la cadena de conexión para definir las cuentas de almacenamiento diferentes para distintas configuraciones del servicio que usa Visual Studio durante la publicación. Sin embargo, dado que el complemento de diagnóstico no está disponible después de Azure SDK 2.5, no se puede configurar en el archivo .cscfg por sí solo la extensión de diagnósticos. Debe configurar la extensión por separado mediante herramientas como Visual Studio o PowerShell.
* Para simplificar el proceso de configuración de la extensión de diagnósticos con PowerShell, la salida del paquete de Visual Studio incluye el XML de configuración pública para la extensión de diagnósticos para cada rol. Visual Studio usa la cadena de conexión de diagnósticos para rellenar la información de cuenta de almacenamiento en la configuración pública. Los archivos de configuración públicos se crean en la carpeta de extensiones. Los archivos de configuración pública usan el patrón de nomenclatura PaaSDiagnostics. &lt;nombre de la función\>. PubConfig.xml. Cualquier implementación basada en PowerShell puede usar este patrón para asignar cada configuración a un rol.
* El [portal Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040) usa la cadena de conexión en el archivo .cscfg para tener acceso a los datos de diagnóstico. Los datos aparecen en la **supervisión** ficha. La cadena de conexión se requiere para establecer el servicio de datos de supervisión detallada se muestra en el portal.

## <a name="migrate-projects-to-azure-sdk-26-and-later"></a>Migración de proyectos a Azure SDK 2.6 y versiones posteriores
Al migrar desde Azure SDK 2.5 a Azure SDK 2.6 o versiones posteriores, si tenía una cuenta de almacenamiento de diagnósticos especificada en el archivo .wadcfgx, la cuenta de almacenamiento permanece en ese archivo. Para aprovechar la flexibilidad de usar cuentas de almacenamiento diferentes para distintas configuraciones de almacenamiento, agregue manualmente la cadena de conexión a su proyecto. Si está migrando un proyecto de Azure SDK 2.4 o anterior a Azure SDK 2.6, se conservan las cadenas de conexión de diagnóstico. Sin embargo, tenga en cuenta los cambios en cómo se tratan las cadenas de conexión en Azure SDK 2.6, se describe en la sección anterior.

### <a name="how-visual-studio-determines-the-diagnostics-storage-account"></a>Modo en que Visual Studio determina la cuenta de almacenamiento de diagnósticos
* Si se especifica una cadena de conexión de diagnóstico en el archivo .cscfg, Visual Studio la usa para configurar la extensión de diagnóstico durante la publicación y al generar los archivos XML de configuración pública durante el empaquetado.
* Si no se especifica una cadena de conexión de diagnóstico en el archivo .cscfg, Visual Studio vuelve a utilizar la cuenta de almacenamiento que se especifica en el archivo .wadcfgx para configurar la extensión de diagnósticos para la publicación y para generar el XML de configuración pública archivos durante el empaquetado.
* La cadena de conexión de diagnóstico en el archivo .cscfg tiene prioridad sobre la cuenta de almacenamiento en el archivo .wadcfgx. Si es una cadena de conexión de diagnósticos especificada en el archivo .cscfg, Visual Studio usa esa cadena de conexión y omite la cuenta de almacenamiento en .wadcfgx.

### <a name="what-does-the-update-development-storage-connection-strings-check-box-do"></a>¿Qué hace la casilla de verificación "Actualizar cadenas de conexión de almacenamiento de desarrollo"?
El **actualizar cadenas de conexión de almacenamiento de desarrollo para diagnóstico y almacenamiento en caché con las credenciales de cuenta de almacenamiento de Microsoft Azure al publicar en Microsoft Azure** casilla de verificación es una manera cómoda de actualizar cualquier almacenamiento de desarrollo las cadenas de conexión de cuenta con la cuenta de almacenamiento de Azure que especifique durante la publicación.

Por ejemplo, si selecciona esta casilla de verificación y la cadena de conexión de diagnóstico especifica `UseDevelopmentStorage=true`, al publicar el proyecto en Azure, Visual Studio actualiza automáticamente la cadena de conexión de diagnóstico con la cuenta de almacenamiento que especificó en el Asistente para publicación. Sin embargo, si se especificó una cuenta de almacenamiento real como la cadena de conexión de diagnóstico, se usa esa cuenta.

## <a name="diagnostics-functionality-differences-in-azure-sdk-24-and-earlier-vs-azure-sdk-25-and-later"></a>Diferencias de funcionalidad de diagnóstico en Azure SDK 2.4 y versiones anteriores frente a. Azure SDK 2.5 y versiones posterior
Si va a actualizar el proyecto de Azure SDK 2.4 y versiones anteriores a Azure SDK 2.5 o posterior, tenga en cuenta las siguientes diferencias de funcionalidad de diagnóstico:

* **Las API de configuración están obsoletas**. Configuración mediante programación del diagnóstico está disponible en Azure SDK 2.4 y anteriores, pero está en desuso en Azure SDK 2.5 y versiones posteriores. Si la configuración de diagnóstico está definida actualmente en el código, debe volver a configurar esa configuración desde el principio en el proyecto migrado para el diagnóstico siga funcionando. El archivo de configuración de diagnósticos para Azure SDK 2.4 es diagnostics.wadcfg. El archivo de configuración de diagnósticos para Azure SDK 2.5 y versiones posteriores es Diagnostics.wadcfg.
* **Se pueden configurar diagnósticos para aplicaciones de servicio en la nube en el nivel de rol**. En Azure SDK 2.5 y versiones posteriores, no se puede configurar diagnósticos para aplicaciones de servicio en la nube en el nivel de instancia.
* **Cada vez que implementa la aplicación, se actualiza la configuración de diagnóstico**. Esto puede provocar problemas de paridad si cambia la configuración de diagnóstico desde el Explorador de servidores de Visual Studio y, a continuación, volver a implementar la aplicación.
* **En Azure SDK 2.5 y versiones posteriores, los volcados de memoria se configuran en el archivo de configuración de diagnóstico y no en el código**. Si tiene volcados de memoria configurados en el código, debe transferir manualmente la configuración del código al archivo de configuración. Los volcados de memoria no se transfieren durante la migración a Azure SDK 2.6.

## <a name="turn-on-diagnostics-in-cloud-service-projects-before-you-deploy-them"></a>Activar los diagnósticos en proyectos de servicio en la nube antes de implementarlos
En Visual Studio, puede recopilar datos de diagnóstico para roles que se ejecutan en Azure cuando se ejecuta el servicio en el emulador antes de la implementación. Todos los cambios de configuración de diagnóstico en Visual Studio se guardan en el archivo de configuración diagnostics.wadcfgx. Esta configuración especifica la cuenta de almacenamiento donde se guardan los datos de diagnóstico cuando implementa su servicio en la nube.

[!INCLUDE [cloud-services-wad-warning](./includes/cloud-services-wad-warning.md)]

### <a name="to-turn-on-diagnostics-in-visual-studio-before-deployment"></a>Para activar los diagnósticos en Visual Studio antes de la implementación

1. En el menú contextual para el rol, seleccione **propiedades**. En el rol **propiedades** cuadro de diálogo, seleccione el **configuración** ficha.
2. En el **diagnósticos** sección, asegúrese de que el **habilitar diagnósticos** casilla está activada.
   
    ![Acceder a la opción Habilitar diagnósticos](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796660.png)
3. Para especificar la cuenta de almacenamiento para los datos de diagnóstico, seleccione el botón de puntos suspensivos (...).
   
    ![Especifique la cuenta de almacenamiento para usar](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796661.png)
4. En el **crear cadena de conexión de almacenamiento** cuadro de diálogo, especifique si desea conectarse mediante el emulador de almacenamiento de Azure, una suscripción de Azure o credenciales escritas manualmente.
   
    ![Cuadro de diálogo de cuenta de almacenamiento](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796662.png)
   
   * Si selecciona **emulador de Microsoft Azure storage**, la cadena de conexión se establece en `UseDevelopmentStorage=true`.
   * Si selecciona **su suscripción**, puede seleccionar la suscripción de Azure que desea usar y escriba un nombre de cuenta. Para administrar las suscripciones de Azure, seleccione **administrar cuentas**.
   * Si selecciona **credenciales escritas manualmente**, escriba el nombre y la clave de la cuenta de Azure que desea usar.
5. Para ver el **configuración de diagnóstico** cuadro de diálogo, seleccione **configurar**. Excepto para **General** y **los directorios de registro**, cada pestaña representa un origen de datos de diagnóstico que se puede recopilar. El valor predeterminado **General** ficha ofrece el diagnóstico siguiente opciones de recopilación de datos: **solo errores**, **toda la información de**, y **plan personalizado**. El valor predeterminado **solo errores** opción usa la menor cantidad de almacenamiento, porque no transfiere advertencias o mensajes de seguimiento. El **toda la información de** opción transfiere la información más, usa el máximo almacenamiento y, por lo tanto, es la opción más cara.

   > [!NOTE]
   > Tamaño mínimo admitido de "Cuota de disco en MB" es 4GB. Sin embargo, si va a recopilar volcados de memoria, aumentarlo a un valor superior a 10GB.
   >
  
    ![Habilitar la configuración y diagnóstico de Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
6. En este ejemplo, seleccione el **plan personalizado** opción, para que pueda personalizar los datos recopilados.
7. En el **Disková Kvóta v MB** cuadro, puede establecer la cantidad de espacio para asignar en su cuenta de almacenamiento de datos de diagnóstico. Puede cambiar o aceptar el valor predeterminado.
8. En cada pestaña de datos de diagnóstico que se van a recopilar, seleccione el **habilitar la transferencia de \<tipo registro\>**  casilla de verificación. Por ejemplo, si desea recopilar registros de aplicación, en el **los registros de aplicación** ficha, seleccione el **habilitar la transferencia de registros de aplicación** casilla de verificación. Además, especifique cualquier otra información requerida por cada tipo de datos de diagnóstico. Para obtener información de configuración para cada pestaña, vea la sección **configurar orígenes de datos de diagnóstico** más adelante en este artículo. 
9. Después de habilitar la colección de todos los datos de diagnóstico que desea, seleccione **Aceptar**.
10. Ejecute el proyecto de servicio de nube de Azure en Visual Studio como de costumbre. Si usa la aplicación, la información del registro que habilitó se guarda en la cuenta de almacenamiento de Azure que especificó.

## <a name="turn-on-diagnostics-on-azure-virtual-machines"></a>Activar diagnósticos en máquinas virtuales de Azure
En Visual Studio, puede recopilar datos de diagnóstico para máquinas virtuales de Azure.

### <a name="to-turn-on-diagnostics-on-azure-virtual-machines"></a>Para activar los diagnósticos en Azure virtual machines

1. En el Explorador de servidores, seleccione el nodo de Azure y, a continuación, conectarse a su suscripción de Azure si aún no está conectado.
2. Expanda el **máquinas virtuales** nodo. Puede crear una nueva máquina virtual, o seleccione un nodo existente.
3. En el menú contextual para la máquina virtual que desee, seleccione **configurar**. Aparece el cuadro de diálogo de configuración de máquina virtual.
   
    ![Configurar una máquina virtual de Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796663.png)
4. Si aún no está instalado, agregue la extensión de diagnósticos de Microsoft Monitoring Agent. Con esta extensión, puede recopilar datos de diagnóstico para la máquina virtual de Azure. En **extensiones instaladas**, en el **seleccionar una extensión disponible** cuadro de lista desplegable, seleccione **diagnósticos de Microsoft Monitoring Agent**.
   
    ![Instalar una extensión de máquina virtual de Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766024.png)
   
    > [!NOTE]
   > Otras extensiones de diagnóstico están disponibles para las máquinas virtuales. Para obtener más información, consulte [extensiones de máquina Virtual y las características de Windows](https://docs.microsoft.com/azure/virtual-machines/windows/extensions-features).
   > 
   > 
5. Para agregar la extensión y ver su **configuración de diagnóstico** cuadro de diálogo, seleccione **agregar**.
6. Para especificar una cuenta de almacenamiento, seleccione **configurar**y, a continuación, seleccione **Aceptar**.
   
    Cada pestaña (excepto para **General** y **los directorios de registro**) representa un origen de datos de diagnóstico que se puede recopilar.
   
    ![Habilitar la configuración y diagnóstico de Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
   
    La pestaña predeterminada, **General**, ofrece las siguientes opciones de recopilación de datos de diagnóstico: **solo errores**, **toda la información de**, y **plan personalizado**. La opción predeterminada, **solo errores**, toma la menor cantidad de almacenamiento porque no transfiere advertencias o mensajes de seguimiento. El **toda la información de** opción transfiere la mayor cantidad de información y es, por lo tanto, la opción más cara en términos de almacenamiento.
7. En este ejemplo, seleccione el **plan personalizado** opción para que pueda personalizar los datos recopilados.
8. El **Disková Kvóta v MB** cuadro especifica la cantidad de espacio que desea asignar en la cuenta de almacenamiento de datos de diagnóstico. Si desea que se puede cambiar el valor predeterminado.
9. En cada pestaña de datos de diagnóstico van a recopilar, seleccione su **habilitar la transferencia de \<tipo registro\>**  casilla de verificación.
   
    Por ejemplo, si desea recopilar registros de aplicación, seleccione la **habilitar la transferencia de registros de aplicación** casilla de verificación en la **los registros de aplicación** ficha. Además, especifique cualquier otra información necesaria para cada tipo de datos de diagnóstico. Para obtener información de configuración para cada pestaña, vea la sección **configurar orígenes de datos de diagnóstico** más adelante en este artículo.
10. Después de habilitar la colección de todos los datos de diagnóstico que desee, seleccione **Aceptar**.
11. Guarde el proyecto actualizado.
    
    Un mensaje en el **Microsoft Azure Activity Log** ventana indica que la máquina virtual se ha actualizado.

## <a name="set-up-diagnostics-data-sources"></a>Configurar orígenes de datos de diagnóstico
Después de habilitar la recopilación de datos de diagnóstico, puede elegir exactamente qué orígenes de datos que van a recopilar y qué información se recopila. Las secciones siguientes describen las fichas de la **configuración de diagnóstico** cuadro de diálogo y significa que cada opción de configuración.

### <a name="application-logs"></a>Registros de aplicación
Los registros de aplicación tienen información de diagnóstico producidos por una aplicación web. Si quiere capturar registros de aplicaciones, seleccione la **habilitar la transferencia de registros de aplicación** casilla de verificación. Para aumentar o disminuir el intervalo entre la transferencia de registros de aplicación a la cuenta de almacenamiento, cambie el **período de transferencia (min)** valor. También puede cambiar la cantidad de información capturada en el registro estableciendo el **nivel de registro** valor. Por ejemplo, seleccione **detallado** para obtener más información, o seleccione **crítico** para capturar solo los errores críticos. Si tiene un proveedor de diagnósticos específico que emite registros de aplicación, puede capturar los registros agregando el GUID del proveedor en el **GUID de proveedor** cuadro.

  ![Registros de aplicación](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758145.png)

Para obtener más información sobre los registros de aplicación, consulte [habilitar el registro de diagnóstico para aplicaciones Web en Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="windows-event-logs"></a>Registros de eventos de Windows
Para capturar los registros de eventos de Windows, seleccione el **habilitar la transferencia de registros de eventos de Windows** casilla de verificación. Para aumentar o disminuir el intervalo entre la transferencia de registros de eventos a la cuenta de almacenamiento, cambie el **período de transferencia (min)** valor. Active las casillas para los tipos de eventos que desea realizar un seguimiento.

![Registros de eventos](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796664.png)

Si usa Azure SDK 2.6 o posterior y desea especificar un origen de datos personalizado, escríbalo en el **\<el nombre del origen de datos\>** cuadro de texto y, a continuación, seleccione **agregar**. El origen de datos se agrega al archivo diagnostics.cfcfg.

Si usa Azure SDK 2.5 y desea especificar un origen de datos personalizado, puede agregarlo a la `WindowsEventLog` archivo sección de diagnostics.wadcfgx, como en el ejemplo siguiente:

```
<WindowsEventLog scheduledTransferPeriod="PT1M">
   <DataSource name="Application!*" />
   <DataSource name="CustomDataSource!*" />
</WindowsEventLog>
```
### <a name="performance-counters"></a>Contadores de rendimiento
Información del contador de rendimiento puede ayudarle a localizar los cuellos de botella del sistema y optimizar el rendimiento del sistema y aplicación. Para obtener más información, consulte [crear y usar contadores de rendimiento en una aplicación de Azure](https://msdn.microsoft.com/library/azure/hh411542.aspx). Para capturar los contadores de rendimiento, seleccione el **habilitar la transferencia de contadores de rendimiento** casilla de verificación. Para aumentar o disminuir el intervalo entre la transferencia de registros de eventos a la cuenta de almacenamiento, cambie el **período de transferencia (min)** valor. Seleccione las casillas de los contadores de rendimiento que desea realizar un seguimiento.

![Contadores de rendimiento](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758147.png)

Para realizar un seguimiento de un contador de rendimiento que no aparece, escriba el contador de rendimiento mediante la sintaxis sugerida. y, a continuación, seleccione **agregar**. El sistema operativo en la máquina virtual determina qué contadores de rendimiento que puede realizar un seguimiento. Para obtener más información sobre la sintaxis, vea [especificar una ruta de acceso de contador](https://msdn.microsoft.com/library/windows/desktop/aa373193.aspx).

### <a name="infrastructure-logs"></a>Registros de infraestructura
Los registros de infraestructura tienen información sobre la infraestructura de diagnóstico de Azure, el módulo RemoteAccess y el módulo RemoteForwarder. Para recopilar información sobre los registros de infraestructura, seleccione el **habilitar la transferencia de registros de infraestructura** casilla de verificación. Para aumentar o disminuir el intervalo entre la transferencia de registros de infraestructura a la cuenta de almacenamiento, cambie el **período de transferencia (min)** valor.

![Registros de infraestructura de diagnóstico](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758148.png)

Para obtener más información, consulte [recopilar datos de registro mediante Diagnósticos de Azure](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="log-directories"></a>Directorios de registro
Directorios de registro tienen datos recopilados de los directorios de registro para las solicitudes de Internet Information Services (IIS), las solicitudes con error o carpetas que elija. Para capturar los directorios de registro, seleccione el **habilitar la transferencia de directorios de registro** casilla de verificación. Para aumentar o disminuir el intervalo entre la transferencia de registros a la cuenta de almacenamiento, cambie el **período de transferencia (min)** valor.

Active las casillas de los registros que se van a recopilar, como **los registros de IIS** y **solicitudes con error** registros. Se proporcionan nombres de contenedor de almacenamiento de forma predeterminada, pero puede cambiar los nombres.

Puede capturar registros desde cualquier carpeta. Especifique la ruta de acceso en el **registro del directorio absoluto** sección y, a continuación, seleccione **Agregar directorio**. Los registros se capturan en los contenedores especificados.

![Directorios de registro](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796665.png)

### <a name="etw-logs"></a>Registros de ETW
Si usas [seguimiento de eventos para Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) (ETW) y quiere capturar registros de ETW, seleccione el **habilitar la transferencia de registros de ETW** casilla de verificación. Para aumentar o disminuir el intervalo entre la transferencia de registros a la cuenta de almacenamiento, cambie el **período de transferencia (min)** valor.

Los eventos se capturan desde orígenes de eventos y manifiestos de eventos que especifique. Para especificar un origen de eventos, en el **orígenes de eventos** sección, escriba un nombre y, a continuación, seleccione **agregar origen de evento**. De forma similar, puede especificar un manifiesto de evento en el **manifiestos de eventos** sección y, a continuación, seleccione **agregar manifiesto de evento**.

![Registros de ETW](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766025.png)

El marco de ETW se admite en ASP.NET a través de clases en el [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) espacio de nombres. El espacio de nombres de Microsoft.WindowsAzure.Diagnostics, que hereda y extiende estándar [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) clases, habilita el uso de [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) como un registro marco de trabajo en el entorno de Azure. Para obtener más información, consulte [tome el control de registro y seguimiento en Microsoft Azure](https://msdn.microsoft.com/magazine/ff714589.aspx) y [habilitar diagnósticos en Azure Cloud Services y virtual machines](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="crash-dumps"></a>Los volcados de memoria
Para capturar información acerca de cuándo se bloquea una instancia de rol, seleccione el **Habilitar transferencia de volcados** casilla de verificación. (Dado que ASP.NET controla la mayoría de las excepciones, esto es generalmente útil para roles de trabajo.) Para aumentar o disminuir el porcentaje de espacio de almacenamiento dedicado a los volcados de memoria, cambiar el **cuota de directorio (%)** valor. Puede cambiar el contenedor de almacenamiento donde se almacenan los volcados de memoria y seleccione si quiere capturar un **completa** o **Mini** volcado de memoria.

Los procesos que se está realizando el seguimiento se muestran en la captura de pantalla siguiente. Active las casillas para los procesos que desea capturar. Para agregar otro proceso a la lista, escriba el nombre del proceso y, a continuación, seleccione **Agregar proceso**.

![Los volcados de memoria](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766026.png)

Para obtener más información, consulte [tome el control de registro y seguimiento en Microsoft Azure](https://msdn.microsoft.com/magazine/ff714589.aspx) y [Microsoft Azure Diagnostics parte 4: componentes de registro personalizados y cambios de Azure Diagnostics 1.3](http://justazure.com/microsoft-azure-diagnostics-part-4-custom-logging-components-azure-diagnostics-1-3-changes/).

## <a name="view-the-diagnostics-data"></a>Ver los datos de diagnóstico
Cuando haya recopilado los datos de diagnóstico para una máquina virtual o servicio en la nube, puede verlo.

### <a name="to-view-cloud-service-diagnostics-data"></a>Para ver los datos de diagnóstico de servicio en la nube
1. Implemente su servicio en la nube como de costumbre y, a continuación, ejecútelo.
2. Puede ver los datos de diagnóstico en un informe que genera Visual Studio o en tablas en la cuenta de almacenamiento. Para ver los datos en un informe, abra Cloud Explorer o el Explorador de servidores, abra el menú contextual del nodo para el rol que desee y, a continuación, seleccione **ver datos de diagnóstico**.
   
    ![Ver datos de diagnóstico](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748912.png)
   
    Aparece un informe que muestra los datos disponibles.
   
    ![Informe de Microsoft Azure Diagnostics en Visual Studio](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796666.png)
   
    Si no se muestran los datos más recientes, podría tener que esperar a que transcurra el período de transferencia.
   
    Para actualizar inmediatamente los datos, seleccione el **actualizar** vínculo. Para que los datos se actualicen automáticamente, seleccione un intervalo en el **actualización automática** cuadro de lista desplegable. Para exportar los datos de error, seleccione el **exportar a CSV** botón para crear un archivo de valores separados por comas que se puede abrir en una hoja de cálculo de Excel.
   
    En Cloud Explorer o el Explorador de servidores, abra la cuenta de almacenamiento que está asociado con la implementación.
3. Abra las tablas de diagnósticos en el Visor de tablas y, a continuación, revise los datos que recopilan. Para los registros de IIS y registros personalizados, puede abrir un contenedor de blobs. En la tabla siguiente se enumera las tablas o contenedores de blobs que contienen los datos para los archivos de registro diferentes. Además de los datos para ese archivo de registro que contienen las entradas de tabla **EventTickCount**, **DeploymentId**, **rol**, y **RoleInstance** , que le ayudarán a identificar qué máquina virtual y rol generan los datos y cuándo. 
   
   | Datos de diagnóstico | Descripción | Ubicación |
   | --- | --- | --- |
   | Registros de aplicación |Los registros que su código genera llamando a métodos de la **System.Diagnostics.Trace** clase. |WADLogsTable |
   | Registros de eventos |Datos de los registros de eventos de Windows en las máquinas virtuales. Windows almacena información en estos registros, pero las aplicaciones y servicios también usan los registros para informar de errores o información de registro. |WADWindowsEventLogsTable |
   | Contadores de rendimiento |Puede recopilar datos sobre cualquier contador de rendimiento que está disponible en la máquina virtual. El sistema operativo ofrece contadores de rendimiento, que incluyen muchas estadísticas, como el tiempo de procesador y el uso de memoria. |WADPerformanceCountersTable |
   | Registros de infraestructura |Registros que se generan a partir de la propia infraestructura de diagnóstico. |WADDiagnosticInfrastructureLogsTable |
   | Registros de IIS |Registros que registran las solicitudes web. Si su servicio en la nube Obtiene una cantidad significativa de tráfico, estos registros pueden ser largos. Es una buena idea para recopilar y almacenar estos datos solo cuando lo necesite. |Puede encontrar registros de solicitudes con error en el contenedor de blobs debajo de wad-iis-failedreqlogs en una ruta de acceso para esa implementación, rol e instancia. Puede encontrar registros completos en wad-iis-logfiles. Las entradas para cada archivo se realizan en la tabla WADDirectories. |
   | Los volcados de memoria |Ofrece imágenes binarias del proceso del servicio en la nube (normalmente un rol de trabajo). |contenedor de blobs wad-crush-dumps |
   | Archivos de registro personalizados |Registros de datos que ha predefinido. |Puede especificar en el código de la ubicación de archivos de registro personalizado en su cuenta de almacenamiento. Por ejemplo, puede especificar un contenedor de blobs personalizado. |
4. Si se truncan los datos de cualquier tipo, puede intentar aumentar el búfer para los datos de tipo o acortar el intervalo entre las transferencias de datos de la máquina virtual en la cuenta de almacenamiento.
5. (Opcional) Purgar datos de la cuenta de almacenamiento ocasionalmente para reducir los costos generales de almacenamiento.
6. Al realizar una implementación completa, se actualiza el archivo diagnostics.cscfg (.wadcfgx para Azure SDK 2.5) en Azure y su servicio en la nube recoge cualquier cambio en la configuración de diagnóstico. Si actualiza una implementación existente en su lugar, no se actualiza el archivo .cscfg en Azure. Todavía puede cambiar la configuración de diagnóstico, no obstante, siguiendo los pasos descritos en la sección siguiente. Para obtener más información sobre cómo realizar una implementación completa y actualizar una implementación existente, consulte [asistente Publicar aplicación de Azure](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-view-virtual-machine-diagnostics-data"></a>Para ver los datos de diagnóstico de máquina virtual
1. En el menú contextual para la máquina virtual, seleccione **ver datos de diagnóstico**.
   
    ![Ver datos de diagnóstico en una máquina virtual de Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766027.png)
   
    El **resumen de diagnóstico** aparece el cuadro de diálogo.
   
    ![Resumen de diagnóstico de máquina virtual de Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796667.png)  
   
    Si no se muestran los datos más recientes, podría tener que esperar a que transcurra el período de transferencia.
   
    Para actualizar inmediatamente los datos, seleccione el **actualizar** vínculo. Para que los datos se actualicen automáticamente, seleccione un intervalo en el **actualización automática** cuadro de lista desplegable. Para exportar los datos de error, seleccione el **exportar a CSV** botón para crear un archivo de valores separados por comas que se puede abrir en una hoja de cálculo de Excel.

## <a name="set-up-cloud-service-diagnostics-after-deployment"></a>Configuración de diagnósticos de servicio de nube después de la implementación
Si está investigando un problema con un servicio en la nube que ya se está ejecutando, es posible que desea recopilar datos que no ha especificado antes de implementar originalmente el rol. En este caso, puede comenzar a recopilar esos datos cambiando la configuración en el Explorador de servidores. Puede configurar diagnósticos para una sola instancia o para todas las instancias de un rol, en función de si abre el **configuración de diagnóstico** cuadro de diálogo en el menú contextual para la instancia o el rol. Si configura el nodo de rol, los cambios que realice se aplican a todas las instancias. Si configura el nodo de la instancia, los cambios que realice solo se aplican a esa instancia.

### <a name="to-set-up-diagnostics-for-a-running-cloud-service"></a>Para configurar diagnósticos para un servicio en ejecución en la nube
1. En el Explorador de servidores, expanda el **servicios en la nube** nodo y, a continuación, expanda la lista de nodos para localizar el rol o instancia (o ambos) que desea investigar.
   
    ![Configurar los diagnósticos](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748913.png)
2. En el menú contextual para un nodo de instancia o rol, seleccione **actualizar valores de diagnóstico**y, a continuación, seleccione la configuración de diagnóstico que se va a recopilar.
   
    Para obtener información acerca de las opciones de configuración, consulte la sección **configurar orígenes de datos de diagnóstico** en este artículo. Para obtener información sobre cómo ver los datos de diagnóstico, consulte la sección **ver los datos de diagnóstico** en este artículo.
   
    Si cambia la recopilación de datos en el Explorador de servidores, los cambios se mantienen hasta que vuelva a implementar totalmente su servicio en la nube. Si utiliza el valor predeterminado la configuración de publicación, no se sobrescriben los cambios. El valor predeterminado de configuración de publicación es actualizar la implementación existente, en lugar de realizar una implementación completa. Para asegurarse de que la configuración se borra durante la implementación, vaya a la **configuración avanzada** pestaña del Asistente para publicación y, a continuación, desactive la **actualización de implementación** casilla de verificación. Cuando vuelve a implementar con esa casilla desactivada, la configuración revierte a en el archivo .wadcfgx (o .wadcfg) según establece el **propiedades** editor para el rol. Si actualiza su implementación, Azure conserva la configuración anterior.

## <a name="troubleshoot-azure-cloud-service-issues"></a>Solucionar problemas del servicio de nube de Azure
Si experimenta problemas con sus proyectos de servicio en la nube, como un rol que se atasca en un estado "ocupado", de manera repetida se recicla o produce un error interno del servidor, existen herramientas y técnicas que puede usar para diagnosticar y corregir el problema. Para obtener ejemplos específicos de problemas y soluciones comunes y para obtener información general de los conceptos y herramientas que puede usar para diagnosticar y corregir estos errores, vea [datos de diagnóstico de proceso de PaaS de Azure](http://blogs.msdn.com/b/kwill/archive/2013/08/09/windows-azure-paas-compute-diagnostics-data.aspx).

## <a name="q--a"></a>Preguntas y respuestas
**¿Qué es el tamaño del búfer, y qué tamaño debería ser?**

En cada instancia de máquina virtual, las cuotas limitan cuántos datos de diagnóstico se pueden almacenar en el sistema de archivos local. Además, especifique un tamaño de búfer para cada tipo de datos de diagnóstico que están disponibles. Este tamaño de búfer actúa como una cuota individual para ese tipo de datos. Para determinar la cuota global y la cantidad de memoria que permanece, vea la parte inferior del cuadro de diálogo para el tipo de datos de diagnóstico. Si especifica búferes mayores o más tipos de datos, alcanzará la cuota global. Puede cambiar la cuota global modificando el archivo de configuración diagnostics.wadcfg o wadcfgx. Los datos de diagnóstico se almacenan en el mismo sistema de archivos como datos de la aplicación. Si la aplicación utiliza una gran cantidad de espacio en disco, no debería aumentar la cuota de diagnóstico general.

**¿Qué es el período de transferencia y cuál debería ser?**

El período de transferencia es la cantidad de tiempo que transcurre entre los datos de captura. Tras cada período de transferencia, datos se mueven desde el sistema de archivos local en una máquina virtual en las tablas de la cuenta de almacenamiento. Si la cantidad de datos que se recopilan supera la cuota antes del final de un período de transferencia, se descartan los datos más antiguos. Si pierde datos porque superan el tamaño de búfer o la cuota global, es posible que desee reducir el período de transferencia.

**¿Qué zona horaria están las marcas de tiempo?**

Las marcas de tiempo se encuentran en la zona horaria local del centro de datos que hospeda el servicio en la nube. Se utilizan las siguientes columnas de marca de tiempo tres de las tablas de registro:

* **PreciseTimeStamp**: marca de tiempo ETW del evento. Es decir, la hora se registra el evento desde el cliente.
* **Marca de tiempo**: el valor de **PreciseTimeStamp** redondeado hacia abajo hasta el límite de frecuencia de carga. Por ejemplo, si su frecuencia de carga es 5 minutos y el evento hora 00:17:12, TIMESTAMP es 00:15:00.
* **Marca de tiempo**: la marca de tiempo en que se creó la entidad en la tabla de Azure.

**¿Cómo administrar los costos al recopilar información de diagnóstico?**

La configuración predeterminada (**nivel de registro** establecido en **Error**, y **período de transferencia** establecido en **1 minuto**) están diseñadas para minimizar los costos. Los costos de proceso aumenten al recopilar más datos de diagnóstico o disminuye el período de transferencia. No recopile más datos que necesita y no olvide deshabilitar la recopilación de datos cuando ya no lo necesita. Es siempre pueden habilitarlo de nuevo, incluso en tiempo de ejecución, como se describe anteriormente en este artículo.

**¿Cómo se puede recopilar registros de solicitudes con error de IIS y?**

De forma predeterminada, IIS no recopila registros de solicitudes con error. Puede configurar IIS para recopilar registros de solicitudes con error editando el archivo web.config para su rol web.

**No estoy obteniendo información de seguimiento desde métodos RoleEntryPoint como OnStart. ¿Qué ocurre?**

Los métodos de **RoleEntryPoint** se llaman en el contexto de WAIISHost.exe, no en IIS. La información de configuración en el archivo web.config que normalmente habilita el seguimiento no es aplicable. Para resolver este problema, agregue un archivo .config a su proyecto de rol web y asigne el nombre para que coincida con el ensamblado de salida que contiene el **RoleEntryPoint** código. En el proyecto de rol web de forma predeterminada, el nombre del archivo .config debería ser WAIISHost.exe.config. Agregue las líneas siguientes a este archivo:

```
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

En el **propiedades** ventana, establezca el **Copy to Output Directory** propiedad **copiar siempre**.

## <a name="next-steps"></a>Pasos siguientes
Para obtener más información sobre el registro de diagnósticos de Azure, consulte [habilitar diagnósticos en Azure Cloud Services y virtual machines](/azure/cloud-services/cloud-services-dotnet-diagnostics.md) y [habilitar el registro de diagnóstico para aplicaciones Web en Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

