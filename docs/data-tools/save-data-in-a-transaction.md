---
title: "Tutorial: Guardar datos en una transacci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "datos [Visual Studio], guardar en una transacción"
  - "guardar datos"
  - "System.Transactions (espacio de nombres)"
  - "Transactions (espacio de nombres)"
  - "transacciones, guardar datos"
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Guardar datos en una transacci&#243;n
En este tutorial se muestra cómo guardar datos en una transacción usando el espacio de nombres <xref:System.Transactions>.  En este ejemplo se utilizan las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind.  
  
## Requisitos previos  
 Este tutorial requiere acceso a la base de datos de ejemplo Northwind.  Para obtener información sobre la configuración de la base de datos de ejemplo Northwind, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Crear una aplicación para Windows  
 El primer paso es crear una **Aplicación para Windows**.  
  
#### Para crear el nuevo proyecto de Windows  
  
1.  En Visual Studio, en el menú **Archivo** cree un nuevo **Proyecto**.  
  
2.  Asigne al proyecto el nombre SavingDataInATransactionWalkthrough.  
  
3.  Seleccione **Aplicación para Windows** y haga clic en **Aceptar**.  Para obtener más información, vea [Aplicaciones cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Se crea el proyecto **SavingDataInATransactionWalkthrough** y se agrega al **Explorador de soluciones**.  
  
## Crear un origen de datos de base de datos  
 En este paso se usa el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png) para crear un origen de datos basado en las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind.  
  
#### Para crear el origen de datos  
  
1.  En el menú **Datos**, haga clic en **Mostrar orígenes de datos**.  
  
2.  En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3.  Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.  
  
4.  En la página **Elegir la conexión de datos** realice una de las siguientes operaciones:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
         O bien  
  
    -   Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión** y cree una conexión con la base de datos Northwind.  
  
5.  Si su base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y haga clic en **Siguiente**.  
  
6.  Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.  
  
7.  Expanda el nodo **Tables** en la página **Elija los objetos de base de datos**.  
  
8.  Seleccione las tablas `Customers` y `Orders` y, a continuación, haga clic en **Finalizar**.  
  
     **NorthwindDataSet** se agrega al proyecto y las tablas `Customers` y `Orders` aparecen en la ventana **Orígenes de datos**.  
  
## Agregar controles al formulario  
 Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.  
  
#### Para crear controles enlazados a datos en el formulario de Windows Forms  
  
-   Expanda el nodo **Customers** en la ventana **Orígenes de datos**.  
  
-   Arrastre el nodo **Customers** principal desde la ventana **Orígenes de datos** a **Form1**.  
  
     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas \(<xref:System.Windows.Forms.BindingNavigator>\) para navegar por los registros.  En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.  
  
-   Arrastre el nodo **Orders** relacionado \(el nodo de tabla secundaria relacionado situado debajo de la columna **Fax**, no el nodo **Orders** principal\) en el formulario debajo de **CustomersDataGridView**.  
  
     En el formulario aparece una <xref:System.Windows.Forms.DataGridView>.  En la bandeja de componentes aparece un objeto [OrdersTableAdapter](../data-tools/tableadapter-overview.md) y un objeto <xref:System.Windows.Forms.BindingSource>.  
  
## Agregar una referencia al ensamblado System.Transactions  
 Las transacciones usan el espacio de nombres <xref:System.Transactions>.  De forma predeterminada, no se agrega una referencia de proyecto al ensamblado system.transactions, por lo que tiene que agregarla manualmente.  
  
#### Para agregar una referencia al archivo DLL System.Transactions  
  
1.  En el menú **Proyecto**, elija **Agregar referencia**.  
  
2.  Seleccione **System.Transactions** \(en la pestaña **.NET**\) y haga clic en **Aceptar**.  
  
     Se agrega una referencia a **System.Transactions** al proyecto.  
  
## Modificar el código del botón SaveItem de BindingNavigator  
 De forma predeterminada, para la primera tabla que se coloca en el formulario, se agrega código al evento `click` del botón de guardado en <xref:System.Windows.Forms.BindingNavigator>.  Para actualizar otras tablas, debe agregar el código manualmente.  Para este tutorial, refactorizamos el código de guardado existente a partir del controlador del evento de clic del botón de guardado, y creamos algunos métodos más para proporcionar funcionalidad de actualización específica según si la fila se debe agregar o eliminar.  
  
#### Para modificar el código de guardado generado automáticamente  
  
1.  Haga doble clic en el botón **Guardar** en **CustomersBindingNavigator** \(el botón con el icono de disquete\).  
  
2.  Reemplace el método `CustomersBindingNavigatorSaveItem_Click` con el código siguiente:  
  
     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]  
  
 El orden para conciliar los cambios a los datos relacionados es el siguiente:  
  
-   Eliminar los registros secundarios \(en este caso, eliminar los registros de la tabla `Orders`\)  
  
-   Eliminar los registros primarios \(en este caso, eliminar los registros de la tabla `Customers`\)  
  
-   Insertar registros primarios \(en este caso, insertar registros en la tabla `Customers`\)  
  
-   Insertar registros secundarios \(en este caso, insertar registros en la tabla `Orders`\)  
  
#### Para eliminar pedidos existentes  
  
-   Agregue el método siguiente `DeleteOrders` a **Form1**:  
  
     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-cs[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]  
  
#### Para eliminar clientes existentes  
  
-   Agregue el método siguiente `DeleteCustomers` a **Form1**:  
  
     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-cs[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]  
  
#### Para agregar nuevos clientes  
  
-   Agregue el método siguiente `AddNewCustomers` a **Form1**:  
  
     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-cs[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]  
  
#### Para agregar nuevos pedidos  
  
-   Agregue el método siguiente `AddNewOrders` a **Form1**:  
  
     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-cs[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]  
  
## Ejecutar la aplicación  
  
#### Para ejecutar la aplicación  
  
-   Presione F5 para ejecutar la aplicación.  
  
## Vea también  
 [Transacciones y simultaneidad](../Topic/Transactions%20and%20Concurrency.md)   
 [Transacciones distribuidas de Oracle](../Topic/Oracle%20Distributed%20Transactions.md)   
 [Cómo: Guardar datos utilizando una transacción](../data-tools/save-data-by-using-a-transaction.md)   
 [Integración de System.Transactions con SQL Server](../Topic/System.Transactions%20Integration%20with%20SQL%20Server.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)