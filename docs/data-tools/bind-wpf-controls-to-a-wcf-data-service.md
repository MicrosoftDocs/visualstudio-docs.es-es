---
title: Enlazar controles de WPF a un servicio de datos de WCF
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: eb6b9a9a213932662a548314bcc39c75e9d35bc3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55909692"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Enlazar controles de WPF a un servicio de datos de WCF

En este tutorial, se creará una aplicación de WPF que contiene controles enlazados a datos. Los controles se enlazan a registros de cliente que se encapsulan en un servicio de datos de WCF. También agregará botones que los clientes pueden usar para ver y actualizar los registros.

En este tutorial se muestran las tareas siguientes:

- Crear un Entity Data Model que se genera a partir de los datos de la base de datos de ejemplo AdventureWorksLT.

- Crear un servicio de datos de WCF que expone los datos en el Entity Data Model a una aplicación WPF.

- Crear un conjunto de controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** hasta WPF Designer.

- Crear botones que naveguen hacia adelante y hacia atrás por los registros de clientes.

- Creación de un botón que guarde los cambios a los datos de los controles para el servicio de datos de WCF y el origen de datos subyacente.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Requisitos previos

Necesita los componentes siguientes para completar este tutorial:

- Programa para la mejora

- Acceder a una instancia en ejecución de SQL Server o SQL Server Express que tenga asociada la base de datos de ejemplo AdventureWorksLT. Puede descargar la base de datos AdventureWorksLT el [sitio Web de CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).

El conocimiento previo de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial:

- Data Services de WCF. Para obtener más información, consulte [Introducción](/dotnet/framework/data/wcf/wcf-data-services-overview).

- Modelos de datos en [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].

- Entity Data Model y ADO.NET Entity Framework. Para obtener más información, consulte [información general de Entity Framework](/dotnet/framework/data/adonet/ef/overview).

- Enlace a datos de WPF. Para obtener más información, vea [Información general sobre el enlace de datos](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-service-project"></a>Crear el proyecto de servicio

Iniciar este tutorial creando un proyecto para un servicio de datos de WCF:

1. Inicie Visual Studio.

2. En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.

3. Expanda **Visual Basic** o **Visual C#** y después seleccione **Web**.

4. Seleccione la plantilla de proyecto **Aplicación web ASP.NET**.

5. En el cuadro **Nombre**, escriba **AdventureWorksService** y haga clic en **Aceptar**.

     Visual Studio crea el proyecto **AdventureWorksService**.

6. En el **Explorador de soluciones**, haga clic con el botón derecho en **Default.aspx** y seleccione **Eliminar**. Este archivo no es necesario en este tutorial.

## <a name="create-an-entity-data-model-for-the-service"></a>Crear un Entity Data Model para el servicio

Para exponer datos a una aplicación mediante el uso de un servicio de datos de WCF, debe definir un modelo de datos para el servicio. El servicio de datos de WCF admite dos tipos de modelos de datos: Entity Data Model y modelos de datos personalizados que se definen mediante objetos de common language runtime (CLR) que implementan la <xref:System.Linq.IQueryable%601> interfaz. En este tutorial, se crea un Entity Data Model para el modelo de datos.

1. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

2. En la lista Plantillas instaladas, haga clic en **Datos** y seleccione el elemento de proyecto **ADO.NET Entity Data Model**.

3. Cambie el nombre a `AdventureWorksModel.edmx`y haga clic en **agregar**.

     Se abre el **Asistente para Entity Data Model**.

4. En la página **Elegir contenido del modelo**, haga clic en **Generar desde la base de datos** y después en **Siguiente**.

5. En la página **Elegir la conexión de datos**, seleccione una de estas opciones:

    - Si una conexión de datos a la base de datos de ejemplo AdventureWorksLT está disponible en la lista desplegable, selecciónela.

    - Haga clic en **Nueva conexión** y cree una conexión a la base de datos AdventureWorksLT.

6. En la página **Elegir la conexión de datos** asegúrese de que la opción **Guardar configuración de conexión de la entidad en App.Config como** está seleccionada y haga clic en **Siguiente**.

7. En la página **Elija los objetos de base de datos**, expanda el nodo **Tablas** y seleccione la tabla **SalesOrderHeader**.

8. Haga clic en **Finalizar**.

## <a name="create-the-service"></a>Crear el servicio

Crear un servicio de datos de WCF para exponer los datos de Entity Data Model a una aplicación WPF:

1. En el menú **Proyecto**, seleccione **Agregar nuevo elemento**.

2. En la lista **Plantillas instaladas**, haga clic en **Web** y seleccione el elemento de proyecto **Servicio de datos de WCF**.

3. En el **nombre** , escriba `AdventureWorksService.svc`y haga clic en **agregar**.

     Visual Studio agrega el `AdventureWorksService.svc` al proyecto.

## <a name="configure-the-service"></a>Configure el servicio

Debe configurar el servicio para trabajar con el Entity Data Model que ha creado:

1. En el `AdventureWorks.svc` archivo de código, reemplace el **AdventureWorksService** declaración con el siguiente código de la clase.

     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]

     Este código actualiza el **AdventureWorksService** clase, por lo que se derive de una <xref:System.Data.Services.DataService%601> que opera el `AdventureWorksLTEntities` objeto de clase de contexto en el Entity Data Model. También actualiza el método `InitializeService` para que los clientes del servicio tengan acceso completo de lectura y escritura a la entidad `SalesOrderHeader`.

