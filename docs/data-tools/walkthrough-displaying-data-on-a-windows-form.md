---
title: "Tutorial: Mostrar datos en Windows Forms | Microsoft Docs"
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
  - "enlace de datos, Windows Forms"
  - "mostrar datos en formularios, tutoriales"
  - "formularios, mostrar datos"
  - "aplicaciones Windows, mostrar datos"
  - "Windows Forms, mostrar datos"
ms.assetid: f6e08c2c-c792-43de-adf3-3e52c0100225
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Tutorial: Mostrar datos en Windows Forms
Uno de los escenarios más habituales en el desarrollo de aplicaciones es mostrar datos en un formulario de una aplicación basada en Windows.  Puede mostrar los datos en un formulario arrastrando elementos desde la [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md) hasta el formulario.  Este tutorial crea un formulario simple que muestra los datos de una tabla única en varios controles individuales.  En este ejemplo se utiliza la tabla `Customers` de la base de datos de ejemplo Northwind.  
  
 Las tareas ilustradas en este tutorial incluyen:  
  
-   Crear un nuevo proyecto **Aplicación Windows**.  
  
-   Crear y configurar un conjunto de datos con el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Seleccionar el control que se va a crear en el formulario al arrastrar elementos desde la ventana **Orígenes de datos**.  Para obtener más información, vea [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Crear un control enlazado a datos arrastrando elementos desde la ventana **Orígenes de datos** hasta su formulario.  
  
## Requisitos previos  
 Para completar las tareas de este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind.  Para obtener más información, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Crear la aplicación para Windows  
 El primer paso es crear un proyecto de tipo **Aplicación para Windows**.  
  
#### Para crear el nuevo proyecto de aplicación para Windows  
  
1.  En el menú **Archivo**, cree un nuevo proyecto.  
  
2.  Asigne al proyecto el nombre `DisplayingDataonaWindowsForm`.  
  
3.  Seleccione **Aplicación para Windows** y haga clic en **Aceptar**.  Para obtener más información, vea [Aplicaciones cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Se crea el proyecto **DisplayingDataonaWindowsForm** y se agrega al **Explorador de soluciones**.  
  
## Crear el origen de datos  
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
  
## Establecer los controles que se van a crear  
 Para este tutorial, los datos se encontrarán en un diseño **Detalles** en el que los datos se muestran en controles individuales.  \(El enfoque alternativo es el del diseño predeterminado, **Cuadrícula**, en el que los datos se muestran en un control <xref:System.Windows.Forms.DataGridView>.\)  
  
#### Para establecer el tipo de acción de colocación de los elementos de la ventana Orígenes de datos  
  
1.  Expanda el nodo **Customers** en la ventana **Orígenes de datos**.  
  
2.  Cambie el tipo de colocación de la tabla **Customers** a **Detalles** seleccionando **Detalles** en la lista desplegable del nodo **Customers**.  Para obtener más información, vea [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Cambie el tipo de colocación de la columna **CustomerID** a una etiqueta seleccionando **Etiqueta** en la lista de controles del nodo **CustomerID**.  
  
## Crear el formulario  
 Cree los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.  
  
#### Para crear controles enlazados en el formulario  
  
-   Arrastre el nodo **Customers** principal desde la ventana **Orígenes de datos** hasta el formulario.  
  
     Los controles enlazados a datos con etiquetas descriptivas aparecen en el formulario, junto con una barra de herramientas \(<xref:System.Windows.Forms.BindingNavigator>\) para navegar por los registros.  En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.  
  
## Probar la aplicación  
  
#### Para ejecutar la aplicación  
  
-   Presione F5.  
  
-   Navegue por los registros utilizando el control <xref:System.Windows.Forms.BindingNavigator>.  
  
## Pasos siguientes  
 Dependiendo de los requisitos de la aplicación, hay varios pasos que pueden realizarse después de crear un Windows Form enlazado a datos.  Entre las mejoras que podría realizar se incluyen:  
  
-   Agregar funcionalidad de búsqueda al formulario.  Para obtener más información, vea [Cómo: Agregar una consulta parametrizada a una aplicación de Windows Forms](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md).  
  
-   Agregar funcionalidad para devolver actualizaciones a la base de datos.  Para obtener más información, vea [Tutorial: Guardar datos en una base de datos \(Tabla única\)](../Topic/Walkthrough:%20Saving%20Data%20to%20a%20Database%20\(Single%20Table\).md).  
  
-   Agregar la tabla `Orders` al conjunto de datos seleccionando **Configurar DataSet con el asistente** desde la ventana **Orígenes de datos**.  A continuación puede agregar controles que muestren los datos relacionados arrastrando el nodo **Orders** \(situado debajo de la columna **Fax** dentro de la tabla **Customers**\) hasta el formulario.  Para obtener más información, vea [Cómo: Mostrar datos relacionados en una aplicación de Windows Forms](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
## Vea también  
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)