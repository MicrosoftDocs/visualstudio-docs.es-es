---
title: Crear un elemento Web de Silverlight que muestre OData para SharePoint
titleSuffix: ''
description: Cree un elemento Web de Silverlight que muestre OData para SharePoint. Personalice la aplicación de Silverlight y modifique y pruebe el elemento Web de Silverlight.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ee35ecc9cfa49f445e93677df9d2917150bc1e74
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847835"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Tutorial: crear un elemento Web de Silverlight que muestre OData para SharePoint
  SharePoint 2010 expone sus datos de lista por medio de OData. En SharePoint, el servicio de OData se implementa mediante el servicio RESTful ListData. SVC. En este tutorial se muestra cómo crear un elemento Web de SharePoint que hospeda una aplicación de Silverlight. La aplicación de Silverlight muestra información de la lista de anuncios de SharePoint mediante ListData. SVC. Para obtener más información, vea [interfaz de REST de SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ff521587(v=office.14)) y [Open Data Protocol](https://www.odata.org/).

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- Ediciones compatibles de Microsoft Windows y SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Crear una aplicación de Silverlight y un elemento Web de Silverlight
 En primer lugar, cree una aplicación de Silverlight en Visual Studio. La aplicación de Silverlight recupera datos de la lista de anuncios de SharePoint mediante el servicio ListData. SVC.

> [!NOTE]
> Ninguna versión de Silverlight anterior a 4,0 admite las interfaces necesarias para hacer referencia a los datos de lista de SharePoint.

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Para crear una aplicación de Silverlight y un elemento Web de Silverlight

1. En la barra de menús, elija **archivo**  >  **nuevo**  >  **proyecto** para mostrar el cuadro de diálogo **nuevo proyecto** .

2. Expanda el nodo **SharePoint** en **Visual C#** o **Visual Basic** y, a continuación, elija el nodo **2010** .

3. En el panel plantillas, elija la plantilla de **elemento Web Silverlight 2010 de SharePoint** .

4. En el cuadro **nombre** , escriba **SLWebPartTest** y elija el botón **Aceptar** .

    Aparece el cuadro de diálogo **Asistente para personalización de SharePoint** .

5. En la página **especifique el sitio y el nivel de seguridad de la depuración** , escriba la dirección URL del sitio del servidor de SharePoint en el que desea depurar la definición del sitio o use la ubicación predeterminada (<em>nombre del sistema</em>http:///).

6. En la sección **¿cuál es el nivel de confianza de esta solución de SharePoint?** , elija el botón de opción **implementar como solución de granja de servidores** .

    Aunque en este ejemplo se usa una solución de granja, los proyectos de elementos Web de Silverlight se pueden implementar como soluciones de granja o de espacio aislado. Para obtener más información sobre soluciones en espacio aislado y soluciones de granja, consulte consideraciones sobre las soluciones en [espacio aislado](../sharepoint/sandboxed-solution-considerations.md).

7. En la sección **¿Cómo desea asociar el elemento Web de Silverlight** de la página **especificar información de configuración de Silverlight** ?, elija el botón de opción **crear un nuevo proyecto de Silverlight y asociarlo con el elemento Web** .

8. Cambie el **nombre** a **SLApplication**, establezca **Language** en **Visual Basic** o **Visual C#** y, a continuación, establezca la **versión de Silverlight** en **Silverlight 4,0**.

9. Elija el botón **Finalizar**. Los proyectos aparecen en **Explorador de soluciones**.

     La solución contiene dos proyectos: una aplicación de Silverlight y un elemento Web de Silverlight. La aplicación de Silverlight recupera y muestra los datos de la lista de SharePoint, y el elemento Web de Silverlight hospeda la aplicación de Silverlight, lo que le permite verla en SharePoint.

## <a name="customize-the-silverlight-application"></a>Personalización de la aplicación de Silverlight
 Agregue código y elementos de diseño a la aplicación de Silverlight.

#### <a name="to-customize-the-silverlight-application"></a>Para personalizar la aplicación de Silverlight

1. Agregue una referencia de ensamblado a System. Windows. Data en la aplicación de Silverlight. Para obtener más información, vea [Cómo: agregar o quitar referencias mediante el cuadro de diálogo Agregar referencia](/previous-versions/wkze6zky(v=vs.140)).

2. En **Explorador de soluciones**, abra el menú contextual para **referencias** y, a continuación, elija **Agregar referencia de servicio**.

    > [!NOTE]
    > Si está utilizando Visual Basic, debe elegir el icono **Mostrar todos los archivos** situado en la parte superior de **Explorador de soluciones** para mostrar el nodo **referencias** .

3. En el cuadro Dirección del cuadro de diálogo **Agregar referencia de servicio** , escriba la dirección URL del sitio de SharePoint, como **http://MySPSite** y, a continuación, elija el botón **ir** .

     Cuando Silverlight ubica el servicio OData de SharePoint ListData. SVC, lo reemplaza por la dirección URL del servicio completa. En este ejemplo, http://myserver se convierte en http://myserver/_vti_bin/ListData.svc .

4. Elija el botón **Aceptar** para agregar la referencia de servicio al proyecto y use el nombre de servicio predeterminado, ServiceReference1.

5. En la barra de menús, elija **Compilar** > **Compilar solución**.

6. Agregue un nuevo origen de datos al proyecto basado en el servicio de SharePoint. Para ello, en la barra de menús, elija **Ver**  >  **otros**  >  **orígenes de datos** de Windows.

     La ventana **orígenes de datos** muestra todos los datos de lista de SharePoint disponibles, como tareas, anuncios y calendario.

7. Agregue los datos de la lista de anuncios a la aplicación de Silverlight. Puede arrastrar "anuncios" desde la ventana **orígenes de datos** hasta Silverlight Designer.

     Esto crea un control de cuadrícula enlazado a la lista de anuncios del sitio de SharePoint.

8. Cambie el tamaño del control de cuadrícula para que se ajuste a la página de Silverlight.

9. En el archivo de código MainPage. XAML (*mainpage.Xaml.CS* para Visual C# o *mainpage. Xaml. VB* para Visual Basic), agregue las siguientes referencias de espacio de nombres.

    ```vb
    ' Add the following three Imports statements.
    Imports SLApplication.ServiceReference1
    Imports System.Windows.Data
    Imports System.Data.Services.Client
    ```

    ```csharp
    // Add the following three using directives.
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

     Asegúrese de reemplazar el marcador de posición *ServerName* por el nombre del servidor que ejecuta SharePoint.

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

## <a name="modify-the-silverlight-web-part"></a>Modificar el elemento Web de Silverlight
 Cambie una propiedad en el proyecto de elemento Web de Silverlight para habilitar la depuración de Silverlight.

#### <a name="to-modify-the-silverlight-web-part"></a>Para modificar el elemento Web de Silverlight

1. Abra el menú contextual del proyecto de elemento Web de Silverlight (**SLWebPartTest**) y, a continuación, elija **propiedades**.

2. En la ventana **propiedades** , elija la pestaña **SharePoint** .

3. Si aún no está seleccionada, active la casilla **Habilitar depuración de Silverlight (en lugar de depuración de scripts)** .

4. Guarde el proyecto.

## <a name="test-the-silverlight-web-part"></a>Probar el elemento Web de Silverlight
 Pruebe el nuevo elemento Web de Silverlight en SharePoint para asegurarse de que muestra los datos de la lista de SharePoint correctamente.

#### <a name="to-test-the-silverlight-web-part"></a>Para probar el elemento Web de Silverlight

1. Elija la tecla **F5** para compilar y ejecutar la solución de SharePoint.

2. En SharePoint, en el menú **acciones del sitio** , elija **nueva página**.

3. En el cuadro de diálogo **nueva página** , escriba un título, como la **prueba de elemento Web SL** y, a continuación, elija el botón **crear** .

4. En el diseñador de páginas, en la pestaña **herramientas de edición** , elija **Insertar**.

5. En la franja de pestañas, elija **elemento Web**.

6. En el cuadro **categorías** , elija la carpeta **personalizada** .

7. En la lista **elementos Web** , elija el elemento Web de Silverlight y, a continuación, elija el botón **Agregar** para agregar el elemento Web al diseñador.

8. Una vez que haya realizado todas las adiciones a la página web que desee, elija la pestaña **Página** y, a continuación, elija el botón **Guardar & cerrar** en la barra de herramientas.

     El elemento Web de Silverlight debería mostrar ahora los datos del anuncio del sitio de SharePoint. De forma predeterminada, la página se almacena en la lista páginas del sitio de SharePoint.

    > [!NOTE]
    > Al tener acceso a los datos de Silverlight entre dominios, Silverlight protege frente a las vulnerabilidades de seguridad que se pueden usar para aprovechar las aplicaciones Web. Si tiene problemas al obtener acceso a datos remotos en Silverlight, consulte [hacer que un servicio esté disponible a través](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc197955(v=vs.95))de los límites del dominio.

## <a name="see-also"></a>Vea también
- [Creación de elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Implementar, publicar y actualizar paquetes de soluciones de SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)