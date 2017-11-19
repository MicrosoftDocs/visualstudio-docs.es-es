---
title: 'Tutorial: Crear un servicio de datos WCF con WPF y Entity Framework | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: aed66709c89c84c6dc4062ca8a4c2c3f38b368ec
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Tutorial: Crear un servicio de datos WCF con WPF y Entity Framework
Este tutorial muestra cómo crear un sencillo [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] que se hospeda en un [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicación Web y, a continuación, obtener acceso a él desde una aplicación de formularios Windows Forms.  
  
En este tutorial:  
  
-   Creará una aplicación web para hospedar un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Creará un [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] que represente la tabla Customers de la base de datos Northwind.  
  
-   Creará un control [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Creará una aplicación cliente y agregará una referencia al [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Habilitará el enlace de datos al servicio y generará la interfaz de usuario.  
  
-   Opcionalmente agregará funciones de filtrado a la aplicación.  
  
## <a name="prerequisites"></a>Requisitos previos  
Este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.  
  
1.  Si no tiene SQL Server Express LocalDB, puede instalarlo desde el [página de descarga de ediciones de SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), o a través del **instalador de Visual Studio**. El instalador de Visual Studio, se puede instalar SQL Server Express LocalDB como parte de la **almacenamiento de datos y el procesamiento** carga de trabajo, o como un componente individual.  
  
2.  Instalar la base de datos de ejemplo Northwind, siga estos pasos:  

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la **almacenamiento de datos y el procesamiento** carga de trabajo en el instalador de Visual Studio.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta...** .  

       Se abre una ventana del editor de consultas.  

    2. Copia la [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de T-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.  

    3. Pegue el script de T-SQL en el editor de consultas y, a continuación, elija la **Execute** botón.  

       Después de unos minutos, finaliza la ejecución de la consulta y se crea la base de datos Northwind.  
  
## <a name="creating-the-service"></a>Crear el servicio web  
Para crear un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], agregará un proyecto web, creará un [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] y, a continuación, creará el servicio a partir del modelo.  
  
En el primer paso, agregará un proyecto web para hospedar el servicio.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-the-web-project"></a>Para crear el proyecto web  
  
1.  En la barra de menús, elija **archivo**, **New**, **proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual Basic** o **Visual C#** y **Web** nodos y, a continuación, elija la **ASP. Aplicación Web de NET** plantilla.  
  
3.  En el **nombre** texto cuadro, escriba **NorthwindWeb**y, a continuación, elija la **Aceptar** botón.  
  
4.  En el **nuevo proyecto ASP.NET** cuadro de diálogo la **seleccione una plantilla de** elija **vacía**y, a continuación, elija la **Aceptar** botón.  
  
En el paso siguiente, aprenderá a crear un [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] que representa la tabla Customers de la base de datos Northwind.  
  
#### <a name="to-create-the-entity-data-model"></a>Para crear el Entity Data Model  
  
1.  En la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
2.  En el **Agregar nuevo elemento** diálogo cuadro, elija la **datos** nodo y, a continuación, elija la **ADO.NET Entity Data Model** elemento.  
  
3.  En el **nombre** texto cuadro, escriba `NorthwindModel`y, a continuación, elija la **agregar** botón.  
  
     Aparecerá el Asistente para Entity Data Model.  
  
4.  En el Asistente de Entity Data Model, en la **Elegir contenido del modelo** página, elija la **EF Designer de base de datos** de elemento y, a continuación, elija la **siguiente** botón.  
  
5.  En la página **Elegir la conexión de datos** , siga uno de estos procedimientos:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, elíjala.  
  
         O bien  
  
    -   Elija la **nueva conexión** botón para configurar una nueva conexión de datos. Para obtener más información, consulte [agregar nuevas conexiones](../data-tools/add-new-connections.md).  
  
6.  Si la base de datos requiere una contraseña, elija la **Sí, incluir datos confidenciales en la cadena de conexión** botón de opción y, a continuación, elija la **siguiente** botón.  
  
    > [!NOTE]
    >  Si aparece un cuadro de diálogo, elija **Sí** para guardar el archivo en el proyecto.  
  
7.  En el **elija su versión** página, elija la **Entity Framework 5.0** botón de opción y, a continuación, elija la **siguiente** botón.  
  
    > [!NOTE]
    >  Para usar la versión más reciente de Entity Framework 6 con servicios de WCF, debe instalar el paquete de NuGet del proveedor de WCF datos servicios Entity Framework. Vea [usar WCF Data Services 5.6.0 con Entity Framework 6 +](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).  
  
8.  En el **elija los objetos de base de datos** página, expanda la **tablas** nodo, seleccione el **clientes** casilla de verificación y, a continuación, elija la **finalizar** botón.  
  
     Se mostrará el diagrama del modelo de entidad y se agregará un archivo NorthwindModel.edmx al proyecto.  
  
En el paso siguiente, creará y probará el servicio de datos.  
  
#### <a name="to-create-the-data-service"></a>Para crear el servicio de datos  
  
1.  En la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
2.  En el **Agregar nuevo elemento** diálogo cuadro, elija la **Web** nodo y, a continuación, elija la **5.6 de servicio de datos de WCF** elemento.  
  
3.  En el **nombre** texto cuadro, escriba `NorthwindCustomers`y, a continuación, elija la **agregar** botón.  
  
     El archivo NorthwindCustomers.svc aparecerá en el **Editor de código**.  
  
4.  En el **Editor de código**, busque el primer `TODO:` comentar y reemplace el código con lo siguiente:  
  
     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]  
  
5.  Reemplace los comentarios del controlador de eventos `InitializeService` por el siguiente código:  
  
     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]  
  
6.  En la barra de menús, elija **depurar**, **iniciar sin depurar** para ejecutar el servicio. Se abrirá una ventana del explorador y se mostrará el esquema XML del servicio.  
  
7.  En el **dirección** barra, escriba `Customers` al final de la dirección URL para NorthwindCustomers.svc y, a continuación, elija la **ENTRAR** clave.  
  
     Se mostrará una representación XML de los datos de la tabla Customers.  
  
    > [!NOTE]
    >  En algunos casos, Internet Explorer interpretará incorrectamente los datos como una fuente RSS. Debe asegurarse de que la opción para mostrar las fuentes RSS está deshabilitada. Para obtener más información, consulte [solucionar problemas de referencias de servicio](../data-tools/troubleshooting-service-references.md).  
  
8.  Cierre la ventana del explorador.  
  
En los siguientes pasos creará una aplicación cliente de Windows Forms para utilizar el servicio.  
  
## <a name="creating-the-client-application"></a>Crear la aplicación cliente.  
 Para crear la aplicación cliente, agregará un segundo proyecto, agregará una referencia del servicio al proyecto, configurará un origen de datos y creará una interfaz de usuario para mostrar los datos del servicio.  
  
 En el primer paso, agregará un proyecto de Windows Forms a la solución y lo establecerá como proyecto de inicio.  
  
#### <a name="to-create-the-client-application"></a>Para crear la aplicación cliente  
  
1.  En la barra de menús, elija Archivo, **agregar**, **nuevo proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual Basic** o **Visual C#** nodo y elija la **Windows** nodo y, a continuación, elija  **Aplicación de formularios Windows Forms**.  
  
3.  En el cuadro de texto **Nombre**, escriba `NorthwindClient` y elija el botón **Aceptar**.  
  
4.  En **el Explorador de soluciones**, elija la **NorthwindClient** nodo del proyecto.  
  
5.  En la barra de menús, elija **proyecto**, **establecer como proyecto de inicio**.  
  
En el paso siguiente, agregará una referencia de servicio a la [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] en el proyecto Web.  
  
#### <a name="to-add-a-service-reference"></a>Para agregar una referencia de servicio  
  
1.  En la barra de menús, elija **proyecto**, **Agregar referencia de servicio**.  
  
2.  En el **Agregar referencia de servicio** diálogo cuadro, elija la **Discover** botón.  
  
     La dirección URL del servicio NorthwindCustomers aparece en la **dirección** campo.  
  
3.  Elija la **Aceptar** botón para agregar la referencia de servicio.  
  
En el paso siguiente, configurará un origen de datos para habilitar el enlace de datos para el servicio.  
  
#### <a name="to-enable-data-binding-to-the-service"></a>Para habilitar el enlace de datos al servicio  
  
1.  En la barra de menús, elija **vista**, **otras ventanas**, **orígenes de datos**.  
  
2.  En el **orígenes de datos** ventana, elija la **Agregar nuevo origen de datos** botón.  
  
3.  En el **elegir un tipo de origen de datos** página de la **Asistente para configuración de orígenes de datos**, elija **objeto**y, a continuación, elija la **siguiente** botón .  
  
4.  En el **seleccionar objetos de datos** página, expanda la **NorthwindClient** nodo y, a continuación, expanda el **NorthwindClient.ServiceReference1** nodo.  
  
5.  Seleccione **cliente** casilla de verificación y, a continuación, elija la **finalizar** botón.  
  
En el paso siguiente, creará la interfaz de usuario que mostrará los datos del servicio.  
  
#### <a name="to-create-the-user-interface"></a>Para crear la interfaz de usuario  
  
1.  En el **orígenes de datos** ventana, abra el menú contextual para el **clientes** nodo y elija **copia**.  
  
2.  En el **Form1.vb** o **Form1.cs** Diseñador de formularios, abra el menú contextual y elija **pegar**.  
  
     Se agregarán al formulario un control <xref:System.Windows.Forms.DataGridView>, un componente <xref:System.Windows.Forms.BindingSource> y un componente <xref:System.Windows.Forms.BindingNavigator>.  
  
3.  Elija la **CustomersDataGridView** (control) y, a continuación, en la **propiedades** ventana conjunto el **acoplar** propiedad **rellenar**.  
  
4.  En **el Explorador de soluciones**, abra el menú contextual para el **Form1** nodo y elija **ver código** para abrir el Editor de código y agregue las siguientes importaciones o mediante declaración en el principio del archivo:  
  
    ```vb  
    Imports NorthwindClient.ServiceReference1  
    ```  
  
    ```csharp  
    using NorthwindClient.ServiceReference1;  
    ```  
  
5.  Agregue el código siguiente al controlador de eventos `Form1_Load`:  
  
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
  
6.  En **el Explorador de soluciones**, abra el menú contextual para el archivo NorthwindCustomers.svc y elija **ver en el explorador**. Se abrirá Internet Explorer y se mostrará el esquema XML del servicio.  
  
7.  Copie la dirección URL de la barra de direcciones de Internet Explorer.  
  
8.  En el código que agregó en el paso 4, seleccione `http://localhost:53161/NorthwindCustomers.svc/` y reemplácelo por la dirección URL que acaba de copiar.  
  
9. En la barra de menús, elija **depurar**, **Iniciar depuración** para ejecutar la aplicación. Se mostrará la información del cliente.  
  
 Ahora dispone de una aplicación operativa que muestra una lista de clientes del servicio NorthwindCustomers. Si desea exponer datos adicionales a través del servicio, puede modificar el [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] para incluir tablas adicionales de la base de datos Northwind.  
  
En el siguiente paso opcional aprenderá cómo filtrar los datos que devuelve el servicio.  
  
## <a name="adding-filtering-capabilities"></a>Agregar funciones de filtrado  
 En este paso, personalizará la aplicación para filtrar los datos en función de la ciudad del cliente.  
  
#### <a name="to-add-filtering-by-city"></a>Para agregar el filtrado por ciudad  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para el **Form1.vb** o **Form1.cs** nodo y elija **abrir**.  
  
2.  Agregar un <xref:System.Windows.Forms.TextBox> control y un <xref:System.Windows.Forms.Button> controlar desde la **cuadro de herramientas** al formulario.  
  
3.  Abra el menú contextual para el <xref:System.Windows.Forms.Button> de control y elija **ver código**y, a continuación, agregue el código siguiente en el `Button1_Click` controlador de eventos:  
  
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
  
4.  En el código anterior, reemplace `http://localhost:53161/NorthwindCustomers.svc` por la dirección URL del controlador de eventos `Form1_Load`.  
  
5.  En la barra de menús, elija **depurar**, **Iniciar depuración** para ejecutar la aplicación.  
  
6.  En el cuadro de texto, escriba **Londres**y, a continuación, elija el botón. Solo se mostrarán los clientes de Londres.  
  
## <a name="see-also"></a>Vea también  
 [Servicios de Windows Communication Foundation y servicios de datos WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [Cómo: Agregar, actualizar o quitar una referencia de servicio de datos de WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)