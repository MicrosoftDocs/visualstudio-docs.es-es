---
title: "Diagnosticar problemas después de la implementación | Documentos de Microsoft"
ms.custom: 
ms.date: 06/20/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3463eab-a352-4d17-8551-adbaad526db0
caps.latest.revision: "60"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f2dce73eab17d97779edec73c1c2c0c60690ac5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="diagnose-problems-after-deployment"></a>Diagnosis de problemas tras la implementación
Para diagnosticar problemas en la aplicación web ASP.NET después de la implementación con IntelliTrace, incluya la información de compilación en su versión para que Visual Studio pueda encontrar automáticamente los archivos de código fuente y archivos de símbolos correctos que se necesitan para depurar el registro de IntelliTrace.  

 Si usa Microsoft Monitoring Agent para controlar IntelliTrace, también necesitará configurar la supervisión de rendimiento de la aplicación en el servidor web. Esto registra eventos de diagnóstico mientras se ejecuta la aplicación y guarda los eventos en un archivo de registro de IntelliTrace. Después, puede consultar los eventos en Visual Studio Enterprise (pero no en las versiones Professional ni Community), ir al código donde se produjo un evento, ver los valores registrados en ese momento y avanzar o retroceder en el código ejecutado. Después de identificar y corregir el problema, repita el ciclo para compilar, lanzar y supervisar la aplicación con el objetivo de solucionar posibles problemas futuros con mayor rapidez.  

 ![Código, compilar, liberar, supervisar, diagnosticar, corregir](../debugger/media/ffr_cycle.png "FFR_Cycle")  

 **Necesitará:**  
  
-   Visual Studio 2017, Visual Studio 2015 o Team Foundation Server de 2017 2015, 2013, 2012 o 2010 para configurar la compilación  
  
-   Microsoft Monitoring Agent para supervisar la aplicación y registrar los datos de diagnóstico  

-   Visual Studio Enterprise (pero no las versiones Professional ni Community) para revisar los datos de diagnóstico y depurar el código con IntelliTrace  

##  <a name="SetUpBuild"></a>Paso 1: Incluir información en la versión de compilación  
 Configure el proceso de compilación para crear un manifiesto de compilación (archivo BuildInfo.config) para el proyecto web e incluya este manifiesto en la versión. Este manifiesto contiene información sobre el proyecto, el control de código fuente y el sistema de compilación que se usaron para crear una compilación específica. Esa información ayuda a Visual Studio a identificar el código fuente y los símbolos que coincidan después de abrir el registro de IntelliTrace para revisar los eventos registrados.  

