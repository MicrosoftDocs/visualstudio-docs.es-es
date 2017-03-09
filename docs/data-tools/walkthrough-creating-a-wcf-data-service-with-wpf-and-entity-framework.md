---
title: "Walkthrough: Creating and Accessing a WCF Data Service in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "data services in Visual Studio"
  - "WCF Data Services, Visual Studio"
  - "ADO.NET Data Services, Visual Studio"
  - "WCF data services in Visual Studio"
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 24
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Walkthrough: Creating and Accessing a WCF Data Service in Visual Studio
En este tutorial se muestra cómo crear un sencillo [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] que se hospeda en una aplicación web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] y al que se tiene acceso desde una aplicación de Windows Forms.  
  
 En este tutorial:  
  
-   Creará una aplicación web para hospedar un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Creará un [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] que represente la tabla Customers de la base de datos Northwind.  
  
-   Creará un control [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Creará una aplicación cliente y agregará una referencia al [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Habilitará el enlace de datos al servicio y generará la interfaz de usuario.  
  
-   Opcionalmente agregará funciones de filtrado a la aplicación.  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Base de datos de ejemplo Northwind.  
  
     Si no tiene esta base de datos en el equipo de desarrollo, puede descargarla desde el [Centro de descarga de Microsoft](http://go.microsoft.com/fwlink/?LinkID=98088).  Para obtener más información, consulte [Descargar bases de datos de ejemplo](../Topic/Downloading%20Sample%20Databases.md).  
  
## Crear el servicio web  
 Para crear un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], agregará un proyecto web, creará un [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] y, a continuación, creará el servicio a partir del modelo.  
  
 En el primer paso, agregará un proyecto web para hospedar el servicio.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para crear el proyecto web  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, expanda los nodos **Visual Basic** o **Visual C\#** y **Web** y, a continuación, elija la plantilla **Aplicación web ASP.NET**.  
  
3.  En el cuadro de texto **Nombre**, escriba NorthwindWeb y elija el botón **Aceptar**.  
  
4.  En el cuadro de diálogo **Nuevo proyecto ASP.NET**, en la lista **Seleccionar una plantilla**, elija **Vacía** y, a continuación, elija el botón **Aceptar**.  
  
 En este paso, creará un [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] que represente la tabla Customers de la base de datos Northwind.  
  
#### Para crear el Entity Data Model  
  
1.  En la barra de menús, elija **Proyecto**, **Agregar nuevo elemento**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento**, elija el nodo **Datos** y, después, elija el elemento **Entity Data Model de ADO.NET**.  
  
3.  En el cuadro de texto **Nombre**, escriba `NorthwindModel` y elija el botón **Agregar**.  
  
     Aparecerá el Asistente para Entity Data Model.  
  
4.  En el Asistente para Entity Data Model, en la página **Elegir contenido del modelo**, elija el elemento **EF Designer de base de datos** y luego elija el botón **Siguiente**.  
  
5.  En la página **Elegir la conexión de datos**, siga uno de estos procedimientos:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, elíjala.  
  
         O bien  
  
    -   Elija el botón **Nueva conexión** para configurar una nueva conexión de datos.  Para obtener más información, consulte [Cómo: Crear conexiones a bases de datos de SQL Server](http://msdn.microsoft.com/es-es/360c340d-e5a6-4a7e-a569-e95d500be43d).  
  
6.  Si la base de datos requiere una contraseña, elija el botón de opción **Sí, incluir datos confidenciales en la cadena de conexión** y elija el botón **Siguiente**.  
  
    > [!NOTE]
    >  Si aparece un cuadro de diálogo, elija **Sí** para guardar el archivo en su proyecto.  
  
7.  En la página **Elija su versión**, elija el botón de opción **Entity Framework 5.0** y, a continuación, elija el botón **Siguiente**.  
  
    > [!NOTE]
    >  Para usar la última versión de Entity Framework 6 con servicios WCF, deberá instalar el paquete NuGet del proveedor de Entity Framework para WCF Data Services.  Vea la entrada de blog sobre cómo [usar WCF Data Services 5.6.0 con Entity Framework 6\+](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).  
  
8.  En la página **Elija los objetos de base de datos**, expanda el nodo **Tablas**, active la casilla **Customers** y, a continuación, elija el botón **Finalizar**.  
  
     Se mostrará el diagrama del modelo de entidad y se agregará un archivo NorthwindModel.edmx al proyecto.  
  
 En este paso, creará y probará el servicio de datos.  
  
#### Para crear el servicio de datos  
  
1.  En la barra de menús, elija **Proyecto**, **Agregar nuevo elemento**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento**, elija el nodo **Web** y, después, elija el elemento **Servicio de datos de WCF 5.6**.  
  
3.  En el cuadro de texto **Nombre**, escriba `NorthwindCustomers` y elija el botón **Agregar**.  
  
     El archivo NorthwindCustomers.svc aparecerá en el **Editor de código**.  
  
4.  En el **Editor de código**, busque el primer comentario `TODO:` y reemplace el código por el texto siguiente:  
  
     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-cs[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]  
  
5.  Reemplace los comentarios del controlador de eventos `InitializeService` por el siguiente código:  
  
     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-cs[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]  
  
6.  Para ejecutar el servicio, en la barra de menús, elija **Depurar**, **Iniciar sin depurar**.  Se abrirá una ventana del explorador y se mostrará el esquema XML del servicio.  
  
7.  En la barra **Dirección**, escriba `Customers` al final de la dirección URL para NorthwindCustomers.svc y, a continuación, elija la tecla ENTRAR.  
  
     Se mostrará una representación XML de los datos de la tabla Customers.  
  
    > [!NOTE]
    >  En algunos casos, Internet Explorer interpretará incorrectamente los datos como una fuente RSS.  Debe asegurarse de que la opción para mostrar las fuentes RSS está deshabilitada.  Para obtener más información, consulte [Troubleshooting Service References](../data-tools/troubleshooting-service-references.md).  
  
8.  Cierre la ventana del explorador.  
  
 En los siguientes pasos creará una aplicación cliente de Windows Forms para utilizar el servicio.  
  
## Crear la aplicación cliente.  
 Para crear la aplicación cliente, agregará un segundo proyecto, agregará una referencia del servicio al proyecto, configurará un origen de datos y creará una interfaz de usuario para mostrar los datos del servicio.  
  
 En el primer paso, agregará un proyecto de Windows Forms a la solución y lo establecerá como proyecto de inicio.  
  
#### Para crear la aplicación cliente  
  
1.  En la barra de menús, elija Archivo, **Agregar**, **Nuevo proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Visual Basic** o **Visual C\#**, elija el nodo **Windows** y, a continuación, elija **Aplicación de Windows Forms**.  
  
3.  En el cuadro de texto **Nombre**, escriba `NorthwindClient` y elija el botón **Aceptar**.  
  
4.  En el **Explorador de soluciones**, elija el nodo de proyecto **NorthwindClient**.  
  
5.  En la barra de menús, elija **Proyecto**, **Establecer como proyecto de inicio**.  
  
 En este paso, agregará una referencia de servicio al [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] en el proyecto web.  
  
#### Para agregar una referencia de servicio  
  
1.  En la barra de menús, elija **Proyecto**, **Agregar referencia de servicio**.  
  
2.  En el cuadro de diálogo **Agregar referencia de servicio**, elija el botón **Detectar**.  
  
     En el campo **Dirección** aparecerá la dirección URL del servicio NorthwindCustomers.  
  
3.  Elija el botón **Aceptar** para agregar la referencia del servicio.  
  
 En este paso, configurará un origen de datos para habilitar el enlace de datos al servicio.  
  
#### Para habilitar el enlace de datos al servicio  
  
1.  En la barra de menús, elija **Ver**, **Otras ventanas**, **Orígenes de datos**.  
  
2.  En la ventana **Orígenes de datos**, elija el botón **Agregar nuevo origen de datos**.  
  
3.  En la página **Elija un tipo de origen de datos** del **Asistente para configuración de orígenes de datos**, elija **Objeto** y, a continuación, elija el botón **Siguiente**.  
  
4.  En la página **Seleccionar los objetos de datos**, expanda el nodo **NorthwindClient** y, a continuación, expanda el nodo **NorthwindClient.ServiceReference1**.  
  
5.  Active la casilla **Customer** y elija el botón **Finalizar**.  
  
 En este paso, creará la interfaz de usuario que mostrará los datos del servicio.  
  
#### Para crear la interfaz de usuario  
  
1.  En la ventana **Orígenes de datos**, abra el menú contextual del nodo **Customers** y elija **Copiar**.  
  
2.  En el diseñador de formularios de **Form1.vb** o de **Form1.cs**, abra el menú contextual y elija **Pegar**.  
  
     Se agregarán al formulario un control <xref:System.Windows.Forms.DataGridView>, un componente <xref:System.Windows.Forms.BindingSource> y un componente <xref:System.Windows.Forms.BindingNavigator>.  
  
3.  Elija el control **CustomersDataGridView** y, a continuación, en la ventana **Propiedades**, establezca la propiedad **Acoplar** en **Rellenar**.  
  
4.  En el **Explorador de soluciones**, abra el menú contextual del nodo **Form1** y elija **Ver código** para abrir el Editor de código. A continuación, agregue la siguiente instrucción Imports o Using en la parte superior del archivo:  
  
    ```vb  
    Imports NorthwindClient.ServiceReference1  
    ```  
  
    ```c#  
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
  
    ```c#  
    private void Form1_Load(object sender, EventArgs e)  
    {  
    NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));  
    this.CustomersBindingSource.DataSource = proxy.Customers;  
    }  
  
    ```  
  
6.  En el **Explorador de soluciones**, abra el menú contextual del archivo NorthwindCustomers.svc y elija **Ver en el explorador**.  Se abrirá Internet Explorer y se mostrará el esquema XML del servicio.  
  
7.  Copie la dirección URL de la barra de direcciones de Internet Explorer.  
  
8.  En el código que agregó en el paso 4, seleccione `http://localhost:53161/NorthwindCustomers.svc/` y reemplácelo por la dirección URL que acaba de copiar.  
  
9. En la barra de menús, elija **Depurar**, **Iniciar depuración** para ejecutar la aplicación.  Se mostrará la información del cliente.  
  
 Ahora dispone de una aplicación operativa que muestra una lista de clientes del servicio NorthwindCustomers.  Si desea exponer datos adicionales a través del servicio, puede modificar el [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] para incluir tablas adicionales de la base de datos Northwind.  
  
 En el siguiente paso opcional aprenderá cómo filtrar los datos que devuelve el servicio.  
  
## Agregar funciones de filtrado  
 En este paso, personalizará la aplicación para filtrar los datos en función de la ciudad del cliente.  
  
#### Para agregar el filtrado por ciudad  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del nodo **Form1.vb** o **Form1.cs** y elija **Abrir**.  
  
2.  Agregue un control <xref:System.Windows.Forms.TextBox> y un control <xref:System.Windows.Forms.Button> desde el **Cuadro de herramientas** al formulario.  
  
3.  Abra el menú contextual del control <xref:System.Windows.Forms.Button> y elija **Ver código**; a continuación, agregue el código siguiente al controlador de eventos `Button1_Click`:  
  
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
  
    ```c#  
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
  
5.  En la barra de menús, elija **Depurar**, **Iniciar depuración** para ejecutar la aplicación.  
  
6.  En el cuadro de texto, escriba London y, a continuación, elija el botón.  Solo se mostrarán los clientes de Londres.  
  
## Vea también  
 [How to: Add, Update, or Remove a WCF Data Service Reference](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)