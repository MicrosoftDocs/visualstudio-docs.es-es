---
title: 'Tutorial: Creación de un servicio de datos WCF con WPF y Entity Framework | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 12d7e9c25cdf4e0431a7e4b5e3639dc59b76790c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703175"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Tutorial: Creación de un servicio de datos de WCF con WPF y Entity Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial se muestra cómo crear una sencilla [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] que se hospeda en un [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplicación Web y, a continuación, acceder a ella desde una aplicación de Windows Forms.  
  
 En este tutorial:  
  
- Creará una aplicación web para hospedar un [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
- Creará un [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] que represente la tabla Customers de la base de datos Northwind.  
  
- Creará un control [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
- Creará una aplicación cliente y agregará una referencia al [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
- Habilitará el enlace de datos al servicio y generará la interfaz de usuario.  
  
- Opcionalmente agregará funciones de filtrado a la aplicación.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
- Base de datos de ejemplo Northwind.  
  
     Si no dispone de esta base de datos en el equipo de desarrollo, puede descargarla del [Centro de descarga de Microsoft](http://go.microsoft.com/fwlink/?LinkID=98088). Para obtener instrucciones, consulte [descargar bases de datos de ejemplo](https://msdn.microsoft.com/library/ef9d69a1-9461-43fe-94bb-7c836754bcb5).  
  
## <a name="creating-the-service"></a>Crear el servicio web  
 Para crear un [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], agregará un proyecto web, creará un [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] y, a continuación, creará el servicio a partir del modelo.  
  
 En el primer paso, agregará un proyecto web para hospedar el servicio.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-the-web-project"></a>Para crear el proyecto web  
  
1. En la barra de menús, elija **archivo**, **New**, **proyecto**.  
  
2. En el cuadro de diálogo **Nuevo proyecto**, expanda los nodos **Visual Basic** o **Visual C#** y **Web** y después elija la plantilla **Aplicación web ASP.NET**.  
  
3. En el cuadro de texto **Nombre**, escriba **NorthwindWeb** y elija el botón **Aceptar**.  
  
4. En el cuadro de diálogo **Nuevo proyecto ASP.NET**, en la lista **Seleccionar una plantilla**, elija **Vacía** y después elija el botón **Aceptar**.  
  
   En este paso, creará un [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] que represente la tabla Customers de la base de datos Northwind.  
  
#### <a name="to-create-the-entity-data-model"></a>Para crear el Entity Data Model  
  
1. En la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
2. En el cuadro de diálogo **Agregar nuevo elemento**, elija el nodo **Datos** y después elija el elemento **Entity Data Model de ADO.NET**.  
  
3. En el **nombre** texto, escriba `NorthwindModel`y, a continuación, elija el **agregar** botón.  
  
    Aparecerá el Asistente para Entity Data Model.  
  
4. En el Asistente para Entity Data Model, en la página **Elegir contenido del modelo**, elija el elemento **EF Designer de base de datos** y luego elija el botón **Siguiente**.  
  
5. En la página **Elegir la conexión de datos** , siga uno de estos procedimientos:  
  
   - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, elíjala.  
  
        -o bien-  
  
   - Elija el botón **Nueva conexión** para configurar una nueva conexión de datos. Para obtener más información, consulte [agregar nuevas conexiones](../data-tools/add-new-connections.md).  
  
6. Si la base de datos requiere una contraseña, elija el botón de opción **Sí, incluir datos confidenciales en la cadena de conexión** y elija el botón **Siguiente**.  
  
   > [!NOTE]
   > Si aparece un cuadro de diálogo, elija **Sí** para guardar el archivo en su proyecto.  
  
7. En la página **Elija su versión**, elija el botón de opción **Entity Framework 5.0** y después elija el botón **Siguiente**.  
  
   > [!NOTE]
   > Para usar la última versión de Entity Framework 6 con servicios WCF, deberá instalar el paquete NuGet del proveedor de Entity Framework para WCF Data Services. Consulte [usar WCF Data Services 5.6.0 con Entity Framework 6 +](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).  
  
8. En la página **Elija los objetos de base de datos**, expanda el nodo **Tablas**, active la casilla **Customers** y después elija el botón **Finalizar**.  
  
    Se mostrará el diagrama del modelo de entidad y se agregará un archivo NorthwindModel.edmx al proyecto.  
  
   En este paso, creará y probará el servicio de datos.  
  
#### <a name="to-create-the-data-service"></a>Para crear el servicio de datos  
  
1. En la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
2. En el cuadro de diálogo **Agregar nuevo elemento**, elija el nodo **Web** y después elija el elemento **Servicio de datos de WCF 5.6**.  
  
3. En el **nombre** texto, escriba `NorthwindCustomers`y, a continuación, elija el **agregar** botón.  
  
    El archivo NorthwindCustomers.svc aparecerá en el **Editor de código**.  
  
4. En el **Editor de código**, busque el primer comentario `TODO:` y reemplace el código por el texto siguiente:  
  
    [!code-csharp[WCFDataServiceWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#1)]
    [!code-vb[WCFDataServiceWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#1)]  
  
5. Reemplace los comentarios del controlador de eventos `InitializeService` por el siguiente código:  
  
    [!code-csharp[WCFDataServiceWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#2)]
    [!code-vb[WCFDataServiceWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#2)]  
  
6. En la barra de menús, elija **depurar**, **iniciar sin depurar** para ejecutar el servicio. Se abrirá una ventana del explorador y se mostrará el esquema XML del servicio.  
  
7. En el **dirección** barra, escriba `Customers` al final de la dirección URL para NorthwindCustomers.svc y, a continuación, elija el **ENTRAR** clave.  
  
    Se mostrará una representación XML de los datos de la tabla Customers.  
  
   > [!NOTE]
   > En algunos casos, Internet Explorer interpretará incorrectamente los datos como una fuente RSS. Debe asegurarse de que la opción para mostrar las fuentes RSS está deshabilitada. Para obtener más información, consulte [solucionar problemas de referencias de servicio](../data-tools/troubleshooting-service-references.md).  
  
8. Cierre la ventana del explorador.  
  
   En los siguientes pasos creará una aplicación cliente de Windows Forms para utilizar el servicio.  
  
## <a name="creating-the-client-application"></a>Crear la aplicación cliente.  
 Para crear la aplicación cliente, agregará un segundo proyecto, agregará una referencia del servicio al proyecto, configurará un origen de datos y creará una interfaz de usuario para mostrar los datos del servicio.  
  
 En el primer paso, agregará un proyecto de Windows Forms a la solución y lo establecerá como proyecto de inicio.  
  
#### <a name="to-create-the-client-application"></a>Para crear la aplicación cliente  
  
1. En la barra de menús, elija Archivo, **agregar**, **nuevo proyecto**.  
  
2. En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual Basic** o **Visual C#** nodo y elija el **Windows** nodo y, a continuación, elija  **Aplicación de Windows Forms**.  
  
3. En el cuadro de texto **Nombre**, escriba `NorthwindClient` y elija el botón **Aceptar**.  
  
4. En el **Explorador de soluciones**, elija el nodo de proyecto **NorthwindClient**.  
  
5. En la barra de menús, elija **Proyecto**, **Establecer como proyecto de inicio**.  
  
   En este paso, agregará una referencia de servicio al [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] en el proyecto web.  
  
#### <a name="to-add-a-service-reference"></a>Para agregar una referencia de servicio  
  
1. En la barra de menús, elija **proyecto**, **Add Service Reference**.  
  
2. En el cuadro de diálogo **Agregar referencia de servicio**, elija el botón **Detectar**.  
  
    En el campo **Dirección** aparecerá la dirección URL del servicio NorthwindCustomers.  
  
3. Elija el botón **Aceptar** para agregar la referencia del servicio.  
  
   En este paso, configurará un origen de datos para habilitar el enlace de datos al servicio.  
  
#### <a name="to-enable-data-binding-to-the-service"></a>Para habilitar el enlace de datos al servicio  
  
1. En la barra de menús, elija **vista**, **Other Windows**, **orígenes de datos**.  
  
2. En la ventana **Orígenes de datos**, elija el botón **Agregar nuevo origen de datos**.  
  
3. En la página **Elija un tipo de origen de datos** del **Asistente para configuración de orígenes de datos**, elija **Objeto** y después elija el botón **Siguiente**.  
  
4. En la página **Seleccionar los objetos de datos**, expanda el nodo **NorthwindClient** y después expanda el nodo **NorthwindClient.ServiceReference1**.  
  
5. Active la casilla **Customer** y elija el botón **Finalizar**.  
  
   En este paso, creará la interfaz de usuario que mostrará los datos del servicio.  
  
#### <a name="to-create-the-user-interface"></a>Para crear la interfaz de usuario  
  
1. En la ventana **Orígenes de datos**, abra el menú contextual del nodo **Customers** y elija **Copiar**.  
  
2. En el diseñador de formularios de **Form1.vb** o de **Form1.cs**, abra el menú contextual y elija **Pegar**.  
  
    Se agregarán al formulario un control <xref:System.Windows.Forms.DataGridView>, un componente <xref:System.Windows.Forms.BindingSource> y un componente <xref:System.Windows.Forms.BindingNavigator>.  
  
3. Elija el control **CustomersDataGridView** y después en la ventana **Propiedades**, establezca la propiedad **Acoplar** en **Rellenar**.  
  
4. En **el Explorador de soluciones**, abra el menú contextual para el **Form1** nodo y elija **ver código** para abrir el Editor de código y agregue las siguientes importaciones o mediante declaración en el principio del archivo:  
  
   ```vb  
   Imports NorthwindClient.ServiceReference1  
   ```  
  
   ```csharp  
   using NorthwindClient.ServiceReference1;  
   ```  
  
5. Agregue el código siguiente al controlador de eventos `Form1_Load` :  
  
   ```vb  
   Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
           Dim proxy As New NorthwindEntities _  
   (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))  
           Me.CustomersBindingSource.DataSource = proxy.Customers  
       End Sub  
   ```  
  
   ```csharp  
   private void Form1_Load(object sender, EventArgs e)  
   {  
   NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));  
   this.CustomersBindingSource.DataSource = proxy.Customers;  
   }  
  
   ```  
  
6. En **el Explorador de soluciones**, abra el menú contextual del archivo NorthwindCustomers.svc y elija **ver en el explorador**. Se abrirá Internet Explorer y se mostrará el esquema XML del servicio.  
  
7. Copie la dirección URL de la barra de direcciones de Internet Explorer.  
  
8. En el código que agregó en el paso 4, seleccione `http://localhost:53161/NorthwindCustomers.svc/` y reemplácelo por la dirección URL que acaba de copiar.  
  
9. En la barra de menús, elija **depurar**, **Iniciar depuración** para ejecutar la aplicación. Se mostrará la información del cliente.  
  
   Ahora dispone de una aplicación operativa que muestra una lista de clientes del servicio NorthwindCustomers. Si desea exponer datos adicionales a través del servicio, puede modificar el [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] para incluir tablas adicionales de la base de datos Northwind.  
  
   En el siguiente paso opcional aprenderá cómo filtrar los datos que devuelve el servicio.  
  
## <a name="adding-filtering-capabilities"></a>Agregar funciones de filtrado  
 En este paso, personalizará la aplicación para filtrar los datos en función de la ciudad del cliente.  
  
#### <a name="to-add-filtering-by-city"></a>Para agregar el filtrado por ciudad  
  
1. En el **Explorador de soluciones**, abra el menú contextual del nodo **Form1.vb** o **Form1.cs** y elija **Abrir**.  
  
2. Agregue un control <xref:System.Windows.Forms.TextBox> y un control <xref:System.Windows.Forms.Button> desde el **Cuadro de herramientas** al formulario.  
  
3. Abra el menú contextual para el <xref:System.Windows.Forms.Button> controlar y elegir **ver código**y, a continuación, agregue el código siguiente en el `Button1_Click` controlador de eventos:  
  
    ```vb  
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
            Dim proxy As New northwindEntities _  
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))  
            Dim city As String = TextBox1.Text  
  
            If city <> "" Then  
                Me.CustomersBindingSource.DataSource = From c In _  
             proxy.Customers Where c.City = city  
            End If  
  
        End Sub  
    ```  
  
    ```csharp  
    private void Button1_Click(object sender, EventArgs e)  
    {  
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));  
    string city = TextBox1.Text;  
  
    if (!string.IsNullOrEmpty(city)) {  
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;  
    }  
  
    }  
    ```  
  
4. En el código anterior, reemplace `http://localhost:53161/NorthwindCustomers.svc` por la dirección URL del controlador de eventos `Form1_Load`.  
  
5. En la barra de menús, elija **depurar**, **Iniciar depuración** para ejecutar la aplicación.  
  
6. En el cuadro de texto, escriba **London** y después elija el botón. Solo se mostrarán los clientes de Londres.  
  
## <a name="see-also"></a>Vea también  
 [Servicios de Windows Communication Foundation y WCF Data Services en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [Cómo: Agregar, actualizar o eliminar una referencia de servicio de datos de WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)
