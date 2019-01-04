---
title: 'Tutorial: Depurar una aplicación de SharePoint mediante IntelliTrace | Documentos de Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d2c36d2781e34f85e46fc8a1a56d384bad713399
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865471"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>Tutorial: Depurar una aplicación de SharePoint mediante IntelliTrace

Con IntelliTrace, puede depurar las soluciones de SharePoint más fácilmente. Los depuradores tradicionales solo proporcionan una instantánea de la solución en el momento actual. Sin embargo, puede usar IntelliTrace para revisar los eventos pasados que se produjeron en la solución y el contexto en los que se produjeron, así como navegar hasta el código.

 Este tutorial muestra cómo depurar un proyecto de SharePoint 2010 o SharePoint 2013 en Visual Studio mediante Microsoft Monitoring Agent para recopilar datos de IntelliTrace de las aplicaciones implementadas. Para analizar estos datos, debe usar Visual Studio Enterprise. Este proyecto incorpora un receptor de características que, cuando se activa la característica, agrega una tarea a la lista de tareas y un anuncio a la lista de anuncios. Cuando la característica está desactivada, la tarea se marca como completada y se agrega un segundo anuncio a la lista de anuncios. Sin embargo, el procedimiento contiene un error lógico que evita que el proyecto se ejecute correctamente. Mediante IntelliTrace, se puede localizar y corregir el error.

 **Se aplica a:** La información de este tema se aplica a las soluciones de SharePoint 2010 y SharePoint 2013 que se crearon en Visual Studio.

 En este tutorial se muestran las tareas siguientes:

- [Crear un receptor de características](#BKMK_CreateReceiver)

- [Agregue código al receptor de características](#BKMK_AddCode)

- [El proyecto de prueba](#BKMK_Test1)

- [Recopilar datos de IntelliTrace mediante Microsoft Monitoring Agent](#BKMK_CollectDiagnosticData)

- [Depurar y corregir la solución de SharePoint](#BKMK_DebugSolution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos

Necesita los componentes siguientes para completar este tutorial:

- Ediciones compatibles de Windows y SharePoint.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Crear un receptor de características

Primero se debe crear un proyecto de SharePoint vacío que tiene un receptor de características.

1. Cree un proyecto de solución de SharePoint 2010 o SharePoint 2013 y asígnele el nombre **IntelliTraceTest**.

     El **Asistente de personalización de SharePoint** aparece, en el que puede especificar el sitio de SharePoint para el proyecto y el nivel de confianza de la solución.

2. Elija la **implementar como solución de granja de servidores** botón de opción y, a continuación, elija el **finalizar** botón.

     IntelliTrace sólo funciona en soluciones de granja.

3. En **el Explorador de soluciones**, abra el menú contextual para el **características** nodo y, a continuación, elija **Agregar característica**.

     *Feature1.Feature* aparece.

4. Abra el menú contextual para Feature1.feature y, a continuación, elija **agregar receptor de eventos** para agregar un módulo de código a la característica.

## <a name="add-code-to-the-feature-receiver"></a>Agregue código al receptor de características

Luego, agregue el código a dos métodos del receptor de características: `FeatureActivated` y `FeatureDeactivating`. Estos métodos se activan cada vez que una característica se activa o se desactiva en SharePoint, respectivamente.

1. En la parte superior de la clase `Feature1EventReceiver`, agregue el siguiente código, que declara las variables que especifican el sitio y subsitio de SharePoint:

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

2. Reemplace el método `FeatureActivated` con el código siguiente:

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

3. Reemplace el método `FeatureDeactivating` con el código siguiente:

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

## <a name="test-the-project"></a>El proyecto de prueba

Ahora que el código se agrega al receptor de características y el recopilador de datos se está ejecutando, implemente y ejecute la solución de SharePoint para probar si funciona correctamente.

> [!IMPORTANT]
> Para este ejemplo, se produce un error en el controlador de eventos FeatureDeactivating. Más adelante en este tutorial, encontrará este error mediante el archivo .iTrace que creó el recopilador de datos.

1. Implemente la solución de SharePoint y vuelva a abrir el sitio de SharePoint en un explorador.

     La característica se activa automáticamente, lo que hace que el receptor de características agregue un anuncio y una tarea.

2. Muestre el contenido de las listas Anuncios y Tareas.

     La lista anuncios debe tener un nuevo anuncio denominado **característica activada: IntelliTraceTest_Feature1**, y la lista de tareas debe tener una nueva tarea que se denomina **desactivar característica: IntelliTraceTest_Feature1**. Si falta cualquiera de estos elementos, compruebe si la característica está activada. Si no está activada, actívela.

3. Desactive la característica siguiendo estos pasos:

   1. En el **acciones del sitio** en SharePoint, elija **configuración del sitio**.

   2. En **acciones del sitio**, elija el **administrar características del sitio** vínculo.

   3. Junto a **IntelliTraceTest Feature1**, elija el **Deactivate** botón.

   4. En la página de advertencia, elija la **desactivar esta característica** vínculo.

      El controlador de eventos FeatureDeactivating() produce un error.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Recopilar datos de IntelliTrace mediante Microsoft Monitoring Agent

Si instala a Microsoft Monitoring Agent en el sistema que se está ejecutando SharePoint, puede depurar las soluciones de SharePoint mediante el uso de datos que es más específicos que la información genérica que devuelve IntelliTrace. El agente funciona fuera de Visual Studio mediante cmdlets de PowerShell para capturar información de depuración mientras se ejecuta la solución de SharePoint.

> [!NOTE]
> La información de configuración de esta sección es específica de este ejemplo. Para obtener más información sobre otras opciones de configuración, consulte [mediante el recolector independiente IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

1. En el equipo que ejecuta SharePoint, [configurar Microsoft Monitoring Agent y empezar a supervisar la solución](../debugger/using-the-intellitrace-stand-alone-collector.md).

2. Desactive la característica:

   1. En el **acciones del sitio** en SharePoint, elija **configuración del sitio**.

   2. En **acciones del sitio**, elija el **administrar características del sitio** vínculo.

   3. Junto a **IntelliTraceTest Feature1**, elija el **Deactivate** botón.

   4. En la página de advertencia, elija la **desactivar esta característica** vínculo.

      Se produce un error; en este caso, se debe al error que se produce en el controlador de eventos FeatureDeactivating().

3. En la ventana de PowerShell, ejecute el [Stop-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) comando para crear el archivo. iTrace, detenga la supervisión y reiniciar la solución de SharePoint.

     **Stop-WebApplicationMonitoring***"\<SharePointSite >\\< SharePointAppName\>"*

## <a name="debug-and-fix-the-sharepoint-solution"></a>Depurar y corregir la solución de SharePoint

Ahora puede ver el archivo de registro de IntelliTrace en Visual Studio para buscar y corregir el error en la solución de SharePoint.

1. En la carpeta del \IntelliTraceLogs, abra el archivo .iTrace en Visual Studio.

     El **resumen de IntelliTrace** aparece la página. Dado que no se controló el error, un identificador de correlación (GUID) de SharePoint aparece en el área de la excepción no controlada de la **Analysis** sección. Elija la **pila de llamadas** botón si desea ver la pila de llamadas donde se produjo el error.

2. Elija la **depurar excepción** botón.

     Si se le solicita, cargue los archivos de símbolos. En el **IntelliTrace** ventana, se resalta la excepción como "producida: Se ha producido un error grave! ".

     En la ventana IntelliTrace, elija la excepción para mostrar el código que produjo un error.

3. Corrija el error al abrir la solución de SharePoint y, a continuación, marcar como comentario o quitando la **throw** instrucción en la parte superior del procedimiento de FeatureDeactivating().

4. Recompile la solución en Visual Studio y, a continuación, vuelva a implementarla en SharePoint.

5. Desactive la característica siguiendo estos pasos:

    1. En el **acciones del sitio** en SharePoint, elija **configuración del sitio**.

    2. En **acciones del sitio**, elija el **administrar características del sitio** vínculo.

    3. Junto a **IntelliTraceTest Feature1**, elija el **Deactivate** botón.

    4. En la página de advertencia, elija la **desactivar esta característica** vínculo.

6. Abra la lista de tareas y compruebe que la **estado** valor de la tarea desactivada es "completada" y su **% completado** valor es 100%.

     El código se ejecuta ahora correctamente.

## <a name="see-also"></a>Vea también

- [Comprobar y depurar el código de SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [Tutorial: Comprobar SharePoint código utilizando pruebas unitarias](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))