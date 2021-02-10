---
title: Depurar aplicaciones de SharePoint con IntelliTrace
description: Use IntelliTrace para depurar y corregir más fácilmente las aplicaciones de SharePoint. Crear y agregar código a un receptor de características. Pruebe el proyecto. Recopilar datos de IntelliTrace.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e2ce8bc2c493d59b8a06a64ff69838e828315bf2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952660"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>Tutorial: depurar una aplicación de SharePoint mediante IntelliTrace

Con IntelliTrace, puede depurar las soluciones de SharePoint más fácilmente. Los depuradores tradicionales solo proporcionan una instantánea de la solución en el momento actual. Sin embargo, puede usar IntelliTrace para revisar los eventos pasados que se produjeron en la solución y el contexto en los que se produjeron, así como navegar hasta el código.

 En este tutorial se muestra cómo depurar un proyecto de SharePoint 2010 o 2013 de SharePoint en Visual Studio mediante Microsoft Monitoring Agent para recopilar datos de IntelliTrace de aplicaciones implementadas. Para analizar los datos, debe usar Visual Studio Enterprise. Este proyecto incorpora un receptor de características que, cuando se activa la característica, agrega una tarea a la lista de tareas y un anuncio a la lista de anuncios. Cuando la característica está desactivada, la tarea se marca como completada y se agrega un segundo anuncio a la lista de anuncios. Sin embargo, el procedimiento contiene un error lógico que evita que el proyecto se ejecute correctamente. Mediante IntelliTrace, se puede localizar y corregir el error.

 **Se aplica a:** La información de este tema se aplica a las soluciones de SharePoint 2010 y SharePoint 2013 que se crearon en Visual Studio.

 En este tutorial se muestran las tareas siguientes:

- [Crear un receptor de características](#create-a-feature-receiver)

- [Agregar código al receptor de características](#add-code-to-the-feature-receiver)

- [Probar el proyecto](#test-the-project)

- [Recopilar datos de IntelliTrace mediante Microsoft Monitoring Agent](#collect-intellitrace-data-by-using-microsoft-monitoring-agent)

- [Depurar y corregir la solución de SharePoint](#debug-and-fix-the-sharepoint-solution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos

Necesitará los componentes siguientes para completar este tutorial:

- Ediciones compatibles de Windows y SharePoint.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Crear un receptor de características

Primero se debe crear un proyecto de SharePoint vacío que tiene un receptor de características.

1. Cree un proyecto de solución de SharePoint 2010 o SharePoint 2013 y asígnele el nombre **IntelliTraceTest**.

     Aparece el **Asistente para la personalización de SharePoint** , en el que puede especificar el sitio de SharePoint para el proyecto y el nivel de confianza de la solución.

2. Elija el botón de opción **implementar como solución de granja de servidores** y, después, elija el botón **Finalizar** .

     IntelliTrace sólo funciona en soluciones de granja.

3. En **Explorador de soluciones**, abra el menú contextual del nodo **características** y, a continuación, elija **Agregar característica**.

     *Feature1. Feature* aparece.

4. Abra el menú contextual de Feature1. Feature y, a continuación, elija **Agregar receptor de eventos** para agregar un módulo de código a la característica.

## <a name="add-code-to-the-feature-receiver"></a>Agregar código al receptor de características

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

2. Reemplace el método `FeatureActivated` por el código siguiente:

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

3. Reemplace el método `FeatureDeactivating` por el código siguiente:

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

## <a name="test-the-project"></a>Prueba del proyecto

Ahora que el código se agrega al receptor de características y el recopilador de datos se está ejecutando, implemente y ejecute la solución de SharePoint para probar si funciona correctamente.

> [!IMPORTANT]
> Para este ejemplo, se produce un error en el controlador de eventos FeatureDeactivating. Más adelante en este tutorial, encontrará este error mediante el archivo .iTrace que creó el recopilador de datos.

1. Implemente la solución de SharePoint y vuelva a abrir el sitio de SharePoint en un explorador.

     La característica se activa automáticamente, lo que hace que el receptor de características agregue un anuncio y una tarea.

2. Muestre el contenido de las listas Anuncios y Tareas.

     La lista de anuncios debe tener un nuevo anuncio denominado **característica activada: IntelliTraceTest_Feature1**, y la lista de tareas debe tener una nueva tarea denominada **desactivar característica: IntelliTraceTest_Feature1**. Si falta cualquiera de estos elementos, compruebe si la característica está activada. Si no está activada, actívela.

3. Desactive la característica siguiendo estos pasos:

   1. En el menú **acciones del sitio** de SharePoint, elija Configuración del **sitio**.

   2. En **acciones del sitio**, elija el vínculo **administrar las características del sitio** .

   3. Junto a **IntelliTraceTest Feature1**, elija el botón **desactivar** .

   4. En la página ADVERTENCIA, elija el vínculo **desactivar esta característica** .

      El controlador de eventos FeatureDeactivating() produce un error.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Recopilar datos de IntelliTrace mediante Microsoft Monitoring Agent

Si instala Microsoft Monitoring Agent en el sistema que ejecuta SharePoint, puede depurar las soluciones de SharePoint mediante el uso de datos más específicos que la información genérica que devuelve IntelliTrace. El agente funciona fuera de Visual Studio mediante cmdlets de PowerShell para capturar información de depuración mientras se ejecuta la solución de SharePoint.

> [!NOTE]
> La información de configuración de esta sección es específica de este ejemplo. Para obtener más información sobre otras opciones de configuración, vea [usar el recopilador](../debugger/using-the-intellitrace-stand-alone-collector.md)independiente de IntelliTrace.

1. En el equipo que ejecuta SharePoint, [configure Microsoft Monitoring Agent y empiece a supervisar la solución](../debugger/using-the-intellitrace-stand-alone-collector.md).

2. Desactive la característica:

   1. En el menú **acciones del sitio** de SharePoint, elija Configuración del **sitio**.

   2. En **acciones del sitio**, elija el vínculo **administrar las características del sitio** .

   3. Junto a **IntelliTraceTest Feature1**, elija el botón **desactivar** .

   4. En la página ADVERTENCIA, elija el vínculo **desactivar esta característica** .

      Se produce un error; en este caso, se debe al error que se produce en el controlador de eventos FeatureDeactivating().

3. En la ventana de PowerShell, ejecute el comando [Stop-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) para crear el archivo. iTrace, detenga la supervisión y reinicie la solución de SharePoint.

     **Stop-WebApplicationMonitoring***" \<SharePointSite> \\<SharePointAppName \> "*  

## <a name="debug-and-fix-the-sharepoint-solution"></a>Depurar y corregir la solución de SharePoint

Ahora puede ver el archivo de registro de IntelliTrace en Visual Studio para buscar y corregir el error en la solución de SharePoint.

1. En la carpeta del \IntelliTraceLogs, abra el archivo .iTrace en Visual Studio.

     Aparece la página **Resumen de IntelliTrace** . Dado que no se ha controlado el error, aparece un identificador de correlación de SharePoint (un GUID) en el área de excepción no controlada de la sección de **análisis** . Elija el botón **pila de llamadas** si desea ver la pila de llamadas en la que se produjo el error.

2. Elija el botón **depurar excepción** .

     Si se le solicita, cargue los archivos de símbolos. En la ventana **IntelliTrace** , la excepción se resalta como "producida: se ha producido un error grave".

     En la ventana IntelliTrace, elija la excepción para mostrar el código que produjo un error.

3. Para corregir el error, abra la solución de SharePoint y, a continuación, comente o quite la instrucción **Throw** en la parte superior del procedimiento FeatureDeactivating ().

4. Recompile la solución en Visual Studio y, a continuación, vuelva a implementarla en SharePoint.

5. Desactive la característica siguiendo estos pasos:

    1. En el menú **acciones del sitio** de SharePoint, elija Configuración del **sitio**.

    2. En **acciones del sitio**, elija el vínculo **administrar las características del sitio** .

    3. Junto a **IntelliTraceTest Feature1**, elija el botón **desactivar** .

    4. En la página ADVERTENCIA, elija el vínculo **desactivar esta característica** .

6. Abra la lista de tareas y compruebe que el valor de **Estado** de la tarea de desactivación es "completado" y su valor **% completado** es 100%.

     El código se ejecuta ahora correctamente.

## <a name="see-also"></a>Vea también

- [Comprobar y depurar código de SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [Tutorial: comprobar el código de SharePoint mediante pruebas unitarias](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))