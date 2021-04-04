---
title: Crear un servicio de datos de WCF con WPF & Entity Framework
description: Cree un servicio de datos de WCF con WPF y Entity Framework hospedado en una aplicación Web de ASP.NET y, a continuación, acceda a él desde una aplicación Windows Forms.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: f519d8e3bfe01fc3e4a1e4cfe82f4f8502c84821
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215700"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Tutorial: Crear un servicio de datos de WCF con WPF y Entity Framework
En este tutorial se muestra cómo crear un sencillo [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] que se hospeda en una aplicación web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] y al que se accede desde una aplicación de Windows Forms.

En este tutorial:

- Creará una aplicación web para hospedar un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Cree un [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] que represente la `Customers` tabla en la base de datos Northwind.

- Creará un control [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Creará una aplicación cliente y agregará una referencia al [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Habilitará el enlace de datos al servicio y generará la interfaz de usuario.

- Opcionalmente agregará funciones de filtrado a la aplicación.

## <a name="prerequisites"></a>Prerrequisitos
En este tutorial se usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo desde la [Página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o a través de la **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** , o como un componente individual.

2. Instale la base de datos de ejemplo Northwind siguiendo estos pasos:

    1. En Visual Studio, abra la ventana **Explorador de objetos de SQL Server** . (**Explorador de objetos de SQL Server** se instala como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** en el instalador de Visual Studio). Expanda el nodo **SQL Server** . Haga clic con el botón secundario en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copie el [script de Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el portapapeles. Este script T-SQL crea la base de datos Northwind desde cero y la rellena con datos.

    3. Pegue el script T-SQL en el editor de consultas y, a continuación, elija el botón **Ejecutar** .

       Tras un breve período de tiempo, la consulta termina de ejecutarse y se crea la base de datos Northwind.

## <a name="creating-the-service"></a>Crear el servicio web
Para crear un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], agregará un proyecto web, creará un [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] y después creará el servicio a partir del modelo.

En el primer paso, agregará un proyecto web para hospedar el servicio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-the-web-project"></a>Para crear el proyecto web

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

2. En el cuadro de diálogo **Nuevo proyecto**, expanda los nodos **Visual Basic** o **Visual C#** y **Web** y después elija la plantilla **Aplicación web ASP.NET**.

3. En el cuadro de texto **Nombre**, escriba **NorthwindWeb** y elija el botón **Aceptar**.

4. En el cuadro de diálogo **Nuevo proyecto ASP.NET**, en la lista **Seleccionar una plantilla**, elija **Vacía** y después elija el botón **Aceptar**.

En el paso siguiente, creará un [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] que representa la `Customers` tabla en la base de datos Northwind.

### <a name="to-create-the-entity-data-model"></a>Para crear el Entity Data Model

1. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento**, elija el nodo **Datos** y después elija el elemento **Entity Data Model de ADO.NET**.

3. En el cuadro de texto **nombre** , escriba `NorthwindModel` y, a continuación, elija el botón **Agregar** .

     Aparecerá el Asistente para Entity Data Model.

4. En el Asistente para Entity Data Model, en la página **Elegir contenido del modelo**, elija el elemento **EF Designer de base de datos** y luego elija el botón **Siguiente**.

5. En la página **Elegir la conexión de datos** , siga uno de estos procedimientos:

    - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, elíjala.

         O bien

    - Elija el botón **Nueva conexión** para configurar una nueva conexión de datos. Para obtener más información, consulte [Agregar nuevas conexiones](../data-tools/add-new-connections.md).

6. Si la base de datos requiere una contraseña, elija el botón de opción **Sí, incluir datos confidenciales en la cadena de conexión** y elija el botón **Siguiente**.

    > [!NOTE]
    > Si aparece un cuadro de diálogo, elija **Sí** para guardar el archivo en su proyecto.

7. En la página **Elija su versión**, elija el botón de opción **Entity Framework 5.0** y después elija el botón **Siguiente**.

    > [!NOTE]
    > Para usar la última versión de Entity Framework 6 con servicios WCF, deberá instalar el paquete NuGet del proveedor de Entity Framework para WCF Data Services. Vea [uso de servicios de datos de WCF 5.6.0 del con Entity Framework 6 +](https://devblogs.microsoft.com/odata/using-wcf-data-services-5-6-0-with-entity-framework-6/).

8. En la página **Elija los objetos de base de datos**, expanda el nodo **Tablas**, active la casilla **Customers** y después elija el botón **Finalizar**.

     Se muestra el diagrama del modelo de entidad y se agrega un archivo *NorthwindModel. edmx* al proyecto.

En el paso siguiente, creará y probará el servicio de datos.

### <a name="to-create-the-data-service"></a>Para crear el servicio de datos

1. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento**, elija el nodo **Web** y después elija el elemento **Servicio de datos de WCF 5.6**.

3. En el cuadro de texto **nombre** , escriba `NorthwindCustomers` y, a continuación, elija el botón **Agregar** .

     El archivo **NorthwindCustomers.svc** aparecerá en el **Editor de código**.

4. En el **Editor de código**, busque el primer comentario `TODO:` y reemplace el código por el texto siguiente:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs" id="Snippet1":::

5. Reemplace los comentarios del controlador de eventos `InitializeService` por el siguiente código:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs" id="Snippet2":::


6. En la barra de menús, elija **depurar**  >  **iniciar sin depurar** para ejecutar el servicio. Se abre una ventana del explorador y se muestra el esquema XML para el servicio.

7. En la barra de **direcciones** , escriba `Customers` al final de la dirección URL de **NorthwindCustomers. SVC** y, a continuación, elija la tecla **entrar** .

     Aparece una representación XML de los datos de la `Customers` tabla.

    > [!NOTE]
    > En algunos casos, Internet Explorer interpretará incorrectamente los datos como una fuente RSS. Debe asegurarse de que la opción para mostrar las fuentes RSS está deshabilitada. Para obtener más información, vea [Solucionar problemas de referencias de servicio](../data-tools/troubleshooting-service-references.md).

8. Cierre la ventana del explorador.

En los pasos siguientes, creará una aplicación cliente Windows Forms para consumir el servicio.

## <a name="creating-the-client-application"></a>Crear la aplicación cliente.
Para crear la aplicación cliente, agregará un segundo proyecto, agregará una referencia del servicio al proyecto, configurará un origen de datos y creará una interfaz de usuario para mostrar los datos del servicio.

En el primer paso, agregará un proyecto de Windows Forms a la solución y lo definirá como proyecto de inicio.

### <a name="to-create-the-client-application"></a>Para crear la aplicación cliente

1. En la barra de menús, elija archivo, **Agregar**  >  **nuevo proyecto**.

2. En el cuadro de diálogo **nuevo proyecto** , expanda el nodo **Visual Basic** o **Visual C#** , elija el nodo **Windows** y, a continuación, elija **Windows Forms aplicación**.

3. En el cuadro de texto **Nombre**, escriba `NorthwindClient` y elija el botón **Aceptar**.

4. En el **Explorador de soluciones**, elija el nodo de proyecto **NorthwindClient**.

5. En la barra de menús, elija **Proyecto**, **Establecer como proyecto de inicio**.

En el paso siguiente, agregará una referencia de servicio a [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] en el proyecto Web.

### <a name="to-add-a-service-reference"></a>Para agregar una referencia de servicio

1. En la barra de menús, elija **proyecto**  >  **Agregar referencia de servicio**.

2. En el cuadro de diálogo **Agregar referencia de servicio**, elija el botón **Detectar**.

     En el campo **Dirección** aparecerá la dirección URL del servicio NorthwindCustomers.

3. Elija el botón **Aceptar** para agregar la referencia del servicio.

En el paso siguiente, configurará un origen de datos para habilitar el enlace de datos al servicio.

### <a name="to-enable-data-binding-to-the-service"></a>Para habilitar el enlace de datos al servicio

1. En la barra de menús, elija **Ver**  >  **otros**  >  **orígenes de datos** de Windows.

   Se abre la ventana **Orígenes de datos**.

2. En la ventana **Orígenes de datos**, elija el botón **Agregar nuevo origen de datos**.

3. En la página **Elija un tipo de origen de datos** del **Asistente para configuración de orígenes de datos**, elija **Objeto** y después elija el botón **Siguiente**.

4. En la página **Seleccionar los objetos de datos**, expanda el nodo **NorthwindClient** y después expanda el nodo **NorthwindClient.ServiceReference1**.

5. Active la casilla **Customer** y elija el botón **Finalizar**.

En el paso siguiente, creará la interfaz de usuario que muestra los datos del servicio.

### <a name="to-create-the-user-interface"></a>Para crear la interfaz de usuario

1. En la ventana **Orígenes de datos**, abra el menú contextual del nodo **Customers** y elija **Copiar**.

2. En el diseñador de formularios de **Form1.vb** o de **Form1.cs**, abra el menú contextual y elija **Pegar**.

    Se agregarán al formulario un control <xref:System.Windows.Forms.DataGridView>, un componente <xref:System.Windows.Forms.BindingSource> y un componente <xref:System.Windows.Forms.BindingNavigator>.

3. Elija el control **CustomersDataGridView** y después en la ventana **Propiedades**, establezca la propiedad **Acoplar** en **Rellenar**.

4. En **Explorador de soluciones**, abra el menú contextual del nodo **Form1** y elija **Ver código** para abrir el editor de código y agregue la siguiente `Imports` `Using` instrucción o en la parte superior del archivo:

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

6. En el **Explorador de soluciones**, abra el menú contextual del archivo **NorthwindCustomers.svc** y elija **Ver en el explorador**. Se abre Internet Explorer y se muestra el esquema XML para el servicio.

7. Copie la dirección URL de la barra de direcciones de Internet Explorer.

8. En el código que agregó en el paso 4, seleccione `http://localhost:53161/NorthwindCustomers.svc/` y reemplácelo por la dirección URL que acaba de copiar.

9. En la barra de menús, elija **depurar**  >  **iniciar depuración** para ejecutar la aplicación. Se muestra la información del cliente.

   Ahora dispone de una aplicación operativa que muestra una lista de clientes del servicio NorthwindCustomers. Si desea exponer datos adicionales a través del servicio, puede modificar el [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] para incluir tablas adicionales de la base de datos Northwind.

En el siguiente paso opcional, aprenderá a filtrar los datos devueltos por el servicio.

## <a name="adding-filtering-capabilities"></a>Agregar funciones de filtrado
En este paso, se personaliza la aplicación para filtrar los datos por la ciudad del cliente.

### <a name="to-add-filtering-by-city"></a>Para agregar el filtrado por ciudad

1. En el **Explorador de soluciones**, abra el menú contextual del nodo **Form1.vb** o **Form1.cs** y elija **Abrir**.

2. Agregue un control <xref:System.Windows.Forms.TextBox> y un control <xref:System.Windows.Forms.Button> desde el **Cuadro de herramientas** al formulario.

3. Abra el menú contextual del <xref:System.Windows.Forms.Button> control, elija **Ver código** y, a continuación, agregue el código siguiente en el `Button1_Click` controlador de eventos:

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

5. En la barra de menús, elija **depurar**  >  **iniciar depuración** para ejecutar la aplicación.

6. En el cuadro de texto, escriba **London** y después elija el botón. Solo se mostrarán los clientes de Londres.

## <a name="see-also"></a>Consulte también

- [Servicios de Windows Communication Foundation y servicios de datos WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Cómo: Adición, actualización o eliminación de una referencia de servicio de datos de WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)
