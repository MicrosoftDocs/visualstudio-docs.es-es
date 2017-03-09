---
title: "Tutorial: Guardar datos en una base de datos (Varias tablas) | Microsoft Docs"
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
  - "datos [Visual Studio], guardar"
  - "datos [Visual Studio], actualizar"
  - "guardar datos, tutoriales"
  - "actualizar conjuntos de datos, tutoriales"
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 24
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Guardar datos en una base de datos (Varias tablas)
Uno de los escenarios más comunes en el desarrollo de aplicaciones consiste en mostrar los datos en un formulario de una aplicación Windows, editar los datos y devolverlos actualizados a la base de datos.  Este tutorial crea un formulario en el que aparecen datos de dos tablas relacionadas y muestra cómo editar los registros y volver a guardar los cambios en la base de datos.  En este ejemplo se utilizan las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind.  
  
 Puede guardar los datos de su aplicación en la base de datos llamando al método `Update` de un TableAdapter.  Cuando se arrastran elementos desde la ventana **Orígenes de datos**, el código para guardar los datos se agrega automáticamente para la primera tabla colocada en un formulario.  Cualquier tabla adicional agregada a un formulario requiere la adición manual del código necesario para guardar los datos.  Este tutorial muestra cómo agregar código para guardar las actualizaciones de varias tablas.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Las tareas ilustradas en este tutorial incluyen:  
  
-   Crear un nuevo proyecto **Aplicación Windows**.  
  