###  <a name="AutomatedBuild"></a>Crear el manifiesto de compilación para una compilación automatizada con Team Foundation Server  

 Haga lo siguiente si usa control de versiones de Team Foundation o Git.
  
 **Paso 2:** [Paso 2: Release your app](#DeployRelease)  
  
 Haga lo siguiente si usa control de versiones de Team Foundation o Git.  
 
 ####  <a name="TFS2017"></a>Servidor de Team Foundation Server de 2017

 Configure la definición de compilación para agregar las ubicaciones del código fuente, la compilación y los símbolos al manifiesto de compilación (archivo BuildInfo.config). Team Foundation Build crea automáticamente el archivo y lo copia en la carpeta de salida del proyecto.
  
1.  Si ya tiene una definición de compilación mediante la plantilla de ASP.NET Core (.NET Framework), puede seleccionar [editar la definición de compilación o crear una nueva definición de compilación.](http://msdn.microsoft.com/Library/1c2eca2d-9a65-477e-9b23-0678ff7882ee)
  
     ![Ver definición de compilación en TFS 2017](../debugger/media/ffr_tfs2017viewbuilddefinition.png "FFR_TFS2013ViewBuildDefinition")
  
2.  Si crea una nueva plantilla, elija la plantilla de ASP.NET Core (.NET Framework). 
  
     ![Elija la plantilla de proceso de compilación &#45; TFS 2017](../debugger/media/ffr_tfs2017buildprocesstemplate.png "FFR_TFS2013BuildProcessTemplate")  
  
3.  Especifique dónde guardar el archivo de símbolos (PDB) para indizar el origen automáticamente.  
  
     Si usa una plantilla personalizada, asegúrese de que la plantilla tiene una actividad para indizar el origen. Posteriormente, podrá agregar un argumento de MSBuild para especificar dónde quiere guardar los archivos de símbolos.
  
     ![Establecer la ruta de acceso de símbolos en la definición de compilación de 2017 TFS](../debugger/media/ffr_tfs2017builddefsymbolspath.png "FFR_TFS2013BuildDefSymbolsPath")  
  
     Para obtener más información sobre los símbolos, consulte [publicar datos de símbolos](http://msdn.microsoft.com/Library/bd6977ca-e30a-491a-a153-671d81222ce6).  
  
4.  Agregue este argumento de MSBuild para incluir el TFS y las ubicaciones de símbolos al archivo de manifiesto de compilación:  
  
     **/p:IncludeServerNameInBuildInfo = true**  
  
     Cualquier usuario que tenga acceso al servidor web podrá ver estas ubicaciones en el manifiesto de compilación. Asegúrese de que el servidor de código fuente sea seguro.
  
6.  Ejecute una nueva compilación.  

####  <a name="TFS2013"></a>Servidor de Team Foundation Server 2013  
 Configure la definición de compilación para agregar las ubicaciones del código fuente, la compilación y los símbolos al manifiesto de compilación (archivo BuildInfo.config). Team Foundation Build crea automáticamente el archivo y lo copia en la carpeta de salida del proyecto.  

1.  [Edite la definición de compilación o cree una nueva definición de compilación.](http://msdn.microsoft.com/Library/1c2eca2d-9a65-477e-9b23-0678ff7882ee)  

     ![Ver definición de compilación en TFS 2013](../debugger/media/ffr_tfs2013viewbuilddefinition.png "FFR_TFS2013ViewBuildDefinition")  

2.  Elija la plantilla predeterminada (TfvcTemplate.12.xaml) o su propia plantilla personalizada.  

     ![Elija la plantilla de proceso de compilación &#45; TFS 2013](../debugger/media/ffr_tfs2013buildprocesstemplate.png "FFR_TFS2013BuildProcessTemplate")  

3.  Especifique dónde guardar el archivo de símbolos (PDB) para indizar el origen automáticamente.  

     Si usa una plantilla personalizada, asegúrese de que la plantilla tiene una actividad para indizar el origen. Posteriormente, podrá agregar un argumento de MSBuild para especificar dónde quiere guardar los archivos de símbolos.  

     ![Establecer la ruta de acceso de símbolos en la definición de compilación de TFS 2013](../debugger/media/ffr_tfs2013builddefsymbolspath.png "FFR_TFS2013BuildDefSymbolsPath")  

     Para obtener más información sobre los símbolos, consulte [publicar datos de símbolos](http://msdn.microsoft.com/Library/bd6977ca-e30a-491a-a153-671d81222ce6).  

4.  Agregue este argumento de MSBuild para incluir el TFS y las ubicaciones de símbolos al archivo de manifiesto de compilación:  

     **/p:IncludeServerNameInBuildInfo = true**  
  
     Cualquier usuario que tenga acceso al servidor web podrá ver estas ubicaciones en el manifiesto de compilación. Asegúrese de que el servidor de código fuente sea seguro.

5.  Si usa una plantilla personalizada, agregue este argumento de MSBuild para especificar dónde guardar el archivo de símbolos:  
  
     **/ p: buildsymbolstorepath =**\<*ruta a símbolos*>  
  
     ![Incluir información de servidor de compilación en la compilación def TFS 2013](../debugger/media/ffr_tfs2013builddefincludeserverinfo.png "FFR_TFS2013BuildDefIncludeServerInfo")  
  
     Y agregue estas líneas al archivo de proyecto web (.csproj, .vbproj):  
  
    ```  
    <!-- Import the targets file. Change the folder location as necessary. -->  
       <Import Project=""$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\BuildInfo\Microsoft.VisualStudio.ReleaseManagement.BuildInfo.targets" />  
  
    ```  

     Cualquier usuario que tenga acceso al servidor web podrá ver estas ubicaciones en el manifiesto de compilación. Asegúrese de que el servidor de código fuente sea seguro.  

6.  Ejecute una nueva compilación.  

 **Paso 2:** [Paso 2: Release your app](#DeployRelease)  

####  <a name="TFS2012_2010"></a>Team Foundation Server 2012 o 2010  
 Haga lo siguiente para crear automáticamente el manifiesto de compilación (archivo BuildInfo.config) para el proyecto y copiar el archivo en la carpeta de salida del proyecto. El archivo aparece como "*NombreDelProyecto*.BuildInfo.config" en la carpeta de salida, pero tendrá el nombre "BuildInfo.config" en la carpeta de implementación después de publicar la aplicación.  

1.  Instale Visual Studio 2013 (cualquier edición) en el servidor de Team Foundation Build.  

2.  En la definición de compilación, especifique dónde guardar los símbolos para indizar el origen automáticamente.  

     Si usa una plantilla personalizada, asegúrese de que la plantilla tiene una actividad para indizar el origen.  

3.  Agregue estos argumentos de MSBuild a la definición de compilación:  

    -   **/p:VisualStudioVersion = 12.0**  

    -   **/p:MSBuildAssemblyVersion = 12.0**  

    -   **/TV:12.0**  

    -   **/p:IncludeServerNameInBuildInfo = true**  

    -   **/ p: buildsymbolstorepath =**\<*ruta a símbolos*>  

4.  Ejecute una nueva compilación.  

 **Paso 2:** [Paso 2: Release your app](#DeployRelease)  

###  <a name="ManualBuild"></a>Crear el manifiesto de compilación para una compilación manual con Visual Studio  
 Haga lo siguiente para crear automáticamente el manifiesto de compilación (archivo BuildInfo.config) para el proyecto y copiar el archivo en la carpeta de salida del proyecto. El archivo aparece como "*NombreDelProyecto*.BuildInfo.config" en la carpeta de salida, pero tendrá el nombre "BuildInfo.config" en la carpeta de implementación después de publicar la aplicación.  

1.  En el **Explorador de soluciones**, descargue el proyecto web.  

2.  Abra el archivo de proyecto (.csproj, .vbproj). Agregue estas líneas:  

    ```xml  
    <!-- **************************************************** -->  
    <!-- Build info -->  
    <PropertyGroup>  
       <!-- Generate the BuildInfo.config file -->  
       <GenerateBuildInfoConfigFile>True</GenerateBuildInfoConfigFile>  
       <!-- Include server name in build info -->   
       <IncludeServerNameInBuildInfo>True</IncludeServerNameInBuildInfo>   
       <!-- Include the symbols path so Visual Studio can find the matching deployed code when you start debugging. -->  
       <BuildSymbolStorePath><path to symbols></BuildSymbolStorePath>  
    </PropertyGroup>  
    <!-- **************************************************** -->  
    ```  

3.  Proteja el archivo de proyecto actualizado.  

4.  Ejecute una nueva compilación.  

 **Paso 2:** [Paso 2: Release your app](#DeployRelease)  

###  <a name="MSBuild"></a>Crear el manifiesto de compilación para una compilación manual con MSBuild.exe  
 Agregue estos argumentos de compilación cuando ejecute una compilación:  

 **/p:GenerateBuildInfoConfigFile = true**  

 **/p:IncludeServerNameInBuildInfo = true**  

 **/ p: buildsymbolstorepath =**\<*ruta a símbolos*>  

##  <a name="DeployRelease"></a>Paso 2: Lanzar la aplicación  
 Si usa el [paquete Web.Deploy](http://msdn.microsoft.com/library/dd394698.aspx) creado por el proceso de compilación para implementar la aplicación, el nombre del manifiesto de compilación se cambiará automáticamente de “*NombreDelProyecto*.BuildInfo.config” a “BuildInfo.config” y se copiará en la misma carpeta que el archivo Web.config de la aplicación en el servidor web.  

 Si usa otros métodos para implementar la aplicación, asegúrese de cambiar el nombre del manifiesto de compilación de “*NombreDelProyecto*.BuildInfo.config” a “BuildInfo.config” y que se copie en la misma carpeta que el archivo Web.config de la aplicación en el servidor web.  

## <a name="step-3-monitor-your-app"></a>Paso 3: supervisar la aplicación  
 Establezca la supervisión de rendimiento de aplicaciones en el servidor web para identificar los posibles problemas de la aplicación, registrar eventos de diagnóstico y guardar estos eventos en un archivo de registro de IntelliTrace. Vea [supervisar la publicación para problemas de implementación de](../debugger/using-the-intellitrace-stand-alone-collector.md).  

##  <a name="InvestigateEvents"></a>Paso 4: Detectar el problema  
 Necesitará Visual Studio Enterprise en el equipo de desarrollo o en otro equipo para revisar los eventos registrados y depurar el código con IntelliTrace. También puede usar herramientas como CodeLens, mapas de depurador y mapas de código para diagnosticar el problema.  

### <a name="open-the-intellitrace-log-and-matching-solution"></a>Abrir el registro de IntelliTrace y la solución correspondiente  

1.  Abra el registro de IntelliTrace (archivo .iTrace) en Visual Studio Enterprise. O bien, haga doble clic en el archivo si tiene Visual Studio Enterprise en el mismo equipo.  

2.  Elija **Abrir solución** para hacer que Visual Studio abra automáticamente la solución o el proyecto correspondiente, si el proyecto no se compiló como parte de una solución. [P: ¿el registro de IntelliTrace falta información sobre una aplicación implementada. ¿Por qué ocurre esto? ¿Qué hago?](#InvalidConfigFile)  

     Visual Studio aplaza automáticamente los cambios pendientes al abrir la solución o proyecto correspondiente. Para obtener más detalles sobre este conjunto de cambios aplazados, consulte la ventana **Salida** o **Team Explorer**.  

     Antes de realizar cambios, confirme que tiene el código fuente correcto. Si usa bifurcaciones, podría estar trabajando en una bifurcación distinta de donde Visual Studio encuentra el código fuente correspondiente, como su bifurcación de versión.  

     ![Abrir solución desde el registro de IntelliTrace](../debugger/media/ffr_itsummarypageopensolution.png "FFR_ITSummaryPageOpenSolution")  

     Si tiene un área de trabajo asignada a esta solución o proyecto, Visual Studio seleccionará dicha área de trabajo para colocar el código fuente encontrado.  

     ![Abrir desde el control de código fuente al área de trabajo asignada](../debugger/media/ffr_openprojectfromsourcecontrol_mapped.png "FFR_OpenProjectFromSourceControl_Mapped")  

     De lo contrario, elija otra área de trabajo o cree una nueva. Visual Studio asignará la bifurcación completa a esta área de trabajo.  

     ![Abrir desde el control de código fuente &#45; Crear nueva área de trabajo](../debugger/media/ffr_openprojectfromsourcecontrol_createnewworkspace.png "FFR_OpenProjectFromSourceControl_CreateNewWorkspace")  

     Para crear un área de trabajo con asignaciones específicas o un nombre distinto al del equipo, elija **Administrar**.  

     [P: ¿por qué dice Visual Studio que mi área de trabajo seleccionada no es válida?](#IneligibleWorkspace)  

     [P: ¿por qué no se puede continuar hasta elegir una colección de equipo o una colección distinta?](#ChooseTeamProject)  

### <a name="diagnose-a-performance-problem"></a>Diagnosticar un problema de rendimiento  

1.  En **Infracciones de rendimiento**, consulte los eventos de rendimiento registrados, el tiempo de ejecución total y otra información del evento. A continuación, profundice más en los métodos que se llamaron durante un evento de rendimiento específico.  

     ![Ver detalles de eventos de rendimiento](../debugger/media/ffr_itsummarypageperformance.png "FFR_ITSummaryPagePerformance")  

     También puede hacer doble clic en el evento.  

2.  En la página de eventos, revise los tiempos de ejecución de estas llamadas. Busque una llamada lenta en el árbol de ejecución.  

     Las llamadas más lentas aparecen en su propia sección si tiene varias llamadas, anidadas o de otra manera.  

     Expanda esa llamada para revisar todas las llamadas anidadas y los valores que se registraron en ese punto en el tiempo. Después, inicie la depuración desde esa llamada.  

     ![Iniciar la depuración desde la llamada al método](../debugger/media/ffr_itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")  

     También puede hacer simplemente doble clic en la llamada.  

     Si el método está en el código de aplicación, Visual Studio va a ese método.  

     ![Vaya al código de la aplicación de eventos de rendimiento](../debugger/media/ffr_itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")  

     Ahora puede revisar otros valores registrados, la pila de llamadas, recorrer el código o utilizar la ventana **IntelliTrace** para [moverse hacia atrás o hacia delante “en el tiempo” por otros métodos](../debugger/intellitrace.md) a los que se llamó durante este evento de rendimiento. [¿Qué es todos los eventos e información en el registro de IntelliTrace? ](../debugger/using-saved-intellitrace-data.md) [¿Qué más puedo hacer desde aquí?](#WhatElse) ¿[Quiere obtener más información acerca de los eventos de rendimiento?](http://blogs.msdn.com/b/visualstudioalm/archive/2013/09/20/performance-details-in-intellitrace.aspx)  

### <a name="diagnose-an-exception"></a>Diagnosticar una excepción  

1.  En **Datos de excepción**, revise los eventos de excepciones registrados, sus tipos, mensajes y cuándo se produjeron las excepciones. Para profundizar en el código, inicie la depuración desde el evento más reciente de un grupo de excepciones.  

     ![Iniciar la depuración desde el evento de excepción](../debugger/media/ffr_itsummarypageexception.png "FFR_ITSummaryPageException")  

     También puede hacer doble clic en el evento.  

     Si se produjo una excepción en el código de la aplicación, Visual Studio va al lugar donde se ha producido la excepción.  

     ![Vaya a código de la aplicación desde un evento de excepción](../debugger/media/ffr_itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")  

     Ahora puede revisar otros valores registrados, la pila de llamadas o utilizar la ventana **IntelliTrace** para [moverse hacia atrás o hacia delante “en el tiempo” por otros eventos registrados](../debugger/intellitrace.md), código relacionado y los valores registrados en esos puntos en el tiempo. [¿Qué es todos los eventos e información en el registro de IntelliTrace?](../debugger/using-saved-intellitrace-data.md)  

###  <a name="WhatElse"></a>¿Qué más puedo hacer desde aquí?  

-   [Obtener más información acerca de este código](../ide/find-code-changes-and-other-history-with-codelens.md). Para buscar referencias a este código, su historial de cambios, errores relacionados, elementos de trabajo, revisiones de código o pruebas unitarias - todo ello sin salir del editor - use los indicadores de CodeLens en el editor.  

     ![CodeLens &#45; Ver referencias a este código](../debugger/media/ffr_itsummarypageperformancecodelensreferences.png "FFR_ITSummaryPagePerformanceCodeLensReferences")  

     ![CodeLens &#45; Ver historial de cambios de este código](../debugger/media/ffr_itsummarypageperformancecodelensauthors.png "FFR_ITSummaryPagePerformanceCodeLensAuthors")  

-   [Asignar su lugar en el código durante la depuración.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) Para realizar un seguimiento visual de los métodos llamados durante la sesión de depuración, asigne la pila de llamadas.  

     ![Asignar la pila de llamadas durante la depuración](../debugger/media/ffr_itsummarypageperformancedebuggermap.png "FFR_ITSummaryPagePerformanceDebuggerMap")  

###  <a name="FAQ"></a> Preguntas y respuestas  

####  <a name="WhyInclude"></a>P: ¿por qué incluir información acerca de mi proyecto, control de código fuente, compilación y símbolos con mi versión?  
 Visual Studio usa esta información para buscar la solución y el código fuente que coincidan con la versión que intente depurar. Después de abrir el registro de IntelliTrace y seleccionar el evento para iniciar la depuración, Visual Studio usa símbolos para buscar y mostrar el código donde se produjo el evento. Después, podrá consultar los valores que se registraron y avanzar o retroceder en la ejecución del código.  

 Si usa TFS y esta información no se encuentra en el manifiesto de compilación (archivo BuildInfo.config), Visual Studio buscará el código fuente correspondiente y los símbolos en el TFS conectado actualmente. Si Visual Studio no puede encontrar el TFS correctos ni código fuente que coincida, se le pedirá que elija un TFS distinto.  

####  <a name="InvalidConfigFile"></a>P: ¿el registro de IntelliTrace falta información sobre una aplicación implementada. ¿Por qué ocurre esto? ¿Qué hago?  
 Esto puede ocurrir si realiza la implementación desde un equipo de desarrollo o si no está conectado a TFS durante la implementación.  

1.  Vaya a la carpeta de implementación del proyecto.  

2.  Busque y abra el manifiesto de compilación (archivo BuildInfo.config).  

3.  Compruebe que el archivo contenga la información necesaria:  

-   **ProjectName**  

     El nombre del proyecto en Visual Studio. Por ejemplo:  

    ```  
    <ProjectName>FabrikamFiber.Extranet.Web</ProjectName>  
    ```  

-   **Errónea**  

-   Información sobre el sistema de control de código fuente y las siguientes propiedades obligatorias:  

    -   **TFS**  

        -   **ProjectCollectionUri**: URI de Team Foundation Server y de la colección de proyectos  

        -   **ProjectItemSpec**: ruta de acceso al archivo del proyecto de la aplicación (.csproj o .vbproj)  

        -   **ProjectVersionSpec**: versión del proyecto  

         Por ejemplo:  

        ```  
        <SourceControl type="TFS">  
           <TfsSourceControl>  
              <ProjectCollectionUri>http://fabrikamfiber:8080/tfs/FabrikamFiber</ProjectCollectionUri>  
              <ProjectItemSpec>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectItemSpec>  
              <ProjectVersionSpec>LFabrikamFiber_BuildAndPublish_20130813@$/WorkInProgress</ProjectVersionSpec>  
           </TfsSourceControl>  
        </SourceControl>  
        ```  

    -   **Git**  

        -   **GitSourceControl**: ubicación del esquema **GitSourceControl**  

        -   **RepositoryUrl**: URI de Team Foundation Server, de la colección de proyectos y del repositorio Git  

        -   **ProjectPath**: ruta de acceso al archivo del proyecto de la aplicación (.csproj o .vbproj)  

        -   **CommitId**: identificador de confirmación  

         Por ejemplo:  

        ```  
        <SourceControl type="Git">   
           <GitSourceControl xmlns="http://schemas.microsoft.com/visualstudio/deploymentevent_git/2013/09">  
              <RepositoryUrl>http://gittf:8080/tfs/defaultcollection/_git/FabrikamFiber</RepositoryUrl>  
              <ProjectPath>/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectPath>  
              <CommitId>50662c96502dddaae5cd5ced962d9f14ec5bc64d</CommitId>  
           </GitSourceControl>  
        </SourceControl>  
        ```  

-   **Compilación**  

     Información sobre el sistema de compilación, ya sea `"TeamBuild"` o `"MSBuild"`, y las siguientes propiedades obligatorias:  

    -   **BuildLabel** (para TeamBuild): nombre y número de la compilación. Esta etiqueta también se usa como nombre del evento de implementación. Para obtener más información acerca de los números de compilación, consulte [Use números de compilación para proporcionar nombres descriptivos a las compilaciones completadas](http://msdn.microsoft.com/Library/1f302e9d-4b0a-40b5-8009-b69ca6f988c3).  

    -   **SymbolPath** (recomendado): lista de URI de las ubicaciones de símbolos (archivo PDB) separadas por punto y coma. Estas URI pueden ser URL o UNC. Esto permite a Visual Studio buscar los símbolos que coinciden para ayudarle con la depuración.  

    -   **BuildReportUrl** (para TeamBuild): ubicación del informe de compilación en TFS  

    -   **BuildId** (para TeamBuild): URI de los detalles de compilación en TFS. Esta URI también se usa como el identificador del evento de implementación. Si no usa TeamBuild, debe ser un identificador único.  

    -   **BuiltSolution**: ruta de acceso al archivo de solución que Visual Studio usa para buscar y abrir la solución correspondiente. Este es el contenido de la propiedad **SolutionPath** de MsBuild.  

     Por ejemplo:  

    -   **TFS**  

        ```  
        <Build type="TeamBuild">  
           <MsBuild>  
              <BuildLabel kind="label">FabrikamFiber_BuildAndPublish_20130813.1</BuildLabel>  
              <SymbolPath>\\fabrikamfiber\FabrikamFiber.CallCenter\Symbols</SymbolPath>  
              <BuildReportUrl kind="informative, url" url="http://fabrikamfiber:8080/tfs/FabrikamFiber/_releasePipeline/FindRelease?buildUri=fabrikamfiber%3a%2f%2f%2fBuild%2fBuild%2f448">Build Report Url</BuildReportUrl>  
              <BuildId kind="id">1c4444d2-518d-4673-a590-dce2773c7744,fabrikamfiber:///Build/Build/448</BuildId>  
              <BuiltSolution>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>  
           </MsBuild>  
        </Build>  
        ```  

    -   **Git**  

        ```  
        <Build type="MSBuild">   
           <MSBuild>  
              <SymbolPath>\\gittf\FabrikamFiber.CallCenter\Symbols</SymbolPath>  
              <BuiltSolution>/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>  
           </MSBuild>  
        </Build>  
        ```  

####  <a name="IneligibleWorkspace"></a>P: ¿por qué dice Visual Studio que mi área de trabajo seleccionada no es válida?  
 **R:** El área de trabajo seleccionada no tiene ninguna asignación entre la carpeta de control de código fuente y una carpeta local. Para crear una asignación para esta área de trabajo, elija **Administrar**. De lo contrario, elija un área de trabajo ya asignada o cree una nueva.  

 ![Abrir desde el control de código fuente con ninguna área de trabajo asignada](../debugger/media/ffr_openprojectfromsourcecontrol_notmapped.png "FFR_OpenProjectFromSourceControl_NotMapped")  

####  <a name="ChooseTeamProject"></a>P: ¿por qué no se puede continuar hasta elegir una colección de equipo o una colección distinta?  
 **R:** Esto puede ocurrir por cualquiera de las siguientes razones:  

-   Visual Studio no está conectado a TFS.  

     ![Abrir desde el control de código fuente &#45; No conectado](../debugger/media/ffr_openprojectfromsourcecontrol_notconnected.png "FFR_OpenProjectFromSourceControl_NotConnected")  

-   Visual Studio no encontró la solución o el proyecto en la colección de equipo actual.  

     Cuando la compilación el archivo de manifiesto (\<*ProjectName*>. BuildInfo.config) no especifica dónde Visual Studio puede encontrar el código fuente correspondiente, Visual Studio usa el TFS conectado actualmente para encontrar la solución correspondiente o el proyecto. Si la colección de equipo actual no tiene el código fuente correspondiente, Visual Studio le pedirá que se conecte a otra colección de equipo.  

-   Visual Studio no encontró la solución o proyecto en la colección especificada por el archivo de manifiesto de compilación (\<*ProjectName*>. BuildInfo.config).  

     Puede que el servidor TFS especificado ya no tenga el código fuente coincidente o que este ni siquiera exista, quizá porque se migró a un nuevo servidor TFS. Si el servidor TFS especificado no existe, puede que Visual Studio agote el tiempo de espera tras un minuto aproximadamente y después le pida que se conecte a otra colección. Para continuar, conéctese al servidor TFS correcto.  

     ![Abrir desde el control de código fuente &#45; migrar](../debugger/media/ffr_openprojectfromsourcecontrol_migrated.png "FFR_OpenProjectFromSourceControl_Migrated")  

####  <a name="WhatWorkspace"></a>P: ¿qué es un área de trabajo?  
 **R:** su [área de trabajo almacena una copia del origen de](http://msdn.microsoft.com/Library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a) para que pueda desarrollar y probarlo por separado antes de proteger su contribución. Si aún no tiene un área de trabajo asignada específicamente a la solución o proyecto encontrados, Visual Studio le pedirá que elija un área de trabajo disponible o que cree una nueva área de trabajo con el nombre del equipo como nombre predeterminado del área.  

####  <a name="UntrustedSymbols"></a>P: ¿por qué aparece este mensaje sobre símbolos que no se confía?  
 ![¿Depurar con la ruta de acceso de símbolos que no se confía? ] (../debugger/media/ffr_ituntrustedsymbolpaths.png "FFR_ITUntrustedSymbolPaths")  

 **R:** este mensaje aparece cuando la ruta de acceso de símbolos en el archivo de manifiesto de compilación (\<*ProjectName*>. BuildInfo.config) no se incluye en la lista de rutas de acceso de símbolos de confianza. Puede agregar la ruta de acceso a dicha lista en las opciones del depurador.
