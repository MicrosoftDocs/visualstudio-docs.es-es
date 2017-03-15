---
title: "Tutorial: Mostrar datos relacionados en Windows Forms | Microsoft Docs"
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
  - "datos [Visual Studio], mostrar en Windows Forms"
  - "datos [Visual Studio], principal-detalles"
  - "mostrar datos en formularios, tutoriales"
  - "mostrar datos de tablas"
  - "mostrar información de tablas"
  - "mostrar tablas, datos relacionados"
  - "listas principal-detalle, mostrar en Windows Forms"
  - "Windows Forms, mostrar datos"
ms.assetid: fc4b9055-2bf3-4028-8aad-9489820d69f6
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Tutorial: Mostrar datos relacionados en Windows Forms
En muchos escenarios de aplicaciones, es posible que desee trabajar con los datos que provienen de más de una tabla y, con frecuencia, con datos de tablas relacionadas.  Es decir, trabajar con una relación primaria\-secundaria.  Por ejemplo, puede crear un formulario donde, al seleccionar un registro de cliente, se muestren los pedidos de ese cliente.  La visualización de los registros relacionados en el formulario se realiza estableciendo la propiedad <xref:System.Windows.Forms.BindingSource.DataSource%2A> del <xref:System.Windows.Forms.BindingSource> secundario del <xref:System.Windows.Forms.BindingSource> primario \(no la tabla secundaria\) y estableciendo la propiedad <xref:System.Windows.Forms.BindingSource.DataMember%2A> del <xref:System.Windows.Forms.BindingSource> secundario de la relación de datos que enlaza las tablas primaria y secundaria.  
  
 Las tareas ilustradas en este tutorial incluyen:  
  
-   Crear un proyecto de **aplicación para Windows**.  
  
-   Crear y configurar un conjunto de datos en la aplicación basado en las tablas `Customers` y `Orders` y de la base de datos Northwind utilizando el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Agregar controles para mostrar datos de la tabla `Customers`.  
  
-   Agregar controles para mostrar los pedidos \(`Orders`\) basados en el cliente \(`Customer`\) seleccionado.  
  
-   Probar la aplicación seleccionando diferentes clientes y comprobando que se muestran los pedidos correctos del cliente seleccionado.  
  
## Requisitos previos  
 Para completar las tareas de este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind.  Para configurar bases de datos de ejemplo, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Crear el proyecto  
 El primer paso es crear una **Aplicación para Windows**.  
  
#### Para crear el proyecto de aplicación para Windows  
  
1.  En el menú **Archivo**, cree un nuevo proyecto.  
  
2.  Asigne al proyecto el nombre `RelatedDataWalkthrough`.  
  
3.  Seleccione **Aplicación para Windows** y haga clic en **Aceptar**.  Para obtener más información, vea [Aplicaciones cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     El proyecto **RelatedDataWalkthrough** se crea y se agrega al **Explorador de soluciones**.  
  
## Crear el origen de datos  
 Este paso crea un conjunto de datos basado en las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind.  
  
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
  
8.  Seleccione las tablas **Customers** y **Orders** y, a continuación, haga clic en **Finalizar**.  
  
     Se agrega al proyecto **NorthwindDataSet** y la tabla **Customers** aparece en la ventana **Orígenes de datos**.  
  
## Crear controles para mostrar datos de la tabla Customers  
  
#### Para crear los controles que muestren los datos del cliente \(registros primarios\)  
  
1.  En la ventana **Orígenes de datos**, seleccione la tabla **Customers** y, a continuación, haga clic en la flecha de lista desplegable.  
  
2.  Elija **Detalles** en el menú.  
  
3.  Arrastre el nodo principal **Customers** de la ventana **Orígenes de datos** hasta la parte superior de **Form1**.  
  
     Los controles enlazados a datos con etiquetas descriptivas aparecen en el formulario, junto con una barra de herramientas \(<xref:System.Windows.Forms.BindingNavigator>\) para navegar por los registros.  En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.  
  
## Crear controles para mostrar datos de la tabla Orders  
 ![Ventana Orígenes de datos que muestra la relación](../data-tools/media/datasources2.gif "DataSources2")  
  
#### Para crear controles que muestren los pedidos de cada cliente \(registros secundarios\)  
  
-   En la ventana **Orígenes de datos**, expanda el nodo **Customers** y seleccione la última columna de la tabla **Customers**, que es un nodo **Orders** expansible, y arrástrela hasta la parte inferior de **Form1**.  
  
     Se agrega un control <xref:System.Windows.Forms.DataGridView> al formulario y, a la bandeja de componentes, un nuevo componente <xref:System.Windows.Forms.BindingSource> \(`OrdersBindingSource`\) y un TableAdapter \(`OrdersTableAdapter`\).  
  
    > [!NOTE]
    >  Abra la [Ventana Propiedades](../ide/reference/properties-window.md) y seleccione **OrdersBindingSource**.  Inspeccione las propiedades <xref:System.Windows.Forms.BindingSource.DataSource%2A> y <xref:System.Windows.Forms.BindingSource.DataMember%2A> para ver cómo está configurado el enlace para mostrar los registros relacionados.  <xref:System.Windows.Forms.BindingSource.DataSource%2A> se establece en `CustomersBindingSource` \(el <xref:System.Windows.Forms.BindingSource> de la tabla primaria\), en lugar de en la tabla `Orders`.  La propiedad <xref:System.Windows.Forms.BindingSource.DataMember%2A> se establece en `FK_Orders_Customers`, que es el nombre del objeto <xref:System.Data.DataRelation> que relaciona las tablas entre sí.  
  
## Probar la aplicación  
  
#### Para probar la aplicación  
  
1.  Presione F5 para ejecutar la aplicación.  
  
2.  Seleccione distintos clientes mediante el control **CustomersBindingNavigator** para comprobar que se muestran los pedidos correctos en el control <xref:System.Windows.Forms.DataGridView>.  
  
## Pasos siguientes  
 Dependiendo de los requisitos de la aplicación, hay varios pasos que se pueden realizar después de crear un formulario principal\-detalle.  Entre las mejoras que podría realizar a este tutorial se incluye:  
  
-   Filtrar los registros de `Customers` agregando parametrización a la tabla `Customers`.  Para ello, seleccione cualquier control que muestre datos contenidos en la tabla `Customers`, haga clic en la etiqueta inteligente y elige **Agregar consulta**.  Cumplimentar [Generador de criterios de búsqueda \(cuadro de diálogo\)](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  Para obtener más información, vea [Cómo: Agregar una consulta parametrizada a una aplicación de Windows Forms](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md).  
  
## Vea también  
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Cómo: Mostrar datos relacionados en una aplicación de Windows Forms](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)   
 [Información general sobre el componente BindingSource](../Topic/BindingSource%20Component%20Overview.md)   
 [Información general sobre el control BindingNavigator](../Topic/BindingNavigator%20Control%20Overview%20\(Windows%20Forms\).md)