-   Crear y configurar un origen de datos en la aplicación con el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Establecer los controles de los elementos en la [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md).  Para obtener más información, vea [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Crear controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** hasta el formulario.  
  
-   Modificar un par de registros en cada tabla del conjunto de datos.  
  
-   Modificar el código para devolver los datos actualizados del conjunto de datos a la base de datos.  
  
## Requisitos previos  
 Para poder completar este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind.  Para obtener más información, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Crear la aplicación para Windows  
 El primer paso es crear una **Aplicación para Windows**.  La asignación de un nombre al proyecto es opcional en este paso, pero se le asignará un nombre para guardarlo más adelante.  
  
#### Para crear el nuevo proyecto de aplicación para Windows  
  
1.  En el menú **Archivo**, cree un nuevo proyecto.  
  
2.  Asigne al proyecto el nombre `UpdateMultipleTablesWalkthrough`.  
  
3.  Seleccione **Aplicación para Windows** y haga clic en **Aceptar**.  Para obtener más información, vea [Aplicaciones cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Se crea el proyecto **UpdateMultipleTablesWalkthrough** y se agrega al **Explorador de soluciones**.  
  
## Crear el origen de datos  
 Este paso crea un origen de datos a partir de la base de datos Northwind utilizando el **Asistente para la configuración de orígenes de datos**.  Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión.  Para obtener información sobre la configuración de la base de datos de ejemplo Northwind, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
#### Para crear el origen de datos  
  
1.  En el menú **Datos**, haga clic en **Mostrar orígenes de datos**.  
  
2.  En la ventana **Orígenes de datos**, haga clic en **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3.  Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.  
  
4.  En la página **Elegir la conexión de datos** realice una de las siguientes operaciones:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
         O bien  
  
    -   Seleccione **Nueva conexión** para abrir el cuadro de diálogo **Agregar o modificar conexión**.  
  
5.  Si su base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y haga clic en **Siguiente**.  
  
6.  Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.  
  
7.  Expanda el nodo **Tables** en la página **Elija los objetos de base de datos**.  
  
8.  Seleccione las tablas **Customers** y **Orders** y, a continuación, haga clic en **Finalizar**.  
  
     Se agrega **NorthwindDataSet** al proyecto y las tablas aparecen en la ventana **Orígenes de datos**.  
  
## Establecer los controles que se van a crear  
 Para este tutorial, los datos de la tabla `Customers` estarán en un diseño **Detalles** en el que los datos se muestran en controles individuales.  Los datos de la tabla `Orders` estarán en un diseño **Cuadrícula** mostrado en un control <xref:System.Windows.Forms.DataGridView>.  
  
#### Para establecer el tipo Drop para los elementos en la ventana Orígenes de datos  
  
1.  Expanda el nodo **Customers** en la ventana **Orígenes de datos**.  
  
2.  Cambie el control de la tabla **Customers** a controles individuales seleccionando **Detalles** en la lista de controles del nodo **Customers**.  Para obtener más información, vea [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## Crear el formulario enlazado a datos  
 Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.  
  
#### Para crear controles enlazados en el formulario  
  
1.  Arrastre el nodo **Customers** principal desde la ventana **Orígenes de datos** a **Form1**.  
  
     Los controles enlazados a datos con etiquetas descriptivas aparecen en el formulario, junto con una barra de herramientas \(<xref:System.Windows.Forms.BindingNavigator>\) para navegar por los registros.  En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.  
  
2.  Arrastre el nodo **Orders** relacionado desde la ventana **Orígenes de datos** hasta **Form1**.  
  
    > [!NOTE]
    >  El nodo **Orders** relacionado se encuentra debajo de la columna **Fax** y es un nodo secundario del nodo **Customers**.  
  
     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas \(<xref:System.Windows.Forms.BindingNavigator>\) para navegar por los registros.  En la bandeja de componentes aparece un objeto [OrdersTableAdapter](../data-tools/tableadapter-overview.md) y un objeto <xref:System.Windows.Forms.BindingSource>.  
  
## Agregar código para actualizar la base de datos  
 Puede actualizar la base de datos llamando a los métodos `Update` de los TableAdapters **Customers** y **Orders**.  De manera predeterminada, se agrega un controlador de eventos para el botón **Guardar** de <xref:System.Windows.Forms.BindingNavigator> al código del formulario para enviar las actualizaciones a la base de datos.  Este procedimiento modifica ese código de modo que envíe las actualizaciones en el orden apropiado y se elimine así la posibilidad de que se produzcan errores de integridad referencial.  El código también implementa el control de errores colocando la llamada de actualización en un bloque try\-catch.  Puede modificar el código para satisfacer las necesidades de la aplicación.  
  
> [!NOTE]
>  Para mayor claridad, este tutorial no utiliza una transacción, pero si va a actualizar dos o más tablas relacionadas, debería incluir toda la lógica de actualización dentro de una transacción.  Una transacción es un proceso que asegura que todos los cambios relacionados con una base de datos son correctos antes de confirmar cualquier cambio.  Para obtener más información, vea [Transacciones y simultaneidad](../Topic/Transactions%20and%20Concurrency.md).  
  
#### Para agregar la lógica de actualización a la aplicación  
  
1.  Haga doble clic en el botón **Guardar** de <xref:System.Windows.Forms.BindingNavigator> para abrir el controlador del evento `bindingNavigatorSaveItem_Click` en el Editor de código.  
  
2.  Reemplace el código del controlador de eventos para que llame a los métodos `Update` de los TableAdapters relacionados.  El código siguiente crea en primer lugar tres tablas de datos temporales para la información actualizada de cada <xref:System.Data.DataRowState> \(<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> y <xref:System.Data.DataRowState>\).  A continuación se ejecutan las actualizaciones en el orden apropiado.  El código debe tener este aspecto:  
  
     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-cs[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]  
  
## Probar la aplicación  
  
#### Para probar la aplicación  
  
1.  Presione F5.  
  
2.  Realice algunos cambios en los datos de uno o más registros de cada tabla.  
  
3.  Presione el botón **Guardar**.  
  
4.  Compruebe los valores de la base de datos para verificar que se guardaron los cambios.  
  
## Pasos siguientes  
 Dependiendo de los requisitos de la aplicación, hay varios pasos que puede que desee realizar después de crear un formulario enlazado a datos en su aplicación para Windows.  Entre las mejoras que podría realizar se incluyen:  
  
-   Agregar funcionalidad de búsqueda al formulario.  Para obtener más información, vea [Cómo: Agregar una consulta parametrizada a una aplicación de Windows Forms](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md).  
  
-   Editar el origen de datos para agregar o quitar objetos de base de datos.  Para obtener más información, vea [Cómo: Editar un conjunto de datos](../Topic/How%20to:%20Edit%20a%20Dataset.md).  
  
## Vea también  
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general de las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)