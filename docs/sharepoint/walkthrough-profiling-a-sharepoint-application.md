---
title: "Walkthrough: Profiling a SharePoint Application | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, profiling"
  - "performance testing [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, performance testing"
  - "profiling [SharePoint development in Visual Studio]"
ms.assetid: 0b19d4b7-5fcc-42a2-b411-96eccd00137f
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Walkthrough: Profiling a SharePoint Application
  En este tutorial se muestra cómo usar las herramientas de generación de perfiles de Visual Studio para optimizar el rendimiento de una aplicación de SharePoint.  La aplicación de ejemplo es un receptor de eventos de características de SharePoint que contiene un bucle inactivo que merma el rendimiento del receptor de eventos de características.  El generador de perfiles de Visual Studio le permite encontrar y eliminar la parte que consume más recursos \(rendimiento más lento\) del proyecto, también conocida como la *ruta de acceso activa*.  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   [Adición de una característica y un receptor de eventos de características](#BKMK_AddFtrandFtrEvntReceiver).  
  
-   [Configuración e implementación de la aplicación de SharePoint](#BKMK_ConfigSharePointApp).  
  
-   [Ejecución de la aplicación de SharePoint](#BKMK_RunSPApp).  
  
-   [Visualización e interpretación de los resultados de la generación de perfiles](#BKMK_ViewResults).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Microsoft Windows y SharePoint.  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
## Creación de un proyecto de SharePoint  
 Primero, cree un proyecto de SharePoint.  
  
#### Para crear un proyecto de SharePoint  
  
1.  En la barra de menús, seleccione **Archivo**, **Nuevo**, **Proyecto** para mostrar el cuadro de diálogo **Nuevo proyecto**.  
  
2.  Expanda el nodo **SharePoint** en **Visual C\#** o **Visual Basic** y, a continuación, seleccione el nodo **2010**.  
  
3.  En el panel de plantillas, seleccione la plantilla **Proyecto de SharePoint 2010**.  
  
4.  En el cuadro **Nombre**, escriba ProfileTest y seleccione el botón **Aceptar**.  
  
     Aparece el **Asistente para personalización de SharePoint**.  
  
5.  En la página **Especifique el sitio y el nivel de seguridad de la depuración**, escriba la dirección URL del sitio del servidor de SharePoint donde desea depurar la definición de sitio o utilice la ubicación predeterminada \(http:\/\/*nombre del sistema*\/\).  
  
6.  En la sección **¿Cuál es el nivel de confianza de esta solución de SharePoint?**, active el botón de opción **Implementar como solución de granja de servidores**.  
  
     De momento solo puede generar perfiles de soluciones de granja de servidores.  Para obtener más información sobre las soluciones en espacio aislado frente a las soluciones de granja de servidores, vea [Consideraciones sobre las soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Elija el botón **Finalizar**.  El proyecto aparece en el **Explorador de soluciones**.  
  
##  <a name="BKMK_AddFtrandFtrEvntReceiver"></a> Adición de una característica y un receptor de eventos de características  
 A continuación, agregue una característica al proyecto junto con un receptor de eventos para esa característica.  Este receptor de eventos contendrá el código cuyo perfil se va a generar.  
  
#### Para agregar una característica y un receptor de eventos de características  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del nodo **Características**, seleccione **Agregar característica** y deje el nombre en el valor predeterminado, **Feature1**.  
  
2.  En el **Explorador de soluciones**, abra el menú contextual de **Feature1** y seleccione **Agregar receptor de eventos**.  
  
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
  
5.  Agregue el siguiente procedimiento bajo el procedimiento `FeatureActivated`.  
  
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
  
6.  En el **Explorador de soluciones**, abra el menú contextual del proyecto \(**ProfileTest**\) y, a continuación, seleccione **Propiedades**.  
  
7.  En el cuadro de diálogo **Propiedades**, seleccione la pestaña **SharePoint**.  
  
8.  En la lista **Configuración de implementación activa**, seleccione **Sin activación**.  
  
     La selección de esta configuración de implementación le permite activar manualmente la característica más adelante en SharePoint.  
  
9. Guarde el proyecto.  
  
##  <a name="BKMK_ConfigSharePointApp"></a> Configuración e implementación de la aplicación de SharePoint  
 Ahora que el proyecto de SharePoint está listo, configúrelo e impleméntelo en el servidor de SharePoint.  
  
#### Para configurar e implementar la aplicación de SharePoint  
  
1.  En el menú **Analizar**, seleccione **Iniciar Asistente de rendimiento**.  
  
2.  En la página uno del **Asistente de rendimiento**, deje el método de generación de perfiles como **Muestreo de la CPU** y seleccione el botón **Siguiente**.  
  
     Los demás métodos de generación de perfiles pueden utilizarse en situaciones más avanzadas de generación de perfiles.  Para obtener más información, vea [Introducción a los métodos de generación de perfiles](../profiling/understanding-performance-collection-methods.md).  
  
3.  En la página dos del **Asistente de rendimiento**, deje el destino del perfil como **ProfileTest** y seleccione el botón **Siguiente**.  
  
     Si una solución tiene varios proyectos, aparecen en esta lista.  
  
4.  En la página tres del **Asistente de rendimiento**, desactive la casilla **Habilitar generación de perfiles de interacción de capa** y, a continuación, seleccione el botón **Siguiente**.  
  
     La característica de generación de perfiles de interacción de capa \(TIP\) es útil para medir el rendimiento de las aplicaciones que consultan a bases de datos y para mostrar el número de veces que se solicita una página web.  Dado que esos datos no son necesarios para este ejemplo, no se habilitará esta característica.  
  
5.  En la página cuatro del **Asistente de rendimiento**, deje activada la casilla **Iniciar generación de perfiles cuando finalice el asistente** y, a continuación, seleccione el botón **Finalizar**.  
  
     El asistente permite la generación de perfiles de la aplicación en el servidor, muestra la ventana **Explorador de rendimiento** y, a continuación, compila, implementa y ejecuta la aplicación de SharePoint.  
  
##  <a name="BKMK_RunSPApp"></a> Ejecución de la aplicación de SharePoint  
 Active la característica en SharePoint, desencadenando el código de evento `FeatureActivation` para la ejecución.  
  
#### Para ejecutar la aplicación de SharePoint  
  
1.  En SharePoint, abra el menú **Acciones del sitio** y seleccione **Configuración del sitio**.  
  
2.  En la lista **Acciones del sitio**, seleccione el vínculo **Administrar las características del sitio**.  
  
3.  En la lista **Características**, seleccione el botón **Activar** situado junto a **ProfileTest Feature1**.  
  
     Se produce una pausa al hacer esto, debido a que se llama al bucle inactivo en la función `FeatureActivated`.  
  
4.  En la barra **Inicio rápido**, seleccione **Listas** y, a continuación, en la lista **Listas**, seleccione **Anuncios**.  
  
     Observe que se ha agregado un nuevo anuncio a la lista que indica que se ha activado la característica.  
  
5.  Cierre el sitio de SharePoint.  
  
     Después de cerrar SharePoint, el generador de perfiles crea y muestra un informe de generación de perfiles de muestreo y lo guarda como un archivo .vsp en la carpeta **ProfileTest** del proyecto.  
  
##  <a name="BKMK_ViewResults"></a> Visualización e interpretación de los resultados de la generación de perfiles  
 Ahora que ha ejecutado la aplicación de SharePoint y ha generado perfiles, vea los resultados de las pruebas.  
  
#### Para ver e interpretar los resultados de la generación de perfiles  
  
1.  En la sección **Funciones que realizan la mayor parte de trabajo individual** del informe de generación de perfiles de muestreo, observe que `TimeCounter` está cerca de la parte superior de la lista.  
  
     Esta ubicación indica que `TimeCounter` fue una de las funciones con el número más alto de muestras, lo que significa que es uno de los mayores cuellos de botella de rendimiento de la aplicación.  Sin embargo, esta situación no es sorprendente, porque se diseñó deliberadamente de ese modo para fines de demostración.  
  
2.  En la sección **Funciones que realizan la mayor parte de trabajo individual**, seleccione el vínculo `ProcessRequest` para mostrar la distribución del consumo de recursos de la función `ProcessRequest`.  
  
     En la sección **Funciones llamadas** de `ProcessRequest`, observe que la función **FeatureActivated** aparece como la que más recursos consume.  
  
3.  En la sección **Funciones llamadas**, seleccione el botón **FeatureActivated**.  
  
     En la sección **Funciones llamadas** de **FeatureActivated**, la función `TimeCounter` aparece como la que más recursos consume.  En el panel **Vista de código de función**, el código resaltado \(`TimeCounter`\) es la zona activa e indica dónde se necesita la corrección.  
  
4.  Cierre el informe de generación de perfiles de muestreo.  
  
     Para ver el informe de nuevo en cualquier momento, abra el archivo .vsp en la ventana **Explorador de rendimiento**.  
  
## Corrección del código y regeneración de perfiles de la aplicación  
 Ahora que ha identificado la función de zona activa de la aplicación de SharePoint, corríjala.  
  
#### Para corregir el código y regenerar los perfiles de la aplicación  
  
1.  En el código del receptor de eventos de características, comente la llamada al método `TimeCounter` de `FeatureActivated` para evitar que se le llame.  
  
2.  Guarde el proyecto.  
  
3.  En **Explorador de rendimiento**, abra la carpeta Destinos y, a continuación, seleccione el nodo **ProfileTest**.  
  
4.  En la barra de herramientas **Explorador de rendimiento**, en la pestaña **Acciones**, seleccione el botón **Iniciar generación de perfiles**.  
  
     Si desea cambiar cualquiera de las propiedades de generación de perfiles antes de la regeneración de perfiles de la aplicación, seleccione el botón **Iniciar Asistente de rendimiento** en su lugar.  
  
5.  Siga las instrucciones de la sección **Ejecución de la aplicación de SharePoint**, anteriormente en este tema.  
  
     La característica se debería activar mucho más rápido ahora que se ha eliminado la llamada al bucle inactivo.  El informe de generación de perfiles de muestreo debería reflejarlo.  
  
## Vea también  
 [Uso de las herramientas de generación de perfiles](../profiling/performance-explorer.md)   
 [Información general sobre las sesiones de rendimiento de las herramientas de generación de perfiles](../profiling/performance-session-overview.md)   
 [Guía básica para la generación de perfiles de rendimiento](../profiling/beginners-guide-to-performance-profiling.md)   
 [Encontrar cuellos de botella en una aplicación con el Generador de perfiles de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=137266)  
  
  