2. Compile el proyecto y compruebe que se compila sin errores.

## <a name="create-the-wpf-client-application"></a>Crear la aplicación cliente WPF

Para mostrar los datos desde el servicio de datos de WCF, cree una nueva aplicación WPF con un origen de datos que se basa en el servicio. Más adelante en este procedimiento, agregará controles enlazados a datos a la aplicación.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo de la solución, haga clic en **Agregar** y seleccione **Nuevo proyecto**.

2. En el cuadro de diálogo **Nuevo proyecto**, expanda **Visual Basic** o **Visual C#** y después expanda **Windows**.

3. Seleccione la plantilla de proyecto **Aplicación WPF**.

4. En el cuadro **Nombre**, escriba `AdventureWorksSalesEditor` y haga clic en **Aceptar**.

   Visual Studio agrega el `AdventureWorksSalesEditor` proyecto a la solución.

5. En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.

   Se abre la ventana **Orígenes de datos**.

6. En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.

   Se abrirá el **Asistente para configuración de orígenes de datos**.

7. En la página **Elija un tipo de origen de datos** del asistente, seleccione **Servicio** y haga clic en **Siguiente**.

8. En el cuadro de diálogo **Agregar referencia de servicio**, haga clic en **Detectar**.

   Visual Studio busca en la solución actual para los servicios disponibles y agrega `AdventureWorksService.svc` a la lista de servicios disponibles en el **servicios** cuadro.

9. En el cuadro **Espacio de nombres**, escriba **AdventureWorksService**.

10. En el cuadro **Servicios**, haga clic en **AdventureWorksService.svc** y haga clic en **Aceptar**.

    Visual Studio descarga la información del servicio y después vuelve al **Asistente para configuración de orígenes de datos**.

11. En la página **Agregar referencia de servicio**, haga clic en **Finalizar**.

    Visual Studio agrega los nodos que representan los datos devueltos por el servicio a la ventana **Orígenes de datos**.

## <a name="define-the-user-interface"></a>Definir la interfaz de usuario

Agregue varios botones a la ventana modificando el código XAML en WPF Designer. Más adelante en este tutorial, agregará código que permite a los usuarios ver y actualizar los registros de ventas usando estos botones.

1. En el **Explorador de soluciones**, haga doble clic en **MainWindow.xaml**.

   La ventana se abre en WPF Designer.

2. En la vista [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] del diseñador, agregue el código siguiente entre las etiquetas `<Grid>`:

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="525" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Compile el proyecto.

## <a name="create-the-data-bound-controls"></a>Crear los controles enlazados a datos

Crear controles que muestren registros de clientes, arrastrando el `SalesOrderHeaders` nodo desde el **orígenes de datos** ventana al diseñador.

1. En la ventana **Orígenes de datos**, haga clic en el menú desplegable del nodo **SalesOrderHeaders** y seleccione **Detalles**.

2. Expanda el nodo **SalesOrderHeaders**.

3. En este ejemplo no se mostrarán algunos campos; por lo tanto, haga clic en el menú desplegable junto a los siguientes nodos y seleccione **Ninguno**:

    - **CreditCardApprovalCode**

    - **ModifiedDate**

    - **OnlineOrderFlag**

    - **RevisionNumber**

    - **rowguid**

    Esta acción impide que Visual Studio cree controles enlazados a datos para estos nodos en el paso siguiente. En este tutorial, se supone que el usuario final no necesita ver estos datos.

