---
title: 'Tutorial: generar perfiles de una aplicación de SharePoint | Microsoft Docs'
description: En este tutorial, use las herramientas de generación de perfiles de Visual Studio para optimizar el rendimiento de una aplicación de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 66e19f7744a56d147fb0760c6f20254ea4308603
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970098"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>Tutorial: generar perfiles de una aplicación de SharePoint
  En este tutorial se muestra cómo usar las herramientas de generación de perfiles de Visual Studio para optimizar el rendimiento de una aplicación de SharePoint. La aplicación de ejemplo es un receptor de eventos de características de SharePoint que contiene un bucle inactivo que merma el rendimiento del receptor de eventos de características. El generador de perfiles de Visual Studio le permite localizar y eliminar la parte más costosa (rendimiento más lento) del proyecto, también conocida como la *ruta de acceso activa*.

 En este tutorial se muestran las siguientes tareas:

- [Agregar una característica y un receptor de eventos de características](#add-a-feature-and-feature-event-receiver).

- [Configurar e implementar la aplicación de SharePoint](#configure-and-deploy-the-sharepoint-application).

- [Ejecute la aplicación de SharePoint](#run-the-sharepoint-application).

- [Ver e interpretar los resultados del perfil](#view-and-interpret-the-profile-results).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- Ediciones compatibles de Microsoft Windows y SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-sharepoint-project"></a>Crear un proyecto de SharePoint
 Primero, cree un proyecto de SharePoint.

### <a name="to-create-a-sharepoint-project"></a>Para crear un proyecto de SharePoint

1. En la barra de menús, elija **archivo**  >  **nuevo**  >  **proyecto** para mostrar el cuadro de diálogo **nuevo proyecto** .

2. Expanda el nodo **SharePoint** en **Visual C#** o **Visual Basic** y, a continuación, elija el nodo **2010** .

3. En el panel plantillas, elija la plantilla de **proyecto de SharePoint 2010** .

4. En el cuadro **nombre** , escriba **profilete** y, a continuación, elija el botón **Aceptar** .

    Aparece el **Asistente para la personalización de SharePoint** .

5. En la página **especifique el sitio y el nivel de seguridad de la depuración** , escriba la dirección URL del sitio del servidor de SharePoint en el que desea depurar la definición del sitio o use la ubicación predeterminada (<em>nombre del sistema</em>http:///).

6. En la sección **¿cuál es el nivel de confianza de esta solución de SharePoint?** , elija el botón de opción **implementar como solución de granja de servidores** .

    De momento solo puede generar perfiles de soluciones de granja de servidores. Para obtener más información sobre las soluciones en espacio aislado frente a las soluciones de granja, consulte [consideraciones sobre soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).

7. Elija el botón **Finalizar**. El proyecto aparece en **Explorador de soluciones**.

## <a name="add-a-feature-and-feature-event-receiver"></a>Agregar una característica y un receptor de eventos de características
 A continuación, agregue una característica al proyecto junto con un receptor de eventos para esa característica. Este receptor de eventos contendrá el código cuyo perfil se va a generar.

### <a name="to-add-a-feature-and-feature-event-receiver"></a>Para agregar una característica y un receptor de eventos de características

1. En **Explorador de soluciones**, abra el menú contextual del nodo **características** , elija **Agregar característica** y deje el nombre en el valor predeterminado, **Feature1**.

2. En **Explorador de soluciones**, abra el menú contextual de **Feature1** y, a continuación, elija **Agregar receptor de eventos**.

     Esto agrega un archivo de código a la característica con varios controladores de eventos con comentarios y abre el archivo para edición.

3. En la clase del receptor de eventos, agregue las siguientes declaraciones de variable.

    ```vb
    ' SharePoint site/subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site/subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

4. Reemplace el procedimiento `FeatureActivated` por el siguiente código.

    ```vb
    Public Overrides Sub FeatureActivated(properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add a new announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    ' Waste some time.
                    TimeCounter()
                    ' Update the list.
                    listItem.Update()
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

                    // Add a new announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " +
    DateTime.Now.ToString();
                    // Waste some time.
                    TimeCounter();
                    // Update the list.
                    listItem.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

5. Agregue el siguiente procedimiento debajo del `FeatureActivated` procedimiento.

    ```vb

    Public Sub TimeCounter()
        Dim result As Integer
        For i As Integer = 0 To 99999
            For j As Integer = 0 To 9999
                result = i * j
            Next j
        Next i
    End Sub
    ```

    ```csharp
    public void TimeCounter()
    {
        for (int i = 0; i < 100000; i++)
        {
            for (int j = 0; j < 10000; j++)
            {
                int result = i * j;
            }
        }
    }
    ```

6. En **Explorador de soluciones**, abra el menú contextual del proyecto (**profilete**) y, a continuación, elija **propiedades**.

7. En el cuadro de diálogo **propiedades** , elija la pestaña **SharePoint** .

8. En la lista **configuración de implementación activa** , elija **sin activación**.

     La selección de esta configuración de implementación le permite activar manualmente la característica más adelante en SharePoint.

9. Guarde el proyecto.

## <a name="configure-and-deploy-the-sharepoint-application"></a>Configurar e implementar la aplicación de SharePoint
 Ahora que el proyecto de SharePoint está listo, configúrelo e impleméntelo en el servidor de SharePoint.

### <a name="to-configure-and-deploy-the-sharepoint-application"></a>Para configurar e implementar la aplicación de SharePoint

1. En el menú **analizar** , elija **iniciar el Asistente para rendimiento**.

2. En la página uno del **Asistente de rendimiento**, deje el método de generación de perfiles como muestreo de la **CPU** y elija el botón **siguiente** .

     Los demás métodos de generación de perfiles pueden utilizarse en situaciones más avanzadas de generación de perfiles. Para obtener más información, vea [Introducción a los métodos de generación de perfiles](../profiling/understanding-performance-collection-methods.md).

3. En la página dos del **Asistente de rendimiento**, deje el destino del perfil como **Profilet** y elija el botón **siguiente** .

     Si una solución tiene varios proyectos, aparecen en esta lista.

4. En la página tres del **Asistente de rendimiento**, desactive la casilla **Habilitar generación de perfiles de interacción de capas** y, a continuación, elija el botón **siguiente** .

     La característica de generación de perfiles de interacción de capa (TIP) es útil para medir el rendimiento de las aplicaciones que consultan a bases de datos y para mostrar el número de veces que se solicita una página web. Dado que esos datos no son necesarios para este ejemplo, no se habilitará esta característica.

5. En la página cuatro del **Asistente de rendimiento**, deje activada la casilla **iniciar generación de perfiles cuando finalice el asistente** y, a continuación, elija el botón **Finalizar** .

     El asistente habilita la generación de perfiles de aplicaciones en el servidor, muestra la ventana de **Explorador de rendimiento** y, a continuación, compila, implementa y ejecuta la aplicación de SharePoint.

## <a name="run-the-sharepoint-application"></a>Ejecutar la aplicación de SharePoint
 Active la característica en SharePoint, desencadenando el código de evento `FeatureActivation` para la ejecución.

### <a name="to-run-the-sharepoint-application"></a>Para ejecutar la aplicación de SharePoint

1. En SharePoint, abra el menú **acciones del sitio** y, a continuación, elija Configuración del **sitio**.

2. En la lista **acciones del sitio** , elija el vínculo **administrar las características del sitio** .

3. En la lista **características** , elija el botón **Activar** situado junto a la opción **Feature1 de Profilet**.

     Se produce una pausa al hacer esto, debido a que se llama al bucle inactivo en la función `FeatureActivated`.

4. En la barra **Inicio rápido** , elija **listas** y, a continuación, en la lista **listas** , elija **anuncios**.

     Observe que se ha agregado un nuevo anuncio a la lista que indica que se ha activado la característica.

5. Cierre el sitio de SharePoint.

     Después de cerrar SharePoint, el generador de perfiles crea y muestra un informe de generación de perfiles de ejemplo y lo guarda como un archivo. VSP en la carpeta del proyecto de **Profilet** .

## <a name="view-and-interpret-the-profile-results"></a>Ver e interpretar los resultados del perfil
 Ahora que ha ejecutado la aplicación de SharePoint y ha generado perfiles, vea los resultados de las pruebas.

### <a name="to-view-and-interpret-the-profile-results"></a>Para ver e interpretar los resultados del perfil

1. En la sección **funciones que realizan la mayor parte del trabajo individual** del informe de generación de perfiles de ejemplo, observe que `TimeCounter` está cerca de la parte superior de la lista.

     Esta ubicación indica que `TimeCounter` fue una de las funciones con el número más alto de muestras, lo que significa que es uno de los mayores cuellos de botella de rendimiento de la aplicación. Sin embargo, esta situación no es sorprendente, porque se diseñó deliberadamente de ese modo para fines de demostración.

2. En la sección **funciones que realizan la mayor parte del trabajo individual** , elija el `ProcessRequest` vínculo para mostrar la distribución del costo de la `ProcessRequest` función.

     En la sección **funciones llamadas** de `ProcessRequest` , observe que la función **FeatureActivated** se muestra como la función más costosa llamada.

3. En la sección **funciones llamadas** , elija el botón **FeatureActivated** .

     En la sección **funciones llamadas** de **FeatureActivated**, la `TimeCounter` función aparece como la función más costosa llamada. En el panel **vista de código de función** , el código resaltado ( `TimeCounter` ) es la zona activa y indica dónde se necesita la corrección.

4. Cierre el informe de generación de perfiles de muestreo.

     Para volver a ver el informe en cualquier momento, abra el archivo. VSP en la ventana de **Explorador de rendimiento** .

## <a name="fix-the-code-and-reprofile-the-application"></a>Corregir el código y regenerar el perfil de la aplicación
 Ahora que ha identificado la función de zona activa de la aplicación de SharePoint, corríjala.

### <a name="to-fix-the-code-and-reprofile-the-application"></a>Para corregir el código y regenerar los perfiles de la aplicación

1. En el código del receptor de eventos de características, comente la llamada al método `TimeCounter` de `FeatureActivated` para evitar que se le llame.

2. Guarde el proyecto.

3. En **Explorador de rendimiento**, abra la carpeta destinos y, a continuación, elija el nodo de **Profilet** .

4. En la barra de herramientas **Explorador de rendimiento** , en la pestaña **acciones** , elija el botón **iniciar generación de perfiles** .

     Si desea cambiar cualquiera de las propiedades de generación de perfiles antes de regeneración la aplicación, elija en su lugar el botón **iniciar el Asistente de rendimiento** .

5. Siga las instrucciones de la sección **ejecución de la aplicación de SharePoint** , anteriormente en este tema.

     La característica se debería activar mucho más rápido ahora que se ha eliminado la llamada al bucle inactivo. El informe de generación de perfiles de muestreo debería reflejarlo.

## <a name="see-also"></a>Vea también
- [Introducción a la sesión de rendimiento](../profiling/performance-session-overview.md)
- [Guía básica para la generación de perfiles de rendimiento](../profiling/beginners-guide-to-performance-profiling.md)
- [Find Application Bottlenecks with Visual Studio Profiler (Detección de cuellos de botella de las aplicaciones con el generador de perfiles de Visual Studio)](/archive/msdn-magazine/2008/march/find-application-bottlenecks-with-visual-studio-profiler)