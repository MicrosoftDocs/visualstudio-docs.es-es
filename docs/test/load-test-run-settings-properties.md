---
title: Parámetros de ejecución de pruebas de carga
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, run settings
ms.assetid: de10dabb-02ed-403b-9e6f-0b735524988c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: 73c561cf7f79345751b62b53ec3b7da4f74e2e52
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860210"
---
# <a name="load-test-run-settings-properties"></a>Propiedades de los parámetros de ejecución de las pruebas de carga

Los parámetros de ejecución de una prueba de carga determinan otras opciones de configuración, incluidas la duración de la prueba, el nivel de detalle de la colección de resultados y los conjuntos de contadores que se recopilan cuando se ejecuta la prueba. Puede crear y almacenar varios parámetros de ejecución para cada prueba de carga, y seleccionar una configuración determinada para utilizarla durante la ejecución de la prueba. Cuando se crea la prueba de carga mediante el **Asistente para prueba de carga nueva**, se agrega un parámetro de ejecución inicial a la prueba de carga.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

En las tablas siguientes se describen las diversas propiedades de los parámetros de ejecución de pruebas de carga. Puede modificar estas propiedades para cumplir los requisitos concretos de las pruebas de carga.

Para obtener más información, vea [Configurar los parámetros de ejecución de pruebas de carga](../test/configure-load-test-run-settings.md).

## <a name="general-properties"></a>Propiedades generales

|Propiedad.|de esquema JSON|
|-|----------------|
|**Descripción**|Una descripción de los parámetros de ejecución.|
|**Errores por tipo máximos**|El número máximo de errores por tipo que se van a guardar para la prueba de carga.<br /><br /> Puede aumentar este número si es preciso, pero al hacerlo también aumentará el tamaño y el tiempo de procesamiento del resultado de la prueba de carga.|
|**Direcciones URL de solicitud máximas notificadas**|Número máximo de direcciones URL únicas de solicitudes de pruebas de rendimiento web que se incluirán en el informe de esta prueba de carga.<br /><br /> Puede aumentar este número si es preciso, pero al hacerlo también aumentará el tamaño y el tiempo de procesamiento del resultado de la prueba de carga.|
|**Infracciones del umbral máximas**|El número máximo de infracciones del umbral que se van a guardar para esta prueba de carga.<br /><br /> Puede aumentar este número si es preciso, pero al hacerlo también aumentará el tamaño y el tiempo de procesamiento del resultado de la prueba de carga.|
|**Ejecutar pruebas unitarias en dominio de aplicación**|Valor booleano que determina si cada ensamblado de prueba unitaria se ejecutará en un dominio de aplicación independiente cuando la prueba de carga contenga pruebas unitarias. El valor predeterminado es True.<br /><br /> Si las pruebas unitarias no requieren un dominio de aplicación diferente o un archivo app.config para que funcionen correctamente, se ejecutarán de forma más rápida si establece el valor de esta propiedad en `False`.|
|**Name**|Nombre del parámetro de ejecución tal como aparece en el nodo **Parámetros de ejecución** del **Editor de pruebas de carga**.|
|**Nivel de validación**|Define el nivel superior de regla de validación que se ejecutará en una prueba de carga. Las reglas de validación se asocian a solicitudes de prueba de rendimiento web. Cada regla de validación tiene un nivel de validación asociado: **Alto**, **Medio** o **Bajo**. Este parámetro de ejecución de pruebas de carga especificará qué reglas de validación se ejecutarán mientras se realiza la prueba de rendimiento web en la prueba de carga. Por ejemplo, si este parámetro de ejecución se establece en **Medio**, se ejecutan todas las reglas de validación marcadas como **Medio** o **Bajo**.|

## <a name="logging-properties"></a>Propiedades de registro

