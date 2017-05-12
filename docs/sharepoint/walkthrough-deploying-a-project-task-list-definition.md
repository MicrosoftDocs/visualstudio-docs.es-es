---
title: "Tutorial: Implementar una definici&#243;n de lista de tareas de proyecto"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, implementar"
ms.assetid: 18b62016-ed30-4dd1-9dfc-0d7e82c6767f
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Tutorial: Implementar una definici&#243;n de lista de tareas de proyecto
  Este tutorial muestra cómo utilizar [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] para crear, personalizar, depurar, y para implementar una lista de SharePoint para realizar tareas del proyecto.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   [Crear una lista de SharePoint](#CreatingListDef).  
  
-   [Crear una lista de SharePoint](#CreatingListDef).  
  
-   [Agregar un controlador de eventos](#AddEventRcvr).  
  
-   [Personalizar la característica Lista de tareas de proyecto](#CustomizeFeature)  
  
-   [Compilar y probar la lista de tareas del proyecto](#BuildTest).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Microsoft Windows y SharePoint.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)] o una edición de Visual Studio Application Lifecycle Management \(ALM\).  
  
##  <a name="CreatingListDef"></a> Crear una lista de SharePoint  
 Cree un proyecto de lista de SharePoint y asociar la definición a tareas.  
  
#### Para crear un proyecto de lista de SharePoint  
  
1.  Abra el cuadro de diálogo de **Nuevo proyecto** , expanda el nodo de **sharepoint** y, a continuación el nodo de **2010** .  
  
2.  En el panel de **Plantillas** , elija la plantilla de **SharePoint 2010 Project** , denomine el proyecto Listatareasproyecto, y elija el botón de **Aceptar** .  
  
     Aparece el **Asistente para personalización de SharePoint**.  
  
3.  Especifique el sitio de SharePoint local que se utiliza para depurar, elija el botón de opción de **Implementar como solución de granja de servidores** , y después elija el botón de **Finalizar** .  
  
4.  Abrir el menú contextual para el proyecto y, a continuación **Add**, **Nuevo elemento**.  
  
5.  En el panel de **Plantillas** , elija la plantilla de **list** , y elija el botón de **Add** .  
  
     Aparece el **Asistente para personalización de SharePoint**.  
  
6.  En el cuadro de **¿Qué nombre desea mostrar en la lista?** , escriba la lista de tareas del proyecto.  
  
7.  Elija el botón de opción de **Cree una lista no personalizable basada en un tipo enumerado existente de** y, a continuación, en la lista, elija **Tareas**, y después elija el botón de **Finalizar** .  
  
     La lista, la característica, y el paquete aparecerán en **Explorador de soluciones**.  
  
##  <a name="AddEventRcvr"></a> Agregar un controlador de eventos  
 En la lista de tareas, puede agregar un receptor de eventos que establece automáticamente la fecha de vencimiento y la descripción de la tarea.  En el procedimiento siguiente se agrega un controlador de eventos simple a la instancia de la lista como un receptor de eventos.  
  
#### Para agregar un receptor de eventos  
  
1.  Abra el menú contextual para el nodo del proyecto, elija **Agregar** y, a continuación, elija **Nuevo elemento**.  
  
2.  En la lista de plantillas de SharePoint, elija la plantilla de **receptor de eventos** , y después denomínela **ProjectTaskListEventReceiver**.  
  
     Aparece el **Asistente para personalización de SharePoint**.  
  
3.  En la página de **Elegir configuración del receptor de eventos** , elija **Eventos de elementos de lista** como el receptor de eventos escribir en la lista de **El tipo de receptor de eventos desea** .  
  
4.  En la lista de **El elemento debe ser el origen de eventos** , elija **Tareas**.  
  
5.  En la lista de eventos para controlar, active la casilla situada junto a **Se agregó un elemento**, y después elija el botón de **Finalizar** .  
  
     Un nuevo nodo de receptor de eventos se agrega al proyecto con un archivo de código que se denomina **ReceptorEventosListaTareasProyecto**.  
  
6.  Agregue código al método `ItemAdded` del archivo de código **ReceptorEventosListaTareasProyecto**.  Cada vez que se agrega una nueva tarea, se le agrega una fecha de vencimiento y una descripción predeterminadas.  La fecha de vencimiento predeterminada es el 1 de julio de 2009.  
  
     [!code-csharp[SPProjectTaskList#1](../snippets/csharp/VS_Snippets_OfficeSP/spprojecttasklist/cs/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]
     [!code-vb[SPProjectTaskList#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spprojecttasklist/vb/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]  
  
##  <a name="CustomizeFeature"></a> Personalizar la característica Lista de tareas de proyecto  
 Al crear una solución de SharePoint, Visual Studio crea automáticamente las características de los elementos predeterminados del proyecto.  Puede personalizar la configuración de la lista de tareas de proyecto para el sitio de SharePoint mediante el diseñador de características.  
  
#### Para personalizar la característica de lista de tareas de proyecto  
  
1.  En el **Explorador de soluciones**, expanda **Características**.  
  
2.  Abrir el menú contextual para **Característica1**y, a continuación **Diseñador de vistas**.  
  
3.  En el cuadro de **title** , entre en **Característica de la lista de tareas de proyecto**.  
  
4.  En la lista de **Ámbito** , elija **web**.  
  
5.  En la ventana de **Propiedades** , entre en **1.0.0.0** como valor para la propiedad de **Versión** .  
  
##  <a name="CustomizePackage"></a> Personalizar el paquete de lista de tareas de proyecto  
 Al crear un proyecto SharePoint, Visual Studio agrega automáticamente las características que contienen los elementos predeterminados del proyecto al paquete.  Puede personalizar la configuración de la lista de tareas de proyecto para el sitio de SharePoint mediante el diseñador de paquetes.  
  
#### Para personalizar el paquete de lista de tareas de proyecto  
  
1.  En **soluciónExplorador**, abra el menú contextual para **Paquete**y, a continuación **Diseñador de vistas**.  
  
2.  En el cuadro de **Name** , entre en **ProjectTaskListPackage**.  
  
3.  Active la casilla de **Reiniciar servidor web** .  
  
##  <a name="BuildTest"></a> Compilar y probar la lista de tareas del proyecto  
 Cuando se ejecuta el proyecto, se abre el sitio de SharePoint.  Sin embargo, debe navegar manualmente hasta la ubicación de la lista de tareas.  
  
#### Para probar la lista de tareas del proyecto  
  
1.  Elija la tecla F5 para compilar e implementar la lista de tareas del proyecto.  
  
     Se abre el sitio de SharePoint.  
  
2.  Elija la ficha de **Domicilio** .  
  
3.  En la barra lateral izquierda, elija el vínculo de **Lista de tareas de proyecto** .  
  
     Aparece la página Lista de tareas del proyecto.  
  
4.  En la pestaña de **Enumera las herramientas** , elija la ficha de **Elementos** .  
  
5.  En el grupo de **Elementos** , elija el botón de **Nuevo elemento** .  
  
6.  En el cuadro de texto de **title** , escriba Task1.  
  
7.  Elija el botón de **Guardar** .  
  
     Una vez estado actualizado el sitio, la tarea **Tarea1** aparece con una fecha de vencimiento de 1\/7\/2009.  
  
8.  Elija **Task1**.  
  
     Aparece la vista detallada de la tarea y la descripción muestra "Esta es una tarea crítica".  
  
##  <a name="Deploy"></a> Implementar la lista de tareas de proyecto  
 Después de compilar y probar la lista de tareas del proyecto, puede implementarla en el *sistema local* o en un *sistema remoto*.  El sistema local es el mismo equipo donde se desarrolló la solución, mientras que un sistema remoto es un equipo diferente.  
  
#### Para implementar la lista de tareas del proyecto en el sistema local  
  
1.  En la barra de menús de Visual Studio, elija **Compilación**, **Implementar solución**.  
  
     Visual Studio recicla el grupo de aplicaciones IIS, contrae las versiones existentes de la solución, copia el archivo de paquete de solución \(.wsp\) en SharePoint y, a continuación, activa sus características.  Ahora puede usar la solución de SharePoint.  Para obtener más información acerca de los pasos de configuración de la implementación, vea [Cómo: Modificar una configuración de implementación de SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  
  
#### Para implementar la lista de tareas del proyecto en un sistema remoto  
  
1.  En la barra de menús de Visual Studio, elija **Compilación**, **Publicar**.  
  
2.  En el cuadro de diálogo de **Publicar** , elija el botón de opción de **Publicar en el sistema de archivos** .  
  
     Puede cambiar la ubicación de destino en el cuadro de diálogo de **Publicar** eligiendo el botón de puntos ![Icono Puntos suspensivos](../sharepoint/media/ellipsisicon.png "Icono Puntos suspensivos") suspensivos y después navegar a otra ubicación.  
  
3.  Elija el botón de **Publicar** .  
  
     Un archivo .wsp se crea para la solución.  
  
4.  Copie el archivo .wsp en el sistema de SharePoint remoto.  
  
5.  Use el comando de PowerShell `Add-SPUserSolution` para instalar el paquete en la instalación de SharePoint remota. \(Para las soluciones de granja de servidores, use el comando `Add-SPSolution`\).  
  
     Por ejemplo, `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.  
  
6.  Use el comando de PowerShell `Install-SPUserSolution` para implementar la solución. \(Para las soluciones de granja de servidores, use el comando `Install-SPSolution`\).  
  
     Por ejemplo, `Install-SPUserSolution –Identity ProjectTaskList.wsp –Site http://NewSiteName`.  
  
     Para obtener más información sobre la implementación remota, vea [Con las Soluciones](http://go.microsoft.com/fwlink/?LinkId=217680) y [Agregar y Soluciones de implementación con PowerShell en SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=217682).  
  
## Pasos siguientes  
 Puede obtener más información sobre cómo personalizar e implementar las soluciones de SharePoint de los temas siguientes:  
  
-   [Tutorial: Crear una lista, tipo de contenido y columna de sitio para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)  
  
-   [Cómo: Crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)  
  
-   [Windows PowerShell para SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)  
  
## Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  