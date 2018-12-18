---
title: 'Tutorial: Crear un elemento Web de Silverlight que muestre OData para SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 67742078cefcd0608d1cff9a5bab609053544392
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296117"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Tutorial: Crear un elemento web de Silverlight que muestre OData para SharePoint
  SharePoint 2010 expone sus datos de la lista por medio de OData. En SharePoint, el servicio de OData se implementa el servicio RESTful ListData.svc. Este tutorial muestra cómo crear un elemento web de SharePoint que hospeda una aplicación de Silverlight. La aplicación de Silverlight, muestra información de la lista de SharePoint anuncio mediante ListData.svc. Para obtener más información, consulte [interfaz REST de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=225999) y [Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Microsoft Windows y SharePoint.
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Crear una aplicación de Silverlight y el elemento web de Silverlight
 En primer lugar, cree una aplicación de Silverlight en Visual Studio. La aplicación de Silverlight recupera datos de la lista de anuncios de SharePoint mediante el servicio ListData.svc.  
  
> [!NOTE]  
>  No hay ninguna versión de Silverlight antes 4.0 admite las interfaces necesarias para hacer referencia a datos de la lista de SharePoint.  
  
#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Para crear una aplicación de Silverlight y el elemento web de Silverlight
  
1. En la barra de menús, elija **archivo** > **New** > **proyecto** para mostrar el **nuevo proyecto** cuadro de diálogo.  
  
2. Expanda el **SharePoint** nodo bajo **Visual C#** o **Visual Basic**y, a continuación, elija el **2010** nodo.  
  
3. En el panel Plantillas, elija el **elemento Web de Silverlight de SharePoint 2010** plantilla.  
  
4. En el **nombre** , escriba **SLWebPartTest** y, a continuación, elija el **Aceptar** botón.  
  
    El **Asistente de personalización de SharePoint** aparece el cuadro de diálogo.  
  
5. En el **especificar el nivel de sitio y de seguridad para la depuración** página, escriba la dirección URL del sitio de SharePoint server donde desea depurar la definición de sitio o usar la ubicación predeterminada (http://<em>nombre del sistema</em>/) .  
  
6. En el **¿qué es el nivel de confianza para esta solución de SharePoint?** sección, elija el **implementar como solución de granja de servidores** botón de opción.  
  
    Aunque este ejemplo usa una solución de granja de servidores, proyectos de elementos web de Silverlight se pueden implementar como granja de servidores o soluciones en espacio aislado. Para obtener más información sobre las soluciones en espacio aislado y soluciones de granja de servidores, consulte [consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
7. En el **cómo desea asociar el elemento Web de Silverlight** sección de la **especificar información de configuración de Silverlight** página, elija la **crear un nuevo proyecto de Silverlight y asociarlo con el elemento web** botón de opción.  
  
8. Cambiar el **nombre** a **SLApplication**, establezca **lenguaje** como **Visual Basic** o **Visual C#**, y, a continuación, establezca **Silverlight versión** a **Silverlight 4.0**.  
  
9. Elija la **finalizar** botón. Los proyectos que aparecen en **el Explorador de soluciones**.  
  
     La solución contiene dos proyectos: una aplicación de Silverlight y un elemento web de Silverlight. La aplicación de Silverlight recupera y muestra los datos de la lista de SharePoint, y el elemento web de Silverlight hospeda la aplicación de Silverlight, lo que le permite verlo en SharePoint.  
  
## <a name="customize-the-silverlight-application"></a>Personalizar la aplicación de Silverlight
 Agregar elementos de código y el diseño a la aplicación de Silverlight.  
  
#### <a name="to-customize-the-silverlight-application"></a>Para personalizar la aplicación de Silverlight
  
1.  Agregue una referencia a System.Windows.Data ensamblado en la aplicación de Silverlight. Para obtener más información, consulte [Cómo: agregar o quitar referencias mediante el cuadro de diálogo Agregar referencia](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
2.  En **el Explorador de soluciones**, abra el menú contextual para **referencias**y, a continuación, elija **Add Service Reference**.  
  
    > [!NOTE]  
    >  Si está utilizando Visual Basic, debe elegir el **mostrar todos los archivos** situado en la parte superior de **el Explorador de soluciones** para mostrar el **referencias** nodo.  
  
3.  En el cuadro Dirección de la **Add Service Reference** diálogo cuadro, escriba la dirección URL del sitio de SharePoint, como **http://MySPSite**y, a continuación, elija el **vaya** botón.  
  
     Cuando Silverlight localiza el servicio SharePoint OData ListData.svc, reemplaza la dirección con la dirección URL completa del servicio. En este ejemplo, http://myserver se convierte en http://myserver/_vti_bin/ListData.svc.  
  
4.  Elija la **Aceptar** botón para agregar la referencia de servicio al proyecto y use el nombre de servicio predeterminado, ServiceReference1.  
  
5.  En la barra de menús, elija **Compilar** > **Compilar solución**.  
  
6.  Agregar un nuevo origen de datos al proyecto basado en el servicio de SharePoint. Para ello, en la barra de menús, elija **vista** > **Other Windows** > **orígenes de datos**.  
  
     El **orígenes de datos** ventana muestra todos los datos de lista de SharePoint disponibles, como tareas, anuncios y el calendario.  
  
7.  Agregue los datos de la lista de anuncios a la aplicación de Silverlight. Puede arrastrar "Anuncios" desde el **orígenes de datos** ventana hasta Silverlight designer.  
  
     Esto crea un control de cuadrícula enlazado a la lista de anuncios del sitio de SharePoint.  
  
8.  El tamaño del control de cuadrícula para ajustarse a la página de Silverlight.  
  
9. En el archivo de código de MainPage.xaml (*MainPage.xaml.cs* para Visual C# o *MainPage.xaml.vb* para Visual Basic), agregue las siguientes referencias de espacio de nombres.  
  
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
     No olvide reemplazar el *ServerName* marcador de posición con el nombre del servidor que ejecuta SharePoint.  
  
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
       
## <a name="modify-the-silverlight-web-part"></a>Modificar el elemento web de Silverlight
 Cambiar una propiedad en el proyecto de elemento web de Silverlight para habilitar la depuración de Silverlight.  
  
#### <a name="to-modify-the-silverlight-web-part"></a>Para modificar el elemento web de Silverlight  
  
1.  Abra el menú contextual para el proyecto de elemento web de Silverlight (**SLWebPartTest**) y, a continuación, elija **propiedades**.  
  
2.  En el **propiedades** ventana, elija el **SharePoint** ficha.  
  
3.  Si aún no está seleccionada, seleccione el **Silverlight Habilitar depuración (en lugar de depuración de Script)** casilla de verificación.  
  
4.  Guarde el proyecto.  
  
## <a name="test-the-silverlight-web-part"></a>Probar el elemento web de Silverlight
 Pruebe el nuevo elemento web de Silverlight en SharePoint para asegurarse de que muestran correctamente los datos de la lista de SharePoint.  
  
#### <a name="to-test-the-silverlight-web-part"></a>Para probar el elemento web de Silverlight  
  
1.  Elija la **F5** clave para compilar y ejecutar la solución de SharePoint.  
  
2.  En SharePoint, en la **acciones del sitio** menú, elija **nueva página**.  
  
3.  En el **nueva página** cuadro de diálogo, escriba un título, como **SL Web parte prueba**y, a continuación, elija el **crear** botón.  
  
4.  En el Diseñador de páginas, en el **herramientas de edición de** ficha, elija **insertar**.  
  
5.  En la franja de pestañas, elija **elemento Web**.  
  
6.  En el **categorías** , seleccione el **personalizado** carpeta.  
  
7.  En el **elementos Web** lista, elija el elemento web de Silverlight y, a continuación, elija el **agregar** para agregar el elemento web para el diseñador.  
  
8.  Una vez realizadas todas las adiciones a la página web que desee, elija el **página** pestaña y, a continuación, elija el **guardar y cerrar** botón en la barra de herramientas.  
  
     El elemento web de Silverlight ahora debe mostrar datos de anuncio desde el sitio de SharePoint. De forma predeterminada, la página se almacena en la lista de las páginas del sitio de SharePoint.  
  
    > [!NOTE]  
    >  Al obtener acceso a datos en Silverlight entre dominios, Silverlight protege contra vulnerabilidades de seguridad que se pueden usar para aprovechar las aplicaciones web. Si tiene problemas al obtener acceso a datos remotos en Silverlight, vea [hacer que un servicio disponible a través de los límites del dominio](http://go.microsoft.com/fwlink/?LinkId=223276).  
  
## <a name="see-also"></a>Vea también
 [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Implementar, publicar y actualizar los paquetes de solución de SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  
