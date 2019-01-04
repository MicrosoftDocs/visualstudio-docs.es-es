---
title: 'Tutorial: Generación de perfiles de una aplicación de SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1e5fb918761cc8e8d68aaaaa5e6a420bb6758a1e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913822"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>Tutorial: Generar perfiles de una aplicación de SharePoint
  En este tutorial se muestra cómo usar las herramientas de generación de perfiles de Visual Studio para optimizar el rendimiento de una aplicación de SharePoint. La aplicación de ejemplo es un receptor de eventos de características de SharePoint que contiene un bucle inactivo que merma el rendimiento del receptor de eventos de características. El generador de perfiles de Visual Studio le permite encontrar y eliminar la parte más cara (rendimiento más lento) del proyecto, también conocido como el *caliente*.  
  
 En este tutorial se muestran las siguientes tareas:  
  
- [Agregar una característica y un receptor de eventos de característica](#BKMK_AddFtrandFtrEvntReceiver).  
  
- [Configurar e implementar la aplicación de SharePoint](#BKMK_ConfigSharePointApp).  
  
- [Ejecutar la aplicación de SharePoint](#BKMK_RunSPApp).  
  
- [Visualización e interpretación de los resultados de la generación de perfiles](#BKMK_ViewResults).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Microsoft Windows y SharePoint.
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
## <a name="create-a-sharepoint-project"></a>Crear un proyecto de SharePoint
 Primero, cree un proyecto de SharePoint.  
  
#### <a name="to-create-a-sharepoint-project"></a>Para crear un proyecto de SharePoint  
  
1. En la barra de menús, elija **archivo** > **New** > **proyecto** para mostrar el **nuevo proyecto** cuadro de diálogo.  
  
2. Expanda el **SharePoint** nodo bajo **Visual C#** o **Visual Basic**y, a continuación, elija el **2010** nodo.  
  
3. En el panel Plantillas, elija el **proyecto de SharePoint 2010** plantilla.  
  
4. En el **nombre** , escriba **ProfileTest**y, a continuación, elija el **Aceptar** botón.  
  
    El **Asistente de personalización de SharePoint** aparece.  
  
5. En el **especificar el nivel de sitio y de seguridad para la depuración** página, escriba la dirección URL del sitio de SharePoint server donde desea depurar la definición de sitio o usar la ubicación predeterminada (http://<em>nombre del sistema</em>/) .  
  
6. En el **¿qué es el nivel de confianza para esta solución de SharePoint?** sección, elija el **implementar como solución de granja de servidores** botón de opción.  
  
    De momento solo puede generar perfiles de soluciones de granja de servidores. Para obtener más información acerca de las soluciones en espacio aislado frente a soluciones de granja, vea [consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
7. Elija la **finalizar** botón. El proyecto aparece en **el Explorador de soluciones**.  
  
## <a name="add-a-feature-and-feature-event-receiver"></a>Agregar una característica y un receptor de eventos de característica
 A continuación, agregue una característica al proyecto junto con un receptor de eventos para esa característica. Este receptor de eventos contendrá el código cuyo perfil se va a generar.  
  
#### <a name="to-add-a-feature-and-feature-event-receiver"></a>Para agregar una característica y un receptor de eventos de características  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para el **características** nodo, elija **Agregar característica**y deje el nombre en el valor predeterminado, **Feature1**.  
  
2.  En **el Explorador de soluciones**, abra el menú contextual para **Feature1**y, a continuación, elija **agregar receptor de eventos**.  
  
     Esto agrega un archivo de código a la característica con varios controladores de eventos con comentarios y abre el archivo para edición.  
  
3.  En la clase del receptor de eventos, agregue las siguientes declaraciones de variable.  
  
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
  
4.  Reemplace el procedimiento `FeatureActivated` por el siguiente código.  
  
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
  
5.  Agregue el siguiente procedimiento a continuación el `FeatureActivated`procedimiento.  
  
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
  
6.  En **el Explorador de soluciones**, abra el menú contextual del proyecto (**ProfileTest**) y, a continuación, elija **propiedades**.  
  
7.  En el **propiedades** diálogo cuadro, elija el **SharePoint** ficha.  
  
8.  En el **Active Deployment Configuration** elija **sin activación**.  
  
     La selección de esta configuración de implementación le permite activar manualmente la característica más adelante en SharePoint.  
  
9. Guarde el proyecto.  
  
## <a name="configure-and-deploy-the-sharepoint-application"></a>Configurar e implementar la aplicación de SharePoint
 Ahora que el proyecto de SharePoint está listo, configúrelo e impleméntelo en el servidor de SharePoint.  
  
#### <a name="to-configure-and-deploy-the-sharepoint-application"></a>Para configurar e implementar la aplicación de SharePoint  
  
1.  En el **analizar** menú, elija **iniciar Asistente de rendimiento**.  
  
2.  En la página uno de los **Asistente de rendimiento**, deje el método de generación de perfiles como **muestreo de la CPU** y elija el **siguiente** botón.  
  
     Los demás métodos de generación de perfiles pueden utilizarse en situaciones más avanzadas de generación de perfiles. Para obtener más información, vea [Introducción a los métodos de generación de perfiles](/visualstudio/profiling/understanding-performance-collection-methods).  
  
3.  En la página dos de los **Asistente de rendimiento**, deje el perfil de destino como **ProfileTest** y elija el **siguiente** botón.  
  
     Si una solución tiene varios proyectos, aparecen en esta lista.  
  
4.  En la página tres de los **Asistente de rendimiento**, desactive la **Habilitar generación de perfiles de interacción de capas** casilla de verificación y, a continuación, elija el **siguiente** botón.  
  
     La característica de generación de perfiles de interacción de capa (TIP) es útil para medir el rendimiento de las aplicaciones que consultan a bases de datos y para mostrar el número de veces que se solicita una página web. Dado que esos datos no son necesarios para este ejemplo, no se habilitará esta característica.  
  
5.  En la página cuatro de los **Asistente de rendimiento**, deje el **Iniciar generación de perfiles cuando finalice el asistente** casilla seleccionada y, a continuación, elija el **finalizar** botón.  
  
     El asistente permite generar perfiles de aplicación en el servidor, se muestra el **Explorador de rendimiento** ventana y, a continuación, compila, implementa y ejecuta la aplicación de SharePoint.  
  
## <a name="run-the-sharepoint-application"></a>Ejecute la aplicación de SharePoint
 Active la característica en SharePoint, desencadenando el código de evento `FeatureActivation` para la ejecución.  
  
#### <a name="to-run-the-sharepoint-application"></a>Para ejecutar la aplicación de SharePoint  
  
1.  En SharePoint, abra el **acciones del sitio** menú y, a continuación, elija **configuración del sitio**.  
  
2.  En el **acciones del sitio** lista, elija el **administrar características del sitio** vínculo.  
  
3.  En el **características** lista, elija el **activar** situado junto a **ProfileTest Feature1**.  
  
     Se produce una pausa al hacer esto, debido a que se llama al bucle inactivo en la función `FeatureActivated`.  
  
4.  En el **inicio rápido** barra, elija **enumera** y, a continuación, en el **enumera** elija **anuncios**.  
  
     Observe que se ha agregado un nuevo anuncio a la lista que indica que se ha activado la característica.  
  
5.  Cierre el sitio de SharePoint.  
  
     Después de cerrar SharePoint, el generador de perfiles crea y muestra un informe de generación de perfiles de ejemplo y lo guarda como un archivo .vsp en la **ProfileTest** carpeta del proyecto.  
  
## <a name="view-and-interpret-the-profile-results"></a>Ver e interpretar los resultados del perfil
 Ahora que ha ejecutado la aplicación de SharePoint y ha generado perfiles, vea los resultados de las pruebas.  
  
#### <a name="to-view-and-interpret-the-profile-results"></a>Para ver e interpretar los resultados del perfil
  
1.  En el **funciones que realizan la mayor parte del trabajo Individual** sección del informe de generación de perfiles de ejemplo, tenga en cuenta que `TimeCounter` está cerca de la parte superior de la lista.  
  
     Esta ubicación indica que `TimeCounter` fue una de las funciones con el número más alto de muestras, lo que significa que es uno de los mayores cuellos de botella de rendimiento de la aplicación. Sin embargo, esta situación no es sorprendente, porque se diseñó deliberadamente de ese modo para fines de demostración.  
  
2.  En el **funciones que realizan la mayor parte del trabajo Individual** sección, elija el `ProcessRequest` vínculo para mostrar la distribución del costo de la `ProcessRequest` función.  
  
     En el **denominadas funciones** sección `ProcessRequest`, tenga en cuenta que el **FeatureActivated** función aparece como la que más recursos consume llama a la función.  
  
3.  En el **denominadas funciones** sección, elija el **FeatureActivated** botón.  
  
     En el **denominadas funciones** sección **FeatureActivated**, el `TimeCounter` función aparece como la que más recursos consume llama a la función. En el **vista de código de función** panel, el código resaltado (`TimeCounter`) es el punto de conexión e indica que se necesita la corrección.  
  
4.  Cierre el informe de generación de perfiles de muestreo.  
  
     Para ver el informe nuevo en cualquier momento, abra el archivo .vsp en la **Explorador de rendimiento** ventana.  
  
## <a name="fix-the-code-and-reprofile-the-application"></a>Corrija el código y regenerar los perfiles de la aplicación
 Ahora que ha identificado la función de zona activa de la aplicación de SharePoint, corríjala.  
  
#### <a name="to-fix-the-code-and-reprofile-the-application"></a>Para corregir el código y regenerar los perfiles de la aplicación  
  
1.  En el código del receptor de eventos de características, comente la llamada al método `TimeCounter` de `FeatureActivated` para evitar que se le llame.  
  
2.  Guarde el proyecto.  
  
3.  En **Explorador de rendimiento**, abra la carpeta destinos y, a continuación, elija el **ProfileTest** nodo.  
  
4.  En el **Explorador de rendimiento** barra de herramientas, en el **acciones** ficha, elija la **Iniciar generación de perfiles** botón.  
  
     Si desea cambiar cualquiera de las propiedades de generación de perfiles antes de la regeneración de perfiles de la aplicación, elija el **iniciar Asistente de rendimiento** botón en su lugar.  
  
5.  Siga las instrucciones de la **ejecuta la aplicación SharePoint** sección anteriormente en este tema.  
  
     La característica se debería activar mucho más rápido ahora que se ha eliminado la llamada al bucle inactivo. El informe de generación de perfiles de muestreo debería reflejarlo.  
  
## <a name="see-also"></a>Vea también
 [Explorador de rendimiento](/visualstudio/profiling/performance-explorer)   
 [Información general sobre la sesión de rendimiento](/visualstudio/profiling/performance-session-overview)   
 [Guía básica para la generación de perfiles de rendimiento](/visualstudio/profiling/beginners-guide-to-performance-profiling)   
 [Encontrar cuellos de botella de aplicación con Visual Studio Profiler](http://go.microsoft.com/fwlink/?LinkID=137266)  
