---
title: Usar el recopilador independiente de IntelliTrace | Microsoft Docs
ms.date: 07/30/2019
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.collectdataoutsideVS
helpviewer_keywords:
- IntelliTrace, debugging applications in production
ms.assetid: 1bde9807-8219-4a2a-a440-ac5ee5178159
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5349c08497bc52c32a4ffed30b74f2d3bd71e4e
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911309"
---
# <a name="using-the-intellitrace-stand-alone-collector-c-visual-basic"></a>Usar el recopilador independiente de IntelliTrace (C#, Visual Basic)

El **recolector independiente IntelliTrace** permite recopilar datos de diagnóstico de IntelliTrace para las aplicaciones en servidores de producción o en otros entornos sin instalar Visual Studio en el equipo de destino y sin cambiar el entorno del sistema de destino. El recolector independiente IntelliTrace funciona en aplicaciones web, de Sharepoint, de WPF y de Windows Forms. Cuando la recolección de datos haya terminado, basta con eliminar el recolector para desinstalarlo.

 Eche un vistazo a IntelliTrace en acción: [Recopilación y análisis de datos en un entorno de producción (vídeo de Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Collecting-and-analyzing-data-in-production)

> [!NOTE]
> Los mismos datos de IntelliTrace se pueden recopilar también para aplicaciones web y de Sharepoint que se ejecutan en equipos remotos; para ello, hay que usar **Microsoft Monitoring Agent** en modo **Trace** .
>
> Si el agente se ejecuta en modo **Monitor** , puede recopilar eventos relacionados con el rendimiento en los datos de IntelliTrace. El modo**Monitor** tiene un impacto en el rendimiento menos acusado que el modo **Trace** o el **recolector independiente IntelliTrace**. Microsoft Monitoring Agent sí modifica el entorno del sistema de destino cuando se instala. Vea [usar el Microsoft Monitoring Agent](../debugger/using-the-microsoft-monitoring-agent.md).
> El recopilador independiente de IntelliTrace no admite instantáneas de proceso.

 **Requisitos**

- .NET Framework 3,5 o superior

- Visual Studio Enterprise (y no las versiones Professional o Community) el equipo de desarrollo o en otro equipo para abrir los archivos .iTrace

  > [!NOTE]
  > Procure guardar los archivos de símbolos (.pdb). Para depurar con IntelliTrace y recorrer el código, debe tener los archivos de código fuente y los archivos de símbolos correspondientes. Vea [diagnosticar problemas después](../debugger/diagnose-problems-after-deployment.md)de la implementación.

  **Preguntas más frecuentes**

- [¿Qué aplicaciones funcionan con el recolector?](#WhatApps)

- [¿Cómo comenzar?](#GetStarted)

- [¿Cómo puedo obtener la mayoría de los datos sin ralentizar la aplicación?](#Minimizing)

- [¿De qué más sitios se pueden obtener datos de IntelliTrace?](#WhereElse)

## <a name="WhatApps"></a> ¿Qué aplicaciones funcionan con el recolector?

- Aplicaciones Web ASP.NET hospedadas en Internet Information Services (IIS) versión 7,0, 7,5, 8,0, 12,0 y 16,0

- Aplicaciones de SharePoint 2010 y SharePoint 2013

- Aplicaciones de Windows Presentation Foundation (WPF) y Windows Forms.

## <a name="GetStarted"></a> ¿Cómo comenzar?

1. [Instalar el recolector](#BKMK_Install_the_IntelliTrace_Stand_Alone_Collector)

2. [Configurar permisos para el directorio de recopilador](#ConfigurePermissionsRunningCollector)

3. [Instalar cmdlets de PowerShell IntelliTrace para recopilar datos para aplicaciones web o aplicaciones de SharePoint](#BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets)

4. [Configurar permisos para el directorio de archivos .iTrace](#BKMK_Create_and_Configure_a_Log_File_Directory)

5. [Recopilar datos de una aplicación web o de una aplicación de SharePoint](#BKMK_Collect_Data_from_IIS_Application_Pools)

     o bien

     [Recopilar datos de una aplicación administrada](#BKMK_Collect_Data_from_Executables)

6. [Abra el archivo .iTrace en Visual Studio Enterprise.](#BKMK_View_IntelliTrace_Log_Files)

## <a name="BKMK_Install_the_IntelliTrace_Stand_Alone_Collector"></a> Instalar el recolector

1. En el servidor de la aplicación, cree el directorio del recolector, por ejemplo: **C:\IntelliTraceCollector**.

2. Obtenga el recopilador desde el [centro de descarga de Microsoft](https://visualstudio.microsoft.com/downloads/#intellitrace-standalone-collector-for-visual-studio-2019), [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=intellitrace%20standalone%20collector%20visual%20studio%202017)o desde la carpeta de instalación de Visual Studio 2013 Update 3. [IntelliTrace Collector para Visual Studio 2013 Update 4](https://www.microsoft.com/download/details.aspx?id=44909)::

   - **Centro de descarga de Microsoft** o **My.VisualStudio.com**:

     1. Seleccione la opción **Descargar**cerca de **IntelliTraceCollector.exe**.

     2. Guarde IntelliTraceCollector.exe en el directorio del recolector (por ejemplo, **C:\IntelliTraceCollector**).

     3. Ejecute IntelliTraceCollector.exe. Esto hace que se extraiga el archivo IntelliTraceCollection.cab.

        \- o -

   - **Carpeta de instalación de Visual Studio**:

     1. Copie IntelliTraceCollection. cab de la carpeta donde está instalado el recopilador, por ejemplo:

          **.. \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\Microsoft\IntelliTrace**

          o bien, para versiones anteriores de Visual Studio:

          **.. \Microsoft Visual Studio 12.0 \ Common7\IDE\CommonExtensions\Microsoft\IntelliTrace\12.0.0**

     2. Coloque IntelliTraceCollection.cab en el directorio del recolector (por ejemplo, **C:\IntelliTraceCollector**).

3. Expanda IntelliTraceCollection.cab:

   1. En el servidor de la aplicación, abra una ventana de símbolo del sistema como administrador.

   2. Vaya al directorio del recolector (por ejemplo, **C:\IntelliTraceCollector**).

   3. Use el comando **expand** , incluido el punto al final ( **.** ), para expandir IntelliTraceCollection.cab:

        `expand  /f:* IntelliTraceCollection.cab .`

       > [!NOTE]
       > El punto ( **.** ) hace que se conserven las subcarpetas que contienen los planes de recolección localizados.

## <a name="ConfigurePermissionsRunningCollector"></a> Configurar permisos para el directorio de recopilador

1. En el servidor de la aplicación, abra una ventana de símbolo del sistema como administrador.

2. Use el comando **icacls** de Windows para conceder permisos completos de administrador del servidor al directorio del recolector. Por ejemplo:

     `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\AdministratorID >* `":F`

3. Para recopilar datos de una aplicación web o de una aplicación de SharePoint:

    1. Dé permisos completos en el directorio del recolector a la persona que vaya a ejecutar los cmdlets de PowerShell de IntelliTrace.

         Por ejemplo:

         `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\UserID>* `":F`

    2. Dé permisos de lectura y ejecución en el directorio del recolector al grupo de aplicaciones de la aplicación web o la aplicación de SharePoint.

         Por ejemplo:

        - En el caso de una aplicación web en el grupo de aplicaciones **DefaultAppPool** :

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\DefaultAppPool":RX`

        - Para una aplicación de SharePoint en el grupo de aplicaciones **SharePoint - 80** :

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\SharePoint - 80":RX`

## <a name="BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets"></a> Instalar cmdlets de PowerShell IntelliTrace para recopilar datos para aplicaciones web o aplicaciones de SharePoint

1. En el servidor de la aplicación, asegúrese de que PowerShell está habilitado. En la mayoría de las versiones de Windows Server, esta característica se puede agregar en la herramienta administrativa **Administrador del servidor** .

     ![Agregar PowerShell mediante Administrador del servidor](../debugger/media/intellitrace_servermanager_addpowershell.png "INTELLITRACE_ServerManager_AddPowerShell")

2. Instale los cmdlets de PowerShell de IntelliTrace.

    1. Abra una ventana de símbolo del sistema de PowerShell como administrador.

        1. Elija **Inicio**, **Todos los programas**, **Accesorios**, **Windows PowerShell**.

        2. Elija uno de los siguientes pasos:

            - En sistemas operativos de 64 bits, abra el menú contextual de **Windows PowerShell**. Elija **Ejecutar como administrador**.

            - En sistemas operativos de 32 bits, abra el menú contextual de **Windows PowerShell (x86)** . Elija **Ejecutar como administrador**.

    2. En la ventana de comandos de PowerShell, use el comando **Import-Module** para importar **Microsoft.VisualStudio.IntelliTrace.PowerShell.dll**.

         Por ejemplo:

         `Import-Module "C:\IntelliTraceCollector\Microsoft.VisualStudio.IntelliTrace.PowerShell.dll"`

## <a name="BKMK_Create_and_Configure_a_Log_File_Directory"></a> Configurar permisos para el directorio de archivos .iTrace

1. En el servidor de la aplicación, cree el directorio de archivos .iTrace, por ejemplo: **C:\IntelliTraceLogFiles**.

   > [!NOTE]
   > - Para evitar ralentizar la aplicación, elija una ubicación en un disco de alta velocidad local que no sea muy activo.
   >   - Puede colocar los archivos iTrace y los archivos del recolector en el mismo lugar. Sin embargo, si tiene una aplicación web o una aplicación de SharePoint, procure que esta ubicación esté fuera del directorio que hospeda la aplicación.
   >
   > [!IMPORTANT]
   > - Restrinja el directorio de archivos .iTrace a solo aquellas identidades deben trabajar con el recolector. Un archivo .iTrace podría contener información confidencial, como datos de los usuarios, bases de datos (u otras ubicaciones de origen) y cadenas de conexión, ya que IntelliTrace puede registrar cualquier dato que se pase a los parámetros de método o como valores devueltos.
   >   - Asegúrese de que los usuarios que pueden abrir archivos iTrace tienen permiso para ver datos confidenciales. Tenga precaución al compartir archivos iTrace. Si otras personas deben tener acceso a ellos, copie los archivos en una ubicación compartida segura.

2. En una aplicación web o aplicación de SharePoint, conceda al grupo de aplicaciones permisos completos al directorio de archivos iTrace. Puede usar el comando **icacls** de Windows o el Explorador de Windows (o el Explorador de archivos).

    Por ejemplo:

   - Para configurar permisos con el comando **icacls** de Windows:

     - En el caso de una aplicación web en el grupo de aplicaciones **DefaultAppPool** :

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\DefaultAppPool":F`

     - Para una aplicación de SharePoint en el grupo de aplicaciones **SharePoint - 80** :

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\SharePoint - 80":F`

       o bien

   - Para configurar permisos con el Explorador de Windows (o el Explorador de archivos):

     1. Abra las **Propiedades** del directorio de archivos .iTrace.

     2. En la pestaña **Seguridad** , elija **Editar** **Agregar**.

     3. Asegúrese de que **Entidades de seguridad integradas** aparece en el cuadro **Seleccionar este tipo de objeto** . Si no está allí, elija **Tipos de objeto** para agregarlo.

     4. Asegúrese de que el equipo local aparece en el cuadro **Desde esta ubicación** . Si no está allí, elija **Ubicaciones** para cambiarlo.

     5. En el cuadro **Escriba los nombres de objeto que desea seleccionar** , agregue el grupo de aplicaciones de la aplicación web o la aplicación de SharePoint.

     6. Elija **Comprobar nombres** para resolver el nombre. Elija **Aceptar**.

     7. Asegúrese de que el grupo de aplicaciones tiene **Control total**.

## <a name="BKMK_Collect_Data_from_IIS_Application_Pools"></a> Recopilar datos de una aplicación web o de una aplicación de SharePoint

1. Para iniciar la recolección de datos, abra una ventana de comandos de PowerShell como administrador y ejecute este comando:

     `Start-IntelliTraceCollection` `"` *\<ApplicationPool>* `"` *\<PathToCollectionPlan>* *\<FullPathToITraceFileDirectory>*

    > [!IMPORTANT]
    > Después de ejecutar este comando, escriba **Y** para confirmar que desea iniciar la recolección de datos.

     Por ejemplo, para recopilar datos de una aplicación de SharePoint en el grupo de aplicaciones de **SharePoint - 80** :

     `Start-IntelliTraceCollection "SharePoint - 80" "C:\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogFiles"`

    |||
    |-|-|
    |*grupoAplicaciones*|Nombre del grupo de aplicaciones donde la aplicación se ejecuta.|
    |*rutaAccesoPlanRecolección*|Ruta de acceso a un plan de recolección, que es un archivo .xml que configura las opciones del recolector.<br /><br /> Puede especificar un plan que se haya suministrado junto con el recolector. Los siguientes planes funcionan en aplicaciones web y aplicaciones de SharePoint:<br /><br /> - collection_plan.ASP.NET.default.xml<br />     Recopila únicamente eventos de IntelliTrace y eventos de SharePoint, incluidas excepciones, llamadas de base de datos y solicitudes de servidor web.<br />- collection_plan.ASP.NET.trace.xml<br />     Recopila las llamadas a funciones y todos los datos en collection_plan.ASP.NET.default.xml. Este plan es adecuado para obtener análisis detallados, pero puede ralentizar la aplicación más que con collection_plan.ASP.NET.default.xml.<br /><br /> Para evitar la ralentización de la aplicación, personalice estos planes o cree su propio plan. Por seguridad, coloque los planes personalizados en la misma ubicación segura que los archivos del recolector. Vea [Crear y personalizar planes de recolección de IntelliTrace](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) y [¿Cómo puedo obtener la mayoría de los datos sin ralentizar la aplicación?](#Minimizing) **Nota:**  De forma predeterminada, el tamaño máximo del archivo. iTrace es 100 MB. Cuando un archivo .iTrace alcanza este límite, el recopilador elimina las entradas más antiguas del archivo para dejar espacio para las entradas más recientes. Para cambiar este límite, modifique el atributo `MaximumLogFileSize` del plan de recolección. <br /><br /> *¿Dónde puedo encontrar las versiones localizadas de estos planes de recolección?*<br /><br /> Los planes localizados se encuentran en las subcarpetas del recolector.|
    |*rutaAccesoCompletaDirectorioArchivosITrace*|Ruta de acceso completa al directorio de archivos .iTrace. **Nota de seguridad:**  Proporcione la ruta de acceso completa, no una ruta de acceso relativa.|

     El recolector se conecta al grupo de aplicaciones y empieza a recopilar datos.

     *¿Se puede abrir el archivo .iTrace en este momento?* No, el archivo está bloqueado durante la recolección de datos.

2. Reproduzca el problema.

3. Para crear un punto de control del archivo. iTrace, use esta sintaxis:

     `Checkpoint-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

4. Use esta sintaxis para comprobar el estado de la recolección:

     `Get-IntelliTraceCollectionStatus`

5. Use esta sintaxis para detener la recolección de datos:

     `Stop-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

    > [!IMPORTANT]
    > Después de ejecutar este comando, escriba **Y** para confirmar que desea detener la recolección de datos. De lo contrario, el recolector podría seguir recopilando de datos, el archivo .iTrace permanecerá bloqueado o es posible que el archivo no contenga datos útiles.

6. [Abra el archivo .iTrace en Visual Studio Enterprise.](#BKMK_View_IntelliTrace_Log_Files)

## <a name="BKMK_Collect_Data_from_Executables"></a> Recopilar datos de una aplicación administrada

1. Use esta sintaxis para iniciar la aplicación y recopilar datos al mismo tiempo:

     *\<FullPathToIntelliTraceCollectorExecutable>* `\IntelliTraceSC.exe launch /cp:` *\<PathToCollectionPlan>* `/f:` *\<FullPathToITraceFileDirectoryAndFileName>* *\<PathToAppExecutableFileAndFileName>*

     Por ejemplo, para recopilar datos de una aplicación denominada **MyApp**:

     `C:IntelliTraceCollectorIntelliTraceSC.exe launch /cp:"C:IntelliTraceCollectorcollection_plan.ASP.NET.default.xml" /f:"C:IntelliTraceLogFilesMyApp.itrace" "C:MyAppMyApp.exe"`

    |||
    |-|-|
    |*rutaAccesoCompletaEjecutableIntelliTraceCollector*|Ruta de acceso completa al archivo ejecutable del recolector, IntelliTraceSC.exe.|
    |*rutaAccesoPlanRecolección*|Ruta de acceso a un plan de recolección, que es un archivo .xml que configura las opciones del recolector.<br /><br /> Puede especificar un plan que se haya suministrado junto con el recolector. Los siguientes planes funcionan en las aplicaciones administradas:<br /><br /> - collection_plan.ASP.NET.default.xml<br />     Recopila únicamente eventos de IntelliTrace, incluidas excepciones, llamadas de base de datos y solicitudes de servidor web.<br />- collection_plan.ASP.NET.trace.xml<br />     Recopila las llamadas a funciones y todos los datos en collection_plan.ASP.NET.default.xml. Este plan es adecuado para obtener análisis detallados, pero puede ralentizar la aplicación más que con collection_plan.ASP.NET.default.xml.<br /><br /> Para evitar la ralentización de la aplicación, personalice estos planes o cree su propio plan. Por seguridad, coloque los planes personalizados en la misma ubicación segura que los archivos del recolector. Vea [Crear y personalizar planes de recolección de IntelliTrace](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) y [¿Cómo puedo obtener la mayoría de los datos sin ralentizar la aplicación?](#Minimizing) **Nota:**  De forma predeterminada, el tamaño máximo del archivo. iTrace es 100 MB. Cuando un archivo .iTrace alcanza este límite, el recopilador elimina las entradas más antiguas del archivo para dejar espacio para las entradas más recientes. Para cambiar este límite, modifique el atributo `MaximumLogFileSize` del plan de recolección. <br /><br /> *¿Dónde puedo encontrar las versiones localizadas de estos planes de recolección?*<br /><br /> Los planes localizados se encuentran en las subcarpetas del recolector.|
    |*rutaAccesoCompletaNombreArchivoYDirectorioArchivosITrace*|Ruta de acceso completa al directorio de archivos .iTrace y el nombre del archivo .iTrace con la extensión **.itrace** . **Nota de seguridad:**  Proporcione la ruta de acceso completa, no una ruta de acceso relativa.|
    |*rutaAccesoNombreArchivoYArchivoEjecutableAplicación*|Ruta de acceso y nombre de archivo de la aplicación administrada.|

2. Cierre la aplicación para detener la recolección de datos.

3. [Abra el archivo .iTrace en Visual Studio Enterprise.](#BKMK_View_IntelliTrace_Log_Files)

## <a name="BKMK_View_IntelliTrace_Log_Files"></a> Abra el archivo .iTrace en Visual Studio Enterprise.

> [!NOTE]
> Para depurar con IntelliTrace y recorrer el código, debe tener los archivos de código fuente y los archivos de símbolos correspondientes. Vea [diagnosticar problemas después](../debugger/diagnose-problems-after-deployment.md)de la implementación.

1. Mueva el archivo .iTrace o cópielo en un equipo con Visual Studio Enterprise (pero no a las versiones Professional o Community).

2. Haga doble clic en el archivo .iTrace fuera de Visual Studio o abra el archivo desde Visual Studio.

     Visual Studio muestra la página **Resumen de IntelliTrace** . En la mayoría de las secciones, puede revisar eventos u otros elementos, elegir un elemento e iniciar la depuración con IntelliTrace justo donde y cuando un evento se ha producido. Vea [uso de datos de IntelliTrace guardados](../debugger/using-saved-intellitrace-data.md).

    > [!NOTE]
    > Para depurar con IntelliTrace y recorrer el código, debe tener los archivos de código fuente y los archivos de símbolos correspondientes en el equipo de desarrollo. Vea [diagnosticar problemas después](../debugger/diagnose-problems-after-deployment.md)de la implementación.

## <a name="Minimizing"></a> ¿Cómo puedo obtener la mayoría de los datos sin ralentizar la aplicación?
 IntelliTrace puede recopilar una gran cantidad de datos, por lo que el impacto en el rendimiento de la aplicación depende de los datos que IntelliTrace recopile y el tipo de código que analice. Vea [Optimizar la recolección de IntelliTrace en servidores de producción](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/)

 A continuación, se muestran algunas maneras de obtener la mayoría de los datos sin ralentizar la aplicación:

- Ejecute el recopilador solo cuando crea que hay algún problema o cuando pueda reproducir el problema.

   Inicie la recolección, reproduzca el problema y, a continuación, detenga la recolección. Abra el archivo .iTrace en Visual Studio Enterprise y examine los datos. Vea [Abra el archivo .iTrace en Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files).

- En las aplicaciones web y de SharePoint, el recolector registra los datos de cada aplicación web que comparte el grupo de aplicaciones especificado. Esto puede ralentizar cualquier aplicación que comparta el mismo grupo de aplicaciones, aunque puede especificar únicamente los módulos para una sola aplicación en el plan de recolección.

   Para evitar que el recolector ralentice otras aplicaciones, hospede cada aplicación en su propio grupo de aplicaciones.

- Revise los eventos en el plan de recolección para el que IntelliTrace recopila los datos. Edite el plan de recolección para deshabilitar los eventos que no son pertinentes o no le interesan.

   Para deshabilitar un evento, establezca el atributo `enabled` para el elemento `<DiagnosticEventSpecification>` en `false`:

   `<DiagnosticEventSpecification enabled="false">`

   Si no existe el atributo `enabled` , el evento está habilitado.

   *¿Cómo mejora esto el rendimiento?*

  - Puede reducir el tiempo de inicio si deshabilita los eventos que no sean relevantes para la aplicación. Por ejemplo, deshabilite los eventos de Windows Workflow en las aplicaciones que no usen Windows Workflow.

  - Puede mejorar el rendimiento del inicio y del tiempo de ejecución si deshabilita los eventos del registro para las aplicaciones que tienen acceso al registro pero no los problemas con la configuración del registro.

- Repase los módulos en el plan de recolección para el que IntelliTrace recopila los datos. Edite el plan de recolección para incluir solo los módulos que le interesen:

  1. Abra el plan de recolección. Busque el elemento `<ModuleList>` .

  2. En `<ModuleList>`establezca el atributo `isExclusionList` en `false`.

  3. Use el elemento `<Name>` para especificar cada módulo con uno de los siguientes valores: nombre de archivo, valor de cadena para incluir cualquier módulo cuyo nombre contenga esa cadena o clave pública.

     Por ejemplo, para recopilar datos de únicamente el módulo web principal de la aplicación web Fabrikam Fiber, cree una lista como esta:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>FabrikamFiber.Web.dll</Name>
  </ModuleList>
  ```

   Para recopilar datos de cualquier módulo cuyo nombre incluya “Fabrikam”, cree una lista como esta:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>Fabrikam</Name>
  </ModuleList>
  ```

   Para recopilar datos de módulos especificando sus tokens de clave pública, cree una lista como esta:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>PublicKeyToken:B77A5C561934E089</Name>
     <Name>PublicKeyToken:B03F5F7F11D50A3A</Name>
     <Name>PublicKeyToken:31BF3856AD364E35</Name>
     <Name>PublicKeyToken:89845DCD8080CC91</Name>
     <Name>PublicKeyToken:71E9BCE111E9429C</Name>
  </ModuleList>
  ```

   *¿Cómo mejora esto el rendimiento?*

   Esto reduce la cantidad de información de llamadas a métodos y otros datos de instrumentación que IntelliTrace recopila cuando la aplicación se inicia y se ejecuta. Estos datos le permiten:

  - Recorrer el código después de recopilar los datos.

  - Examinar los valores que se pasan a las llamadas a función y que estas devuelven.

    *¿Por qué no excluir módulos en su lugar?*

    Los planes de recolección excluyen módulos de forma predeterminada estableciendo el atributo `isExclusionList` en `true`. Sin embargo, la exclusión de módulos no impide que se puedan seguir recopilando datos de módulos que no cumplen los criterios de lista o que no le interesen, como los módulos de terceros o de código abierto.

- *¿Hay algún dato que IntelliTrace no recopile?*

   Sí. Para reducir el impacto en el rendimiento, IntelliTrace restringe la recolección de datos a los valores de los tipos de datos primitivos pasados a métodos y devueltos de estos, así como a los valores de los tipos de datos primitivos en campos de objetos de nivel superior pasados a métodos y devueltos de estos.

   Por ejemplo, suponga que tiene una signatura de método `AlterEmployee` que acepta un entero `id` y un objeto `Employee` de `oldemployee`:

   `public Employee AlterEmployee(int id, Employee oldemployee)`

   El tipo `Employee` tiene los atributos siguientes: `Id`, `Name`y `HomeAddress`. Existe una relación de asociación entre `Employee` y el tipo `Address` .

   ![Relación entre el empleado y la dirección](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")

   El recolector registra valores de `id`, `Employee.Id`, `Employee.Name` y el objeto `Employee` devuelto del método `AlterEmployee` . Sin embargo, el recolector únicamente registra información sobre si es null o no el objeto `Address` . El recolector tampoco registra datos sobre variables locales del método `AlterEmployee` , a menos que otros métodos utilicen esas variables locales como parámetros en el punto en el que se registran como parámetros de método.

## <a name="WhereElse"></a> ¿De qué más sitios se pueden obtener datos de IntelliTrace?

Puede obtener datos de IntelliTrace de una sesión de depuración de IntelliTrace en Visual Studio Enterprise. Consulte [características de IntelliTrace](../debugger/intellitrace-features.md).

## <a name="where-can-i-get-more-information"></a>¿Dónde puedo obtener más información?
 [Uso de datos de IntelliTrace guardados](../debugger/using-saved-intellitrace-data.md)

 [IntelliTrace](../debugger/intellitrace.md)

### <a name="blogs"></a>Blogs
 [Uso del recopilador independiente de IntelliTrace de manera remota](https://devblogs.microsoft.com/devops/using-the-intellitrace-standalone-collector-remotely/)

 [Crear y personalizar planes de recolección de IntelliTrace](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/)

 [Optimizar la recolección de IntelliTrace en servidores de producción](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/)

 [Microsoft DevOps](https://devblogs.microsoft.com/devops/)

### <a name="forums"></a>Foros
 [Depurador de Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="videos"></a>Vídeos
 [Vídeo de Channel 9: Recopilación y análisis de datos de IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Collecting-and-analyzing-data-in-production)
