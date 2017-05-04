---
title: "Tutorial: Crear un elemento web de Silverlight que muestre OData para SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/22/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.SilverlightWebPart"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 92d55e68-8f3f-4bf7-a21b-801c298b04c4
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Tutorial: Crear un elemento web de Silverlight que muestre OData para SharePoint
  SharePoint 2010 expone los datos de la lista mediante OData.  En SharePoint, el servicio de OData es implementado por el servicio ListData.svc de RESTful.  Este tutorial muestra cómo crear un elemento web de SharePoint que hospeda una aplicación de Silverlight.  Muestra SharePoint Announcement de la aplicación de Silverlight muestran información mediante ListData.svc.  Para obtener más información, vea [Interfaz de RESTO de windows workflow foundation de SharePoint](http://go.microsoft.com/fwlink/?LinkId=225999) y [Protocolo abierto de datos](http://go.microsoft.com/fwlink/?LinkId=226000).  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   [Crear una aplicación de Silverlight y un elemento web de Silverlight](#BKMK_creatingSLApp).  
  
-   [Personalizar la aplicación de Silverlight](#BKMK_customizeSLApp).  
  
-   [Personalizar la aplicación de Silverlight](#BKMK_customizeSLApp).  
  
-   [Personalizar la aplicación de Silverlight](#BKMK_customizeSLApp).  
  
-   [Probar el elemento web de Silverlight](#BKMK_testSLApp).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Microsoft Windows y SharePoint.  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
##  <a name="BKMK_creatingSLApp"></a> Crear una aplicación de Silverlight y un elemento web de Silverlight  
 Primero, cree una aplicación Silverlight en Visual Studio.  La aplicación de Silverlight recupera datos de anuncios de SharePoint mediante el servicio de ListData.svc.  
  
> [!NOTE]  
>  Ninguna versiones de Silverlight antes de que 4,0 admiten las interfaces necesarias para hacer referencia a datos de lista de SharePoint.  
  
#### Para crear parte de Silverlight de un web de la aplicación y de Silverlight  
  
1.  En la barra de menú, elija **archivo**, **new**, **Project** para mostrar el cuadro de diálogo de **Nuevo proyecto** .  
  
2.  Expanda el nodo de **sharepoint** en **Visual C\#** o **Visual Basic**y, a continuación el nodo de **2010** .  
  
3.  En el panel plantillas, elija la plantilla de **Elemento web de SharePoint 2010 Silverlight** .  
  
4.  En el cuadro de **Name** , entre en SLWebPartTest y elija el botón de **Aceptar** .  
  
     El cuadro de diálogo de **Asistente para la personalización de SharePoint** aparece.  
  
5.  En la página de **Especifique el sitio y el nivel de seguridad de la depuración** , escriba la dirección URL para el sitio de servidor de SharePoint donde desea depurar la definición de sitio, o utilice la ubicación predeterminada \(http:\/\/*system name*\/\).  
  
6.  En la sección **¿Cuál es el nivel de confianza de esta solución de SharePoint?**, elija el botón de opción **Implementar como solución de granja de servidores**.  
  
     Aunque en este ejemplo se utiliza una solución de granja, los proyectos web de la parte de Silverlight se pueden implementar como granja o las soluciones en espacio aislado.  Para obtener más información sobre las soluciones en espacio aislado y soluciones de granja de servidores, vea [Consideraciones sobre las soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  En la sección de **Cómo desea asociar al elemento web de Silverlight** de la página de **Especificar información de configuración de Silverlight** , elija el botón de opción de **Crear un nuevo proyecto de Silverlight y asociarlo al elemento web** .  
  
8.  Cambie **Name** a SLApplication, establezca **Idioma** a **Visual Basic** o a **Visual C\#**, y establezca **Versión de Silverlight** a **Silverlight 4,0**.  
  
9. Elija el botón **Finalizar**.  Los proyectos aparecen en **Explorador de soluciones**.  
  
     La solución contiene dos proyectos: una aplicación Silverlight y una parte web de Silverlight.  La aplicación de Silverlight recupera y muestra los datos de lista de SharePoint, y hospeda web de la parte de Silverlight la aplicación de Silverlight, permitiéndole para verla en SharePoint.  
  
##  <a name="BKMK_customizeSLApp"></a> Personalizar la aplicación de Silverlight  
 Agregue el código y los elementos de diseño a la aplicación de Silverlight.  
  
#### Para personalizar la aplicación de Silverlight  
  
1.  Agregue una referencia de ensamblado a System.Windows.Data en la aplicación de Silverlight.  Para obtener más información, vea [Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
2.  En **Explorador de soluciones**, abra el menú contextual para **Referencias**y, a continuación **Agregar referencia de servicio**.  
  
    > [!NOTE]  
    >  Si utiliza Visual Basic, debe elegir el icono de **Mostrar todos los archivos** en la parte superior de **Explorador de soluciones** para mostrar el nodo de **Referencias** .  
  
3.  En el cuadro dirección de cuadro de diálogo de **Agregar referencia de servicio** , escriba la dirección URL del sitio de SharePoint, como **http:\/\/MySPSite**, y elija el botón de **Ir** .  
  
     Cuando Silverlight encuentra el servicio ListData.svc de SharePoint OData, reemplaza la dirección con la dirección URL del servicio completo.  Para este ejemplo, http:\/\/myserver se convierte en http:\/\/myserver\/\_vti\_bin\/ListData.svc.  
  
4.  Elija el botón de **Aceptar** para agregar la referencia de servicio al proyecto, y utilice el nombre predeterminado del servicio, ServiceReference1.  
  
5.  En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
6.  Agregue un nuevo origen de datos al proyecto basado en el servicio de SharePoint.  Para ello, en la barra de menú, elija **Visualización**, **Otras ventanas**, **Orígenes de datos**.  
  
     La ventana de **Orígenes de datos** muestra todos los datos disponibles de la lista de SharePoint, como tareas, Anuncios, y calendario.  
  
7.  Agregue los datos de la lista de Anuncios a la aplicación de Silverlight.  Puede arrastrar “Anuncios” de la ventana de **Orígenes de datos** sobre el diseñador de Silverlight.  
  
     Esto crea un límite del control de cuadrícula a la lista de Anuncios de sitio de SharePoint.  
  
8.  Cambie el tamaño del control de cuadrícula para ajustarse la página de Silverlight.  
  
9. En el archivo de código MainPage.xaml \(MainPage.xaml.cs para Visual c\# o MainPage.xaml.vb para Visual Basic\), agregue las siguientes referencias de espacio de nombres.  
  
    ```vb  
    ' Add the following three Imports statements.  
    Imports SLApplication.ServiceReference1  
    Imports System.Windows.Data  
    Imports System.Data.Services.Client  
    ```  
  
    ```csharp  
    // Add the following three using statements.  
    using SLApplication.ServiceReference1;  
    using System.Windows.Data;  
    using System.Data.Services.Client;  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#1](SP_SLWebPart#1)]  -->  
  
10. Agregue las declaraciones de variable siguientes en la parte superior de la clase.  
  
    ```vb  
    Private context As TeamSiteDataContext  
    Private myCollectionViewSource As CollectionViewSource  
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()  
    ```  
  
    ```csharp  
    private TeamSiteDataContext context;  
    private CollectionViewSource myCollectionViewSource;  
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#2](SP_SLWebPart#2)]  -->  
  
11. Reemplace el procedimiento de `UserControl_Loaded` con el siguiente.  
  
    ```vb  
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)  
        ' The URL for the OData service.  
        ' Replace <server name> in the next line with the name of your SharePoint server.  
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))  
  
        ' Do not load your data at design time.  
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then  
            'Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)  
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)  
            announcements.LoadAsync(context.Announcements)  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)  
    {  
        // The URL for the OData service.  
        // Replace <server name> in the next line with the name of your   
        // SharePoint server.  
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));  
  
        // Do not load your data at design time.  
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))  
        {  
            //Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];  
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);  
            announcements.LoadAsync(context.Announcements);  
        }  
    }  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#3](SP_SLWebPart#3)]  -->  
  
     Asegúrese de reemplazar el marcador de *ServerName* con el nombre del servidor que ejecuta SharePoint.  
  
12. Agregue el procedimiento de control de errores siguiente.  
  
    ```vb  
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)  
        ' Handle any errors.  
        If e.[Error] Is Nothing Then  
            myCollectionViewSource.Source = announcements  
        Else  
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))  
        End If  
    End Sub  
  
    ```  
  
    ```csharp  
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)  
    {  
        // Handle any errors.  
        if (e.Error == null)  
        {  
            myCollectionViewSource.Source = announcements;  
        }  
        else  
        {  
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));  
        }  
    }  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#4](SP_SLWebPart#4)]  -->  
  
## Modificar el elemento web de Silverlight  
 Cambie la propiedad del proyecto web de la parte de Silverlight para habilitar la depuración de Silverlight.  
  
#### Para modificar la parte del web de Silverlight  
  
1.  Abrir el menú contextual para el proyecto web de la parte de Silverlight \(**SLWebPartTest**\) y, a continuación **Propiedades**.  
  
2.  En la ventana de **Propiedades** , elija la ficha de **sharepoint** .  
  
3.  Si aún no está seleccionada, active la casilla de **Habilitar depuración de Silverlight \(en lugar de depuración de script\)** .  
  
4.  Guarde el proyecto.  
  
##  <a name="BKMK_testSLApp"></a> Probar el elemento web de Silverlight  
 Pruebe el nuevo elemento web de Silverlight en SharePoint para asegurarse de que muestra los datos de la lista de SharePoint correctamente.  
  
#### Para probar el elemento web de Silverlight  
  
1.  Elija la tecla F5 para compilar y ejecutar la solución de SharePoint.  
  
2.  En SharePoint, en el menú de **Acciones del sitio** , elija **Nueva página**.  
  
3.  En el cuadro de diálogo **Nueva página** , escriba un título, como prueba de elemento web de SL, y elija el botón de **crear** .  
  
4.  En el diseñador de la página, en la ficha de **Herramientas de edición** , elija **INSERT**.  
  
5.  En la barra de la ficha, elija **Elemento Web**.  
  
6.  En el cuadro de **categorías** , elija la carpeta de **Custom** .  
  
7.  En la lista de **Elementos web** , elija el elemento web de Silverlight, y elija el botón de **Add** para agregar el elemento web al diseñador.  
  
8.  Después de haber creado todas las adiciones a la página Web que desea, elija la ficha de **Página** , y elija el botón de **Guardar y cerrar &**  en la barra de herramientas.  
  
     El elemento web de Silverlight ahora debe mostrar los datos de Anuncio del sitio de SharePoint.  De forma predeterminada, la página se almacena en las páginas del sitio enumeradas en SharePoint.  
  
    > [!NOTE]  
    >  Cuando datos de acceso en Silverlight entre dominios, restricciones de Silverlight contra las vulnerabilidades de seguridad que se pueden utilizar para las aplicaciones Web.  Si experimenta problemas al tener acceso a datos remotos en Silverlight, vea [Crear un Servicio límites disponibles del dominio de Entre](http://go.microsoft.com/fwlink/?LinkId=223276).  
  
## Vea también  
 [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Implementar, publicar y actualizar paquetes de soluciones de  
SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  