|Propiedad.|de esquema JSON|
|-|----------------|
|**Máximos registros de prueba**|Especifica el número máximo de registros de prueba que se van a guardar para la prueba de carga. Cuando se alcance el valor especificado para el número máximo de registros de prueba, la prueba de carga dejará de recopilar registros. Por tanto, los registros se recopilarán al principio de la prueba, no al final. La ejecución de la prueba de carga continuará hasta que se complete.|
|**Frecuencia de guardado del registro para pruebas completadas**|Especifica la frecuencia con la que se escribirá el registro de prueba. El número indica que en el registro de prueba se guardará una prueba de cada número de pruebas especificado. Por ejemplo, si se especifica el valor diez, significa que se escribirá en el registro de prueba la décima, la vigésima, la trigésima, y así sucesivamente. Si se establece el valor en 0, se especifica que no se guardará ningún registro de prueba.|
|**Guardar registro si la prueba no es correcta**|Valor booleano que determina si se guardan registros de prueba si se produce un error en una prueba de carga. De manera predeterminada, es `True`.<br /><br /> Para obtener más información, vea [Cómo: Especificar si los errores de las pruebas se guardan en los registros de pruebas](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|

 Para obtener más información, vea [Modificar la configuración de registro de pruebas de carga](../test/modify-load-test-logging-settings.md).

## <a name="results-properties"></a>Propiedades de resultados

|Propiedad.|de esquema JSON|
|-|----------------|
|**Tipo de almacenamiento**|Manera de almacenar los contadores de rendimiento obtenidos en una prueba de carga. Las opciones son las siguientes:<br /><br /> -   **Base de datos**: necesita una base de datos SQL que tenga un **Almacén de resultados de pruebas de carga**.<br />-   **Ninguno**.|
|**Almacenamiento de detalles de tiempo**|Se usa para determinar qué detalles se almacenan en el **Almacén de resultados de pruebas de carga**. Hay tres valores disponibles:<br /><br /> -   **AllIndividualDetails**: recopila y almacena valores de tiempo individuales de cada prueba, transacción y página que se haya ejecutado o emitido durante la prueba de carga en el **Almacén de resultados de pruebas de carga**. Es necesario si piensa usar el **Diagrama de actividad del usuario virtual** del **Analizador de pruebas de carga**.<br />     Para obtener más información, vea [Analizar la actividad de usuario virtual de prueba de carga en la vista Detalles del Analizador de prueba de carga](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).<br />-   **None**: no recopila ningún valor de tiempo individual. Este es el valor predeterminado para Visual Studio 2013 Update 4 y versiones posteriores.<br />-   **StatisticsOnly**: recopila y almacena solamente estadísticas, en lugar de almacenar los valores de tiempo individuales de cada prueba, transacción y página que se haya ejecutado o emitido durante la prueba de carga en el **Almacén de resultados de pruebas de carga**.<br /><br /> Para obtener más información, vea [Cómo: Especificar la propiedad Almacenamiento de detalles de tiempo](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).|

## <a name="sql-tracing-properties"></a>Propiedades de seguimiento SQL

|Propiedad.|de esquema JSON|
|-|----------------|
|**Duración mínima de operaciones SQL de las que se realiza el seguimiento**|Duración mínima de una operación de SQL que capturará Seguimiento SQL, expresada en milisegundos. Por ejemplo, esto permite omitir operaciones que se completan rápidamente si se desea encontrar operaciones de SQL que son lentas bajo carga.|
|**Cadena de conexión de seguimiento SQL**|Cadena de conexión utilizada para obtener acceso a la base de datos de la que se realiza el seguimiento.|
|**Directorio de seguimiento SQL**|La ubicación del archivo de seguimiento SQL al finalizar el seguimiento. Este directorio debe tener permisos de escritura para SQL Server y permisos de lectura para el controlador.|
|**Seguimiento SQL habilitado**|Habilita la traza de las operaciones de SQL. El valor predeterminado es `False`.|

## <a name="test-iterations-properties"></a>Propiedades de iteraciones de prueba

|Propiedad.|de esquema JSON|
|-|----------------|
|**Iteraciones de prueba**|Especifica el número total de pruebas individuales que se ejecutarán antes de completarse la prueba de carga. Esta propiedad solo se aplica cuando la propiedad "Usar iteraciones de prueba" es `True`.|
|**Usar iteraciones de prueba**|Si Usar iteraciones de prueba es `True`, la prueba de carga se ejecutará hasta que el número de pruebas individuales completadas dentro de la prueba de carga alcance el número especificado por la propiedad "Iteraciones de prueba". En este caso, se omiten los valores de las opciones temporales: "Duración de la preparación", "Duración de la ejecución" y "Duración del enfriamiento". Si "Usar iteraciones de prueba" es `False`, se aplicarán todas las opciones de tiempo y se omitirá "Iteraciones de prueba".|

 Para obtener más información, vea [Cómo: Especificar el número de iteraciones de prueba en los parámetros de ejecución de una prueba de carga](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="timing-properties"></a>Propiedades de sincronización

|Propiedad.|de esquema JSON|
|-|----------------|
|**Duración del enfriamiento**|Duración del período de enfriamiento, expresado en formato de hh:mm:ss. Puede que algunas pruebas individuales de una prueba de carga sigan en ejecución cuando finalice la prueba de carga. Durante el período de enfriamiento, esas pruebas pueden continuar hasta completarse o hasta que finaliza dicho período. De manera predeterminada no se aplica un período de enfriamiento, y las pruebas individuales finalizan cuando lo hace la prueba de carga de acuerdo con el valor de Duración de la ejecución.|
|**Duración de la ejecución**|Duración de la prueba, en formato hh:mm:ss.|
|**Frecuencia de muestreo**|Intervalo en el que se capturarán valores de contador de rendimiento, en formato hh:mm:ss.<br /><br /> Para obtener más información, vea [Cómo: Especificar la frecuencia de muestreo](../test/how-to-specify-the-sample-rate-for-a-load-test.md).|
|**Duración de la preparación**|Período que transcurre desde que comienza la prueba hasta que empiezan a registrarse las muestras de datos, en formato hh:mm:ss. Se utiliza con frecuencia para cargar por pasos los usuarios virtuales hasta alcanzar cierto nivel de carga antes de registrar los valores de ejemplo. Los valores de muestra que se capturan antes de que concluya el período de preparación se muestran en el **Analizador de pruebas de carga**.|

## <a name="webtest-connections-properties"></a>Propiedades de conexiones WebTest

|Propiedad.|de esquema JSON|
|-|----------------|
|**Modelo de conexión de WebTest**|Controla el uso de conexiones del agente de la prueba de carga al servidor web para las pruebas de rendimiento web que se ejecutan dentro de una prueba de carga. Hay disponibles tres opciones de modelo de conexión de pruebas de rendimiento web:<br /><br /> - El modelo **Conexión por usuario** simula el comportamiento de un usuario que está usando un explorador real. Cuando se simula Internet Explorer 6 o Internet Explorer 7, cada usuario virtual que ejecuta una prueba de rendimiento web usa una o dos conexiones dedicadas al servidor web. La primera conexión se establece cuando se emite la primera solicitud en la prueba de rendimiento web. Se puede utilizar una segunda conexión cuando una página contiene más de una solicitud dependiente. Estas solicitudes se emiten en paralelo, usando las dos conexiones. Estas conexiones se reutilizan para solicitudes posteriores en la prueba de rendimiento web. Las conexiones se cierran cuando finaliza la prueba de rendimiento web. Una desventaja de este modelo es que el número de conexiones que se mantienen abiertas en el equipo agente podría ser alto (hasta dos veces la carga de usuarios). Por consiguiente, los recursos necesarios para admitir este elevado número de conexiones pueden limitar la carga de usuarios que se pueden controlar desde un único agente de prueba de carga. Cuando se simula Internet Explorer 8, se admiten seis conexiones simultáneas.<br />- El modelo **Grupo de conexiones** conserva los recursos en el agente de pruebas de carga al compartir conexiones al servidor web entre varios usuarios virtuales de la prueba de rendimiento web. Si la carga de usuarios es mayor que el tamaño del grupo de conexiones, las pruebas de rendimiento web ejecutadas por usuarios virtuales diferentes compartirán una conexión. Como consecuencia, podría ocurrir que una prueba de rendimiento web tuviera que esperar antes de emitir una solicitud mientras otra prueba de rendimiento web está utilizando la conexión. El contador de rendimiento de pruebas de carga Tiempo promedio de espera de conexión hace un seguimiento del tiempo promedio que debe esperar una prueba de rendimiento web antes de enviar una solicitud. Este número debe ser menor que el tiempo medio de respuesta para una página. De lo contrario, puede que el tamaño del grupo de conexiones sea demasiado pequeño.<br />- El modelo **Conexión por iteración de prueba** especifica el uso de conexiones dedicadas para cada iteración de prueba.|
|**Tamaño del grupo de conexiones WebTest**|Especifica el número máximo de conexiones que pueden realizarse entre el agente de la prueba de carga y el servidor Web. Solo se aplica al modelo **Grupo de conexiones**.|

##  <a name="change-run-setting-properties"></a>Cambiar las propiedades de los parámetros de ejecución
 Puede agregar más parámetros de ejecución a la prueba de carga con distintas configuraciones de propiedades para poder realizar la prueba de carga en condiciones diferentes. Por ejemplo, puede agregar una nueva configuración de pruebas y utilizar una velocidad de muestra diferente o especificar una duración más larga. Solo puede usar un parámetro de ejecución cada vez y debe especificar cuál desea usar marcándolo como activo. Como ejemplo, vea [Cómo: Seleccionar el parámetro de ejecución activo de una prueba de carga](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

### <a name="to-change-run-settings"></a>Para cambiar los parámetros de ejecución:

1.  Abra una prueba de carga.

2.  Expanda la carpeta **Parámetros de ejecución**.

3.  Elija un nodo de **Parámetros de ejecución**.

4.  En el menú **Ver**, elija la ventana **Propiedades**.

     Se muestra la ventana **Propiedades**, con las propiedades de los parámetros de ejecución seleccionados.

5.  Use la ventana **Propiedades** para cambiar los parámetros de ejecución. Por ejemplo, cambie la duración de ejecución a **00:05:00** para ejecutar la prueba durante cinco minutos.

    > [!NOTE]
    > Para obtener una lista completa de las propiedades de los parámetros de ejecución y sus descripciones, vea [Propiedades de los parámetros de ejecución de las pruebas de carga](../test/load-test-run-settings-properties.md).

6.  Cuando haya terminado de cambiar las propiedades, guarde la prueba de carga. En el menú **Archivo**, elija **Guardar**.

> [!NOTE]
> Las asignaciones de conjuntos de contadores también forman parte de los parámetros de ejecución. Para más información, consulte [Especificar los conjuntos de contadores y las reglas de umbral para equipos en una prueba de carga](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="see-also"></a>Vea también

- [Configurar los parámetros de ejecución de pruebas de carga](../test/configure-load-test-run-settings.md)