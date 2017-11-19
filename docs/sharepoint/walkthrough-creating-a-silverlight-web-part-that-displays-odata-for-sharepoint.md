---
title: 'Tutorial: Crear un elemento Web de Silverlight que muestre OData para SharePoint | Documentos de Microsoft'
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
ms.assetid: 92d55e68-8f3f-4bf7-a21b-801c298b04c4
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0a6999a7a390c207c184f26d36e0ca5d64d5fef5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Tutorial: Crear un elemento web de Silverlight que muestre OData para SharePoint
  SharePoint 2010 expone sus datos de la lista por medio de OData. En SharePoint, el servicio de OData se implementa el servicio RESTful ListData.svc. Este tutorial muestra cómo crear un elemento web de SharePoint que hospeda una aplicación de Silverlight. La aplicación de Silverlight, muestra información de la lista de SharePoint anuncio mediante ListData.svc. Para obtener más información, consulte [interfaz REST de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=225999) y [Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Microsoft Windows y SharePoint. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
##  <a name="creating-a-silverlight-application-and-silverlight-web-part"></a>Crear una aplicación de Silverlight y el elemento Web de Silverlight  
 En primer lugar, cree una aplicación de Silverlight en Visual Studio. La aplicación de Silverlight recupera datos de la lista de anuncios de SharePoint mediante el servicio ListData.svc.  
  
> [!NOTE]  
>  Ninguna versión de Silverlight anterior a la 4.0 admite las interfaces necesarias para hacer referencia a datos de la lista de SharePoint.  
  
#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Para crear una aplicación de Silverlight y el elemento web de Silverlight  
  
1.  En la barra de menús, elija **archivo**, **New**, **proyecto** para mostrar la **nuevo proyecto** cuadro de diálogo.  
  
2.  Expanda el **SharePoint** nodo bajo **Visual C#** o **Visual Basic**y, a continuación, elija la **2010** nodo.  
  
3.  En el panel Plantillas, elija la **elemento Web de SharePoint 2010 Silverlight** plantilla.  
  
4.  En el **nombre** cuadro, escriba **SLWebPartTest** y, a continuación, elija la **Aceptar** botón.  
  
     El **Asistente para personalización de SharePoint** aparece el cuadro de diálogo.  
  
5.  En el **especificar el nivel de sitio y la seguridad para la depuración** página, escriba la dirección URL para el sitio del servidor de SharePoint donde desea depurar la definición de sitio o utilice la ubicación predeterminada (http://*nombre del sistema*/) .  
  
6.  En el **¿qué es el nivel de confianza para esta solución de SharePoint?** sección, elija el **implementar como solución de granja de servidores** botón de opción.  
  
     Aunque en este ejemplo usa una solución de granja de servidores, proyectos de elemento web de Silverlight se pueden implementar como granja de servidores o soluciones en espacio aislado. Para obtener más información sobre las soluciones en espacio aislado y soluciones de granja de servidores, consulte [consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  En el **cómo desea asociar el elemento Web de Silverlight** sección de la **especificar información de configuración de Silverlight** página, elija la **crear un nuevo proyecto de Silverlight y asociar con el elemento web** botón de opción.  
  
8.  Cambiar el **nombre** a **SLApplication**, establezca **lenguaje** como **Visual Basic** o **Visual C#**, y, a continuación, establezca **Silverlight versión** a **Silverlight 4.0**.  
  
9. Elija la **finalizar** botón. Los proyectos aparecen en **el Explorador de soluciones**.  
  
     La solución contiene dos proyectos: una aplicación de Silverlight y un elemento web de Silverlight. La aplicación de Silverlight recupera y muestra los datos de lista de SharePoint, y el elemento web de Silverlight hospeda la aplicación de Silverlight, lo que le permite ver en SharePoint.  
  
##  <a name="customizing-the-silverlight-application"></a>Personalizar la aplicación de Silverlight  
 Agregar elementos de código y el diseño a la aplicación de Silverlight.  
  
#### <a name="to-customize-the-silverlight-application"></a>Para personalizar la aplicación de Silverlight  
  
1.  Agregue una referencia a System.Windows.Data ensamblado en la aplicación de Silverlight. Para obtener más información, consulte [Cómo: agregar o quitar referencias mediante el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
2.  En **el Explorador de soluciones**, abra el menú contextual para **referencias**y, a continuación, elija **Agregar referencia de servicio**.  
  
    > [!NOTE]  
    >  Si está utilizando Visual Basic, debe elegir el **mostrar todos los archivos** situado en la parte superior de **el Explorador de soluciones** para mostrar la **referencias** nodo.  
  
3.  En el cuadro Dirección de la **Agregar referencia de servicio** diálogo cuadro, escriba la dirección URL del sitio de SharePoint, como **http://MySPSite**y, a continuación, elija la **vaya** botón.  
  
     Cuando Silverlight busca el servicio de SharePoint OData ListData.svc, reemplaza la dirección con la dirección URL completa del servicio. En este ejemplo, http://myserver se convierte en http://myserver/_vti_bin/ListData.svc.  
  
4.  Elija la **Aceptar** botón para agregar la referencia de servicio al proyecto y use el nombre de servicio predeterminado, ServiceReference1.  
  
5.  En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
6.  Agregar un nuevo origen de datos para el proyecto basándose en el servicio de SharePoint. Para ello, en la barra de menús, elija **vista**, **otras ventanas**, **orígenes de datos**.  
  
     El **orígenes de datos** ventana muestra todos los datos de lista de SharePoint disponibles, como tareas, anuncios y el calendario.  
  
7.  Agregue los datos de la lista de anuncios a la aplicación de Silverlight. También puede arrastrar "Anuncios" desde el **orígenes de datos** ventana en el Diseñador de Silverlight.  
  
     Esto crea un control de cuadrícula enlazado a la lista de anuncios del sitio de SharePoint.  
  
8.  El tamaño del control de cuadrícula para ajustarse a la página de Silverlight.  
  
9. En el archivo de código de MainPage.xaml (MainPage.xaml.cs para Visual C#) o MainPage.xaml.vb para Visual Basic, agregue las siguientes referencias de espacio de nombres.  
  
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
  
10. Agregue las siguientes declaraciones de variable en la parte superior de la clase.  
  
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
   
11. Reemplace el `UserControl_Loaded` procedimiento por lo siguiente.  
  
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
     No olvide reemplazar la *ServerName* marcador de posición con el nombre del servidor que ejecuta SharePoint.  
  
12. Agregue el siguiente procedimiento de control de errores.  
  
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
       
## <a name="modifying-the-silverlight-web-part"></a>Modificar el elemento Web de Silverlight  
 Cambiar una propiedad en el proyecto de elementos web de Silverlight para habilitar la depuración de Silverlight.  
  
#### <a name="to-modify-the-silverlight-web-part"></a>Para modificar el elemento web de Silverlight  
  
1.  Abra el menú contextual para el proyecto de elementos web de Silverlight (**SLWebPartTest**) y, a continuación, elija **propiedades**.  
  
2.  En el **propiedades** ventana, elija la **SharePoint** ficha.  
  
3.  Si aún no está seleccionada, seleccione la **Silverlight Habilitar depuración (en lugar de depuración de Script)** casilla de verificación.  
  
4.  Guarde el proyecto.  
  
##  <a name="testing-the-silverlight-web-part"></a>Probar el elemento Web de Silverlight  
 Probar el nuevo elemento web de Silverlight de SharePoint para asegurarse de que muestran correctamente los datos de la lista de SharePoint.  
  
#### <a name="to-test-the-silverlight-web-part"></a>Para probar el elemento web de Silverlight  
  
1.  Presione la tecla F5 para compilar y ejecutar la solución de SharePoint.  
  
2.  En SharePoint, en la **acciones del sitio** menú, elija **nueva página**.  
  
3.  En el **nueva página** cuadro de diálogo, escriba un título, como **SL Web parte prueba**y, a continuación, elija la **crear** botón.  
  
4.  En el Diseñador de la página, en la **herramientas de edición** ficha, elija **insertar**.  
  
5.  En la franja de pestañas, elija **elemento Web**.  
  
6.  En el **categorías** cuadro, elija la **personalizado** carpeta.  
  
7.  En el **elementos Web** lista, elija el elemento web de Silverlight y, a continuación, elija la **agregar** botón para agregar el elemento web para el diseñador.  
  
8.  Una vez realizadas todas las adiciones a la página web que desee, elija la **página** ficha y, a continuación, elija la **guardar y cerrar** botón en la barra de herramientas.  
  
     El elemento web de Silverlight ahora debería mostrar datos de anuncio desde el sitio de SharePoint. De forma predeterminada, la página se almacena en la lista de páginas del sitio de SharePoint.  
  
    > [!NOTE]  
    >  Al obtener acceso a datos en Silverlight entre dominios, Silverlight protege frente a vulnerabilidades de seguridad que pueden usarse para aprovechar las aplicaciones web. Si tiene problemas al obtener acceso a datos remotos de Silverlight, consulte [hacer que un servicio disponible a través de los límites del dominio](http://go.microsoft.com/fwlink/?LinkId=223276).  
  
## <a name="see-also"></a>Vea también  
 [Crear elementos Web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Implementar, publicar y actualizar paquetes de soluciones de SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  