4. Desde la ventana **Orígenes de datos**, arrastre el nodo **SalesOrderHeaders** a la fila de la cuadrícula situada debajo de la fila que contiene los botones.

     Visual Studio genera el código XAML que crea un conjunto de controles que están enlazados a los datos de la tabla **Producto**. Para obtener más información sobre el XAML y el código generado, vea [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

5. En el diseñador, haga clic en el cuadro de texto junto a la etiqueta **Customer ID**.

6. En la ventana **Propiedades**, active la casilla junto a la propiedad **IsReadOnly**.

7. Establezca la propiedad **IsReadOnly** de cada uno de los cuadros de texto siguientes:

    - **Número de pedido de compra**

    - **Id. del pedido de ventas**

    - **Número de pedido de venta**

## <a name="load-the-data-from-the-service"></a>Cargar los datos del servicio

Utilice el objeto de proxy de servicio para cargar los datos de ventas desde el servicio. A continuación, asigne los datos devueltos al origen de datos para el <xref:System.Windows.Data.CollectionViewSource> en la ventana de WPF.

1. En el diseñador, para crear el `Window_Loaded` controlador de eventos, haga doble clic en el texto que dice: **MainWindow**.

2. Reemplace el controlador de evento con el código siguiente: Asegúrese de reemplazar la dirección *localhost* en este código por la dirección del host local de su equipo de desarrollo.

     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]

## <a name="navigate-sales-records"></a>Navegar por los registros de ventas

Agregue código que permita a los usuarios desplazarse por los registros de ventas usando los botones **\<** y **>**.

1. En el diseñador, haga doble clic en el botón **<** en la superficie de la ventana.

     Visual Studio abre el archivo de código subyacente y crea un nuevo controlador de evento `backButton_Click` para el evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Agregue el código siguiente al controlador de evento `backButton_Click` generado:

     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]

3. Vuelva al diseñador y haga doble clic en el botón **>**.

     Visual Studio abre el archivo de código subyacente y crea un nuevo controlador de evento `nextButton_Click` para el evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

4. Agregue el código siguiente al controlador de evento `nextButton_Click` generado:

     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]

## <a name="save-changes-to-sales-records"></a>Guardar los cambios en los registros de ventas

Agregue código que permita a los usuarios ver y guardar cambios en los registros de ventas usando el botón **Guardar cambios**:

1. En el diseñador, haga doble clic en el botón **Guardar cambios**.

     Visual Studio abre el archivo de código subyacente y crea un nuevo controlador de evento `saveButton_Click` para el evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Agregue el código siguiente al controlador de eventos `saveButton_Click`.

     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]

## <a name="test-the-application"></a>Probar la aplicación

Compile y ejecute la aplicación para comprobar que puede ver y actualizar los registros de clientes:

1. En **compilar** menú, haga clic en **compilar solución**. Compruebe que la solución se compila sin errores.

2. Presione **Ctrl**+**F5**.

     Visual Studio inicia el proyecto **AdventureWorksService** sin depurarlo.

3. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto **AdventureWorksSalesEditor**.

4. En el menú contextual (menú contextual), en **depurar**, haga clic en **Iniciar nueva instancia**.

     La aplicación se ejecuta. Compruebe lo siguiente:

    - Los cuadros de texto muestran campos de datos diferentes de los del primer registro de ventas, que tiene el identificador de pedido de ventas **71774**.

    - Puede hacer clic en los botones **>** o **<** para navegar por otros registros de ventas.

5. En uno de los registros de ventas, escriba algún texto en el cuadro **Comentario** y haga clic en **Guardar cambios**.

6. Cierre la aplicación y vuelva a iniciarla en Visual Studio.

7. Vaya al registro de ventas que ha cambiado y compruebe que el cambio se conserva después de cerrar y volver a abrir la aplicación.

8. Cierre la aplicación.

## <a name="next-steps"></a>Pasos siguientes

Una vez completado este tutorial, puede realizar las siguientes tareas relacionadas:

- Aprenda cómo usar la ventana **Orígenes de datos** en Visual Studio para enlazar controles WPF a otros tipos de orígenes de datos. Para obtener más información, consulte [WPF enlazar controles a un conjunto de datos](../data-tools/bind-wpf-controls-to-a-dataset.md).

- Aprenda cómo usar la ventana **Orígenes de datos** en Visual Studio para mostrar datos relacionados (es decir, datos en una relación primario-secundario) en controles WPF. Para obtener más información, consulte [Tutorial: mostrar datos relacionados en una aplicación WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Vea también

- [Enlace de controles de WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Enlazar controles de WPF a un conjunto de datos](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [Información general de WCF (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Introducción a Entity Framework (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Información general (.NET Framework) de enlace de datos](/dotnet/framework/wpf/data/data-binding-overview)