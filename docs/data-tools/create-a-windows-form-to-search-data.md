---
title: "Tutorial: Crear Windows Forms para buscar datos | Microsoft Docs"
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
  - "datos [Visual Studio], parametrizar consultas"
  - "datos [Visual Studio], buscar"
  - "parámetros, mostrar datos filtrados"
  - "Windows Forms, mostrar datos"
  - "Windows Forms, buscar datos"
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 28
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Crear Windows Forms para buscar datos
Un escenario habitual de la aplicación es mostrar los datos seleccionados en un formulario.  Por ejemplo, puede que desee mostrar los pedidos de un cliente concreto o los detalles de un pedido específico.  En este caso, un usuario escribe información en un formulario y, a continuación, se ejecuta una consulta con la entrada del usuario como parámetro; es decir, los datos se seleccionan basándose en una consulta parametrizada.  La consulta devuelve sólo los datos que satisfacen los criterios escritos por el usuario.  Este tutorial muestra cómo crear una consulta que devuelve los clientes de una ciudad específica y cómo modificar la interfaz de usuario para que los usuarios puedan escribir el nombre de una ciudad y presionar un botón para ejecutar la consulta.  
  
 El uso de consultas parametrizadas ayuda a que la aplicación sea más eficaz, ya que permite a la base de datos realizar el trabajo que mejor sabe hacer: filtrar registros rápidamente.  Al contrario, si solicita una tabla de base de datos completa, transferirla por la red y, a continuación, utilizar la lógica de la aplicación para buscar los registros que se desean, la aplicación puede tornarse más lenta y difícil de utilizar.  
  
 Puede agregar consultas parametrizadas a cualquier TableAdapter \(y controles para aceptar los valores de parámetro y ejecutar la consulta\) utilizando el [Generador de criterios de búsqueda \(cuadro de diálogo\)](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  Abra el cuadro de diálogo seleccionando el comando **Agregar consulta** del menú **Datos** \(o en cualquier etiqueta inteligente del TableAdapter\).  
  
 Las tareas ilustradas en este tutorial incluyen:  
  
-   Crear un nuevo proyecto **Aplicación Windows**.  
  
-   Crear y configurar el origen de datos de la aplicación con el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Establecer el tipo de colocación de los elementos en la [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md).  Para obtener más información, vea [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Crear controles que muestran datos arrastrando elementos desde la ventana **Orígenes de datos** hasta un formulario.  
  
-   Agregar controles para mostrar los datos en el formulario.  
  
-   Finalizar el [Generador de criterios de búsqueda \(cuadro de diálogo\)](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
-   Escribir parámetros en el formulario y ejecutar la consulta parametrizada.  
  
## Requisitos previos  
 Para completar las tareas de este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind.  Para obtener más información, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Crear la aplicación para Windows  
 El primer paso es crear una **Aplicación para Windows**.  La asignación de un nombre al proyecto es opcional en este paso, pero se le asignará un nombre para guardarlo más adelante.  
  
#### Para crear el nuevo proyecto de aplicación para Windows  
  
1.  En el menú **Archivo**, cree un nuevo proyecto.  
  
2.  Asigne al proyecto el nombre `WindowsSearchForm`.  
  
3.  Seleccione **Aplicación para Windows** y haga clic en **Aceptar**.  Para obtener más información, vea [Aplicaciones cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     El proyecto **WindowsSearchForm** se crea y se agrega al **Explorador de soluciones**.  
  
## Crear el origen de datos  
 Este paso crea un origen de datos a partir de una base de datos utilizando el **Asistente para la configuración de orígenes de datos**.  Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión.  Para obtener información sobre la configuración de la base de datos de ejemplo Northwind, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
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
  
## Crear el formulario  
 Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.  
  
#### Para crear controles enlazados en el formulario  
  
1.  Expanda el nodo **Customers** en la ventana **Orígenes de datos**.  
  
2.  Arrastre el nodo **Customers** desde la ventana **Orígenes de datos** hasta el formulario.  
  
     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas \(<xref:System.Windows.Forms.BindingNavigator>\) para navegar por los registros.  En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.  
  
## Agregar parametrización \(funcionalidad de búsqueda\) a la consulta  
 Puede agregar una cláusula WHERE a la consulta original utilizando el [Generador de criterios de búsqueda \(cuadro de diálogo\)](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
#### Para crear una consulta parametrizada y controles para escribir los parámetros  
  
1.  Seleccione el control <xref:System.Windows.Forms.DataGridView> y, a continuación, elija **Agregar consulta** en el menú **Datos**.  
  
2.  Escriba `FillByCity` en el área **Nuevo nombre de consulta** en el [Generador de criterios de búsqueda \(cuadro de diálogo\)](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
3.  Agregue `WHERE City = @City` a la consulta en el área **Texto de la consulta**.  
  
     La consulta debe ser similar a lo siguiente:  
  
     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`  
  
     `FROM Customers`  
  
     `WHERE City = @City`  
  
    > [!NOTE]
    >  Los orígenes de datos de Access y Oledb utilizan el signo de interrogación '?' para denotar los parámetros, por lo que la cláusula WHERE tendría esta apariencia: `WHERE City = ?`.  
  
4.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Generador de criterios de búsqueda**.  
  
     **FillByCityToolStrip** se agrega al formulario.  
  
## Probar la aplicación  
 Al ejecutar la aplicación, se abre el formulario listo para tomar el parámetro como entrada.  
  
#### Para probar la aplicación  
  
1.  Presione F5 para ejecutar la aplicación.  
  
2.  Escriba Londres en el cuadro de texto **Ciudad** y haga clic en **FillByCity**.  
  
     La cuadrícula de datos se rellena con clientes que cumplen con los criterios de la parametrización.  En este ejemplo, la cuadrícula de datos muestra sólo los clientes que tienen un valor de **Londres** en su columna **City**.  
  
## Pasos siguientes  
 Dependiendo de los requisitos de la aplicación, existen varios pasos que se pueden realizar después de crear un formulario parametrizado.  Entre las mejoras que podría realizar se incluyen:  
  
-   Agregar controles que muestran datos relacionados.  Para obtener más información, vea [Cómo: Mostrar datos relacionados en una aplicación de Windows Forms](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
-   Modificar el conjunto de datos agregando o quitando objetos de la base de datos.  Para obtener más información, vea [Cómo: Editar un conjunto de datos](../Topic/How%20to:%20Edit%20a%20Dataset.md).  
  
## Vea también  
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Información general sobre el componente BindingSource](../Topic/BindingSource%20Component%20Overview.md)   
 [Información general sobre el control BindingNavigator](../Topic/BindingNavigator%20Control%20Overview%20\(Windows%20Forms\).md)