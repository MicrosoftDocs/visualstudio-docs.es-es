---
title: "Tutorial: Depurar una aplicaci&#243;n de SharePoint mediante IntelliTrace | Microsoft Docs"
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
helpviewer_keywords: 
  - "IntelliTrace [desarrollo de SharePoint en Visual Studio]"
  - "recolector de datos independiente"
  - "Desarrollo de SharePoint en Visual Studio, IntelliTrace"
  - "recolector de datos"
  - "IntelliTrace"
ms.assetid: 4bd80d2f-f680-4bf4-81c3-f14e8185f6a4
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Tutorial: Depurar una aplicaci&#243;n de SharePoint mediante IntelliTrace
  Con IntelliTrace, puede depurar las soluciones de SharePoint más fácilmente.  Los depuradores tradicionales solo proporcionan una instantánea de la solución en el momento actual.  Sin embargo, puede usar IntelliTrace para revisar los eventos pasados que se produjeron en la solución y el contexto en los que se produjeron, así como navegar hasta el código.  
  
 En este tutorial se muestra cómo depurar un proyecto de SharePoint 2010 o de SharePoint 2013 en Visual Studio Ultimate mediante Microsoft Monitoring Agent para recopilar datos de IntelliTrace de aplicaciones implementadas.  Para analizar estos datos, se debe utilizar Visual Studio Ultimate.  Este proyecto incorpora un receptor de características que, cuando se activa la característica, agrega una tarea a la lista de tareas y un anuncio a la lista de anuncios.  Cuando la característica está desactivada, la tarea se marca como completada y se agrega un segundo anuncio a la lista de anuncios.  Sin embargo, el procedimiento contiene un error lógico que evita que el proyecto se ejecute correctamente.  Mediante IntelliTrace, se puede localizar y corregir el error.  
  
 **Se aplica a:** la información en este tema se aplica a las soluciones de SharePoint 2010 y a SharePoint 2013 creadas en Visual Studio.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   [Crear un receptor de características](#BKMK_CreateReceiver)  
  
-   [Agregar código al receptor de características](#BKMK_AddCode)  
  
-   [Probar el proyecto](#BKMK_Test1)  
  
-   [Recopilar datos de IntelliTrace mediante Microsoft Monitoring Agent](#BKMK_CollectDiagnosticData)  
  
-   [Depurar y corregir la solución de SharePoint](#BKMK_DebugSolution)  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Windows y SharePoint.  Vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio Ultimate.  
  
##  <a name="BKMK_CreateReceiver"></a> Crear un receptor de características  
 Primero se debe crear un proyecto de SharePoint vacío que tiene un receptor de características.  
  
#### Para crear un receptor de características  
  
1.  Cree el proyecto de solución de SharePoint 2010 o SharePoint 2013 y asígnele el nombre IntelliTraceTest.  
  
     Aparece el **Asistente para personalización de SharePoint**, en el que puede especificar el sitio de SharePoint para el proyecto y el nivel de confianza de la solución.  
  
2.  Elija el botón de opción de **Implementar como solución de granja de servidores** y después elija el botón de **Finalizar**.  
  
     IntelliTrace sólo funciona en soluciones de granja.  
  
3.  En el **Explorador de soluciones**, abra el menú contextual para el nodo **Características** y, a continuación, elija **Agregar característica**.  
  
     Aparece Feature1.feature.  
  
4.  Abra el menú contextual para Feature1.feature y, a continuación, elija **Agregar receptor de eventos** para agregar un módulo de código a la característica.  
  
##  <a name="BKMK_AddCode"></a> Agregar código al receptor de características  
 Luego, agregue el código a dos métodos del receptor de características: `FeatureActivated` y `FeatureDeactivating`.  Estos métodos se activan cada vez que una característica se activa o se desactiva en SharePoint, respectivamente.  
  
#### Para agregar código al receptor de características  
  
1.  En la parte superior de la clase `Feature1EventReceiver`, agregue el siguiente código, que declara las variables que especifican el sitio y subsitio de SharePoint:  
  
    ```vb  
    ' SharePoint site and subsite.  
    Private siteUrl As String = "http://localhost"  
    Private webUrl As String = "/"  
    ```  
  
    ```csharp  
    // SharePoint site and subsite.  
    private string siteUrl = "http://localhost";  
    private string webUrl = "/";  
    ```  
  
2.  Reemplace el método `FeatureActivated` con el código siguiente:  
  
    ```vb  
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
                    Dim taskList As SPList = web.Lists("Tasks")  
  
                    ' Add an announcement to the Announcements list.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()  
                    listItem.Update()  
  
                    ' Add a task to the Task list.  
                    Dim newTask As SPListItem = taskList.Items.Add()  
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    newTask.Update()  
                End Using  
            End Using  
  
        Catch e As Exception  
            Console.WriteLine("Error: " & e.ToString())  
        End Try  
  
    End Sub  
    ```  
  
    ```csharp  
    public override void FeatureActivated(SPFeatureReceiverProperties properties)  
    {  
        try  
        {  
            using (SPSite site = new SPSite(siteUrl))  
            {  
                using (SPWeb web = site.OpenWeb(webUrl))  
                {  
                    // Reference the lists.  
                    SPList announcementsList = web.Lists["Announcements"];  
                    SPList taskList = web.Lists["Tasks"];  
  
                    // Add an announcement to the Announcements list.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();  
                    listItem.Update();  
  
                    // Add a task to the Task list.  
                    SPListItem newTask = taskList.Items.Add();  
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;  
                    newTask.Update();  
                }  
            }  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
  
    }  
    ```  
  
3.  Reemplace el método `FeatureDeactivating` con el código siguiente:  
  
    ```vb  
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)  
        ' The following line induces an error to demonstrate debugging.  
        ' Remove this line later for proper operation.  
        Throw New System.InvalidOperationException("Serious error occurred!")  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim taskList As SPList = web.Lists("Tasks")  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
  
                    ' Add an announcement that the feature was deactivated.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()  
                    listItem.Update()  
  
                    ' Find the task that the feature receiver added to the Task list when the  
                    ' feature was activated.  
                    Dim qry As New SPQuery()  
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"  
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)  
  
                    For Each taskItem As SPListItem In taskItems  
                        ' Mark the task as complete.  
                        taskItem("PercentComplete") = 1  
                        taskItem("Status") = "Completed"  
                        taskItem.Update()  
                    Next  
                End Using  
  
            End Using  
  
        Catch e As Exception  
            Console.WriteLine("Error: " & e.ToString())  
        End Try  
  
    End Sub  
    ```  
  
    ```csharp  
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)  
    {  
        // The following line induces an error to demonstrate debugging.  
        // Remove this line later for proper operation.  
        throw new System.InvalidOperationException("A serious error occurred!");   
        try  
        {  
            using (SPSite site = new SPSite(siteUrl))  
            {  
                using (SPWeb web = site.OpenWeb(webUrl))  
                {  
                    // Reference the lists.  
                    SPList taskList = web.Lists["Tasks"];  
                    SPList announcementsList = web.Lists["Announcements"];  
  
                    // Add an announcement that the feature was deactivated.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();  
                    listItem.Update();  
  
                    // Find the task that the feature receiver added to the Task list when the  
                    // feature was activated.  
                    SPQuery qry = new SPQuery();  
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";  
                    SPListItemCollection taskItems = taskList.GetItems(qry);  
  
                    foreach (SPListItem taskItem in taskItems)  
                    {  
                        // Mark the task as complete.  
                        taskItem["PercentComplete"] = 1;  
                        taskItem["Status"] = "Completed";  
                        taskItem.Update();  
                    }  
                }  
            }  
  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
    }  
    ```  
  
##  <a name="BKMK_Test1"></a> Probar el proyecto  
 Ahora que el código se agrega al receptor de características y el recopilador de datos se está ejecutando, implemente y ejecute la solución de SharePoint para probar si funciona correctamente.  
  
> [!IMPORTANT]  
>  Para este ejemplo, se produce un error en el controlador de eventos FeatureDeactivating.  Más adelante en este tutorial, encontrará este error mediante el archivo .iTrace que creó el recopilador de datos.  
  
#### Para probar el proyecto  
  
1.  Implemente la solución de SharePoint y vuelva a abrir el sitio de SharePoint en un explorador.  
  
     La característica se activa automáticamente, lo que hace que el receptor de características agregue un anuncio y una tarea.  
  
2.  Muestre el contenido de las listas Anuncios y Tareas.  
  
     La lista Anuncios debe tener un nuevo anuncio denominado **Característica activada: IntelliTraceTest\_Feature1** y la lista de Tareas debe tener una nueva tarea denominada **Desactivar característica: IntelliTraceTest\_Feature1**.  Si falta cualquiera de estos elementos, compruebe si la característica está activada.  Si no está activada, actívela.  
  
3.  Desactive la característica siguiendo estos pasos:  
  
    1.  En el menú **Acciones del sitio** en SharePoint, elija **Configuración del sitio**.  
  
    2.  En **Acciones del sitio**, elija el vínculo **Administrar las características del sitio**.  
  
    3.  Junto a **IntelliTraceTest Feature1**, elija el botón **Desactivar**.  
  
    4.  En la página Advertencia, elija el vínculo **Desactivar esta característica**.  
  
     El controlador de eventos FeatureDeactivating\(\) produce un error.  
  
##  <a name="BKMK_CollectDiagnosticData"></a> Recopilar datos de IntelliTrace mediante Microsoft Monitoring Agent  
 Si instala Microsoft Monitoring Agent en el sistema que ejecuta SharePoint, puede depurar las soluciones de SharePoint mediante el uso de datos que son más específicos que la información genérica que devuelve IntelliTrace.  El agente funciona fuera de Visual Studio mediante cmdlets de PowerShell para capturar información de depuración mientras se ejecuta la solución de SharePoint.  
  
> [!NOTE]  
>  La información de configuración de esta sección es específica de este ejemplo.  Para obtener más información sobre otras opciones de configuración, vea [Usar el recopilador independiente de IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
1.  En el equipo que está ejecutando SharePoint, [configure Microsoft Monitoring Agent y comience a supervisar la solución](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
2.  Desactive la característica:  
  
    1.  En el menú **Acciones del sitio** en SharePoint, elija **Configuración del sitio**.  
  
    2.  En **Acciones del sitio**, elija el vínculo **Administrar las características del sitio**.  
  
    3.  Junto a **IntelliTraceTest Feature1**, elija el botón **Desactivar**.  
  
    4.  En la página Advertencia, elija el vínculo **Desactivar esta característica**.  
  
     Se produce un error; en este caso, se debe al error que se produce en el controlador de eventos FeatureDeactivating\(\).  
  
3.  En la ventana PowerShell, ejecute el comando [Stop\-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) para crear el archivo .iTrace, detenga la supervisión y reinicie la solución de SharePoint.  
  
     **Stop\-WebApplicationMonitoring**  *"\<SharePointSite\>\\\<SharePointAppName\>"*  
  
##  <a name="BKMK_DebugSolution"></a> Depurar y corregir la solución de SharePoint  
 Ahora puede ver el archivo de registro de IntelliTrace en Visual Studio para buscar y corregir el error en la solución de SharePoint.  
  
#### Para depurar y corregir la solución de SharePoint  
  
1.  En la carpeta del \\IntelliTraceLogs, abra el archivo .iTrace en Visual Studio.  
  
     Aparece la página **Resumen de IntelliTrace**.  Puesto que el error no se ha controlado, aparece un identificador de correlación de SharePoint \(un GUID\) en el área de la excepción no controlada de la sección **Análisis**.  Elija el botón **Pila de llamadas** si desea ver la pila de llamadas donde se produjo el error.  
  
2.  Elija el botón **Depurar excepción**.  
  
     Si se le solicita, cargue los archivos de símbolos.  En la ventana **IntelliTrace**, la excepción resalta un mensaje advirtiendo que se produjo un error grave.  
  
     En la ventana IntelliTrace, elija la excepción para mostrar el código que produjo un error.  
  
3.  Corrija el error abriendo la solución de SharePoint y después marque como comentario o quite la instrucción **throw** en la parte superior del procedimiento de FeatureDeactivating\(\).  
  
4.  Recompile la solución en Visual Studio y, a continuación, vuelva a implementarla en SharePoint.  
  
5.  Desactive la característica siguiendo estos pasos:  
  
    1.  En el menú **Acciones del sitio** en SharePoint, elija **Configuración del sitio**.  
  
    2.  En **Acciones del sitio**, elija el vínculo **Administrar las características del sitio**.  
  
    3.  Junto a **IntelliTraceTest Feature1**, elija el botón **Desactivar**.  
  
    4.  En la página Advertencia, elija el vínculo **Desactivar esta característica**.  
  
6.  Abra la lista Tareas y compruebe que el valor **Estado** de la tarea Desactivada es "Completada" y el valor **% completado** es 100 %.  
  
     El código se ejecuta ahora correctamente.  
  
## Vea también  
 [Comprobar y depurar código de SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)   
 [Uso de IntelliTrace](../debugger/intellitrace.md)   
 [Tutorial: Comprobar código de SharePoint mediante pruebas unitarias](http://msdn.microsoft.com/es-es/3d2c4aaf-3cb5-4825-b21b-f10222abe818)  
  
  