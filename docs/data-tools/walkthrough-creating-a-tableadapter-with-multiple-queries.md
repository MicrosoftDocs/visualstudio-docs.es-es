---
title: "Tutorial: Crear un objeto TableAdapter con varias consultas | Microsoft Docs"
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
  - "datos [Visual Studio], TableAdapters"
  - "datos [Visual Studio], tutoriales"
  - "consultas [Visual Studio], TableAdapters"
  - "consultas TableAdapter, crear"
  - "TableAdapters, crear"
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Tutorial: Crear un objeto TableAdapter con varias consultas
En este tutorial creará un TableAdapter en un conjunto de datos mediante el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).  Este tutorial le guiará por el proceso de creación de una segunda consulta en el [TableAdapter](../data-tools/tableadapter-overview.md) por medio del [Asistente para la configuración de consultas de TableAdapter](../data-tools/editing-tableadapters.md) en el [Diseñador de DataSet](../data-tools/creating-and-editing-typed-datasets.md).  
  
 Las tareas ilustradas en este tutorial incluyen:  
  
-   Crear un nuevo proyecto **Aplicación Windows**.  
  
-   Crear y configurar un origen de datos en la aplicación creando un conjunto de datos con el **Asistente para la configuración de orígenes de datos**.  
  
-   Abrir el nuevo conjunto de datos en el **Diseñador de DataSet**.  
  
-   Agregar consultas al TableAdapter con el **Asistente para la configuración de consultas de TableAdapter**.  
  
## Requisitos previos  
 Para completar las tareas de este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind \(versión de SQL Server o Access\).  Para obtener más información, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Crear una nueva aplicación para Windows  
 El primer paso consiste en crear una aplicación Windows.  
  
#### Para crear un proyecto de aplicación para Windows nuevo  
  
1.  En el menú **Archivo** de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], cree un proyecto.  
  
2.  Elija un lenguaje de programación en el panel **Tipos de proyecto**.  
  
3.  Haga clic en **Aplicación para Windows** en el panel **Plantillas**.  
  
4.  Asigne el nombre `TutorialConsultasTableAdapter` al proyecto y haga clic en **Aceptar**.  
  
     Visual Studio agrega el proyecto al **Explorador de soluciones** y muestra un nuevo formulario en el diseñador.  
  
## Crear un origen de datos de la base de datos con un TableAdapter  
 En este paso se crea un origen de datos utilizando el **Asistente para la configuración de orígenes de datos** basado en la tabla `Customers` de la base de datos de ejemplo Northwind.  Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión.  Para obtener información sobre la configuración de la base de datos de ejemplo Northwind, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
#### Para crear el origen de datos  
  
1.  En el menú **Datos**, haga clic en **Mostrar orígenes de datos**.  
  
2.  En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3.  Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.  
  
4.  En la página **Elegir la conexión de datos** realice una de las siguientes operaciones:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
         O bien  
  
    -   Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.  
  
5.  Si su base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y haga clic en **Siguiente**.  
  
6.  Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.  
  
7.  Expanda el nodo **Tables** en la página **Elija los objetos de base de datos**.  
  
8.  Seleccione la tabla **Customers** y, a continuación, haga clic en **Finalizar**.  
  
     Se agrega al proyecto **NorthwindDataSet** y la tabla **Customers** aparece en la ventana **Orígenes de datos**.  
  
## Abrir el conjunto de datos en el Diseñador de DataSet  
  
#### Para abrir el conjunto de datos en el Diseñador de DataSet  
  
1.  Haga clic con el botón secundario en **NorthwindDataset** en la ventana **Orígenes de datos**.  
  
2.  En el menú contextual, elija **Editar DataSet con el Diseñador**.  
  
     NorthwindDataset se abre en el **Diseñador de DataSet**.  
  
## Agregar una segunda consulta a CustomersTableAdapter  
 El asistente creó el conjunto de datos con una tabla de datos **Customers** y **CustomersTableAdapter**.  En esta sección del tutorial agregaremos una segunda consulta a **CustomersTableAdapter**.  
  
#### Para agregar una segunda consulta a CustomersTableAdapter  
  
1.  Arrastre una **Consulta** desde la pestaña **DataSet** del **Cuadro de herramientas** a la tabla **Customers**.  
  
     Se abrirá el [Asistente para la configuración de consultas de TableAdapter](../data-tools/editing-tableadapters.md).  
  
2.  Seleccione **Usar instrucciones SQL** y, luego, haga clic en **Siguiente**.  
  
3.  Seleccione **SELECT que devuelve filas** y, luego, haga clic en **Siguiente**.  
  
4.  Agregue una cláusula WHERE a la consulta, de forma que se lea:  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  Si está usando la versión de Access de Northwind, reemplace el parámetro @City por un signo de interrogación.  \(`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`\)  
  
5.  En la página **Elija los métodos que se van a generar**, asigne el nombre **FillByCity** al método `Rellenar un DataTable`.  
  
    > [!NOTE]
    >  El método **Devolver un DataTable** no se utiliza en este tutorial, así que puede desactivar la casilla o dejar el nombre predeterminado.  
  
6.  Haga clic en **Siguiente** para finalizar el asistente.  
  
     La consulta **FillByCity** se agrega a **CustomersTableAdapter**.  
  
## Agregar código para ejecutar la consulta adicional en el formulario  
  
#### Para ejecutar la consulta  
  
1.  Seleccione **Form1** en el **Explorador de soluciones** y haga clic en **Diseñador de vistas**.  
  
2.  Arrastre el nodo **Customers** desde la ventana **Orígenes de datos** a **Form1**.  
  
3.  Cambie la vista de código seleccionando **Código** del menú **Ver**.  
  
4.  Reemplace el código del controlador de eventos `Form1_Load` por lo siguiente para ejecutar la consulta `FillByCity`.  
  
     [!code-vb[VbRaddataTableAdapters#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-tableadapter-with-multiple-queries_1.vb)]
     [!code-cs[VbRaddataTableAdapters#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-tableadapter-with-multiple-queries_1.cs)]  
  
## Ejecutar la aplicación  
  
#### Para ejecutar la aplicación  
  
-   Presione F5.  
  
-   La cuadrícula se rellena con los clientes que tengan el valor `Seattle` en `City`.  
  
## Pasos siguientes  
  
### Para agregar funcionalidad a la aplicación  
  
-   Agregue un control <xref:System.Windows.Forms.TextBox> y un control <xref:System.Windows.Forms.Button> y pase el valor del cuadro de texto a la consulta.  \(`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`\).  
  
-   Agregue la lógica de validación al evento <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> de las tablas de datos en el conjunto de datos.  Para obtener más información, vea [Validar los datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md).  
  
## Vea también  
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Cómo: Crear TableAdapters](../data-tools/create-and-configure-tableadapters.md)   
 [Cómo: Crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)