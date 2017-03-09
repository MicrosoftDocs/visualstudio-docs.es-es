---
title: "Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos complejo | Microsoft Docs"
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
  - "enlace de datos, complejo"
  - "enlace de datos, controles de usuario"
  - "controles de usuario [Visual Studio], enlace de datos complejo"
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 13
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos complejo
Cuando muestra datos en formularios de las aplicaciones Windows, puede elegir controles existentes en el **Cuadro de herramientas** o crear controles personalizados si la aplicación requiere funcionalidad que no está disponible en los controles estándar.  En este tutorial se muestra cómo crear un control que implementa <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.  Los controles que implementan <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contienen unas propiedades `DataSource` y `DataMember` que se pueden enlazar a datos.  Tales controles son similares a <xref:System.Windows.Forms.DataGridView> o <xref:System.Windows.Forms.ListBox>.  
  
 Para obtener más información sobre la creación de controles, vea [Desarrollar controles de formularios Windows Forms en tiempo de diseño](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
 Al crear controles para el uso en escenarios de enlace de datos, necesita implementar uno de los atributos de enlace a datos siguientes:  
  
|Uso de atributo de enlace de datos|  
|----------------------------------------|  
|Implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute> en controles sencillos, como un <xref:System.Windows.Forms.TextBox>, que muestra una única columna \(o propiedad\) de datos.  Para obtener más información, vea [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implemente el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.DataGridView>, que muestra listas \(o tablas\) de datos.  \(Este proceso se describe en esta página del tutorial.\)|  
|Implemente el <xref:System.ComponentModel.LookupBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.ComboBox>, que muestren listas \(o tablas\) de datos, pero que también necesiten presentar una única columna o propiedad.  Para obtener más información, vea [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 En este tutorial se crea un control complejo que muestra las filas de datos de una tabla.  En este ejemplo se utiliza la tabla `Customers` de la base de datos de ejemplo Northwind.  El control de usuario complejo mostrará la tabla de clientes en una <xref:System.Windows.Forms.DataGridView> del control personalizado.  
  
 Durante este tutorial aprenderá a:  
  
-   Crear una nueva **aplicación para Windows**.  
  
-   Agregue un nuevo **Control de usuario** a su proyecto.  
  
-   Diseñe visualmente el control de usuario.  
  
-   Implemente el atributo `ComplexBindingProperty`.  
  
-   Cree un conjunto de datos con el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Establezca la tabla **Customers** de la [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md) de forma que se use el nuevo control complejo.  
  
-   Agregue el nuevo control arrastrándolo desde la ventana **Orígenes de datos** hasta **Form1**.  
  
## Requisitos previos  
 Para poder completar este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind.  Para obtener más información, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Crear una aplicación para Windows  
 El primer paso es crear una **Aplicación para Windows**.  
  
#### Para crear el nuevo proyecto de Windows  
  
1.  En Visual Studio, en el menú **Archivo** cree un nuevo **Proyecto**.  
  
2.  Asigne el nombre TutorialDeControlComplejo al proyecto.  
  
3.  Seleccione **Aplicación para Windows** y haga clic en **Aceptar**.  Para obtener más información, vea [Aplicaciones cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     El proyecto **TutorialDeControlComplejo** se crea y se agrega al **Explorador de soluciones**.  
  
## Agregar un control de usuario al proyecto  
 Como en este tutorial se crea un control complejo enlazable a datos a partir de un **Control de usuario**, deberá agregar un elemento **Control de usuario** al proyecto.  
  
#### Para agregar un control de usuario al proyecto  
  
1.  En el menú **Proyecto**, elija **Agregar control de usuario**.  
  
2.  Escriba ComplexDataGridView en el área **Nombre** y haga clic en **Agregar**.  
  
     El control **ComplexDataGridView** se agrega al **Explorador de soluciones** y se abre en el diseñador.  
  
## Diseñar el control ComplexDataGridView  
 En este paso se agrega un <xref:System.Windows.Forms.DataGridView> al control de usuario.  
  
#### Para diseñar el control ComplexDataGridView  
  
-   Arrastre un control <xref:System.Windows.Forms.DataGridView> del **Cuadro de herramientas** hasta la superficie de diseño del control del usuario.  
  
## Agregar el atributo de enlace de datos requerido  
 En el caso de los controles complejos que admiten enlaces a datos, puede implementar el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.  
  
#### Para implementar el atributo ComplexBindingProperties  
  
1.  Cambie el control **ComplexDataGridView** a vista de código.  \(En el menú **Ver**, seleccione **Código**\).  
  
2.  Reemplace el código de `ComplexDataGridView` por lo siguiente:  
  
     [!code-cs[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]  
  
3.  En el menú **Compilar**, elija **Compilar solución**.  
  
## Crear un origen de datos de su base de datos  
 En este paso se usa el **Asistente para la configuración de orígenes de datos** para crear un origen de datos basado en la tabla `Customers` de la base de datos de ejemplo Northwind.  Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión.  Para obtener información sobre la configuración de la base de datos de ejemplo Northwind, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
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
  
8.  Seleccione la tabla `Customers` y, a continuación, haga clic en **Finalizar**.  
  
     **NorthwindDataSet** se agrega al proyecto y la tabla `Customers` aparece en la ventana **Orígenes de datos**.  
  
## Establecer la columna Customers para que use el control ComplexDataGridView  
 Dentro de la ventana **Orígenes de datos** puede establecer el control que se va a crear antes de arrastrar elementos a un formulario.  
  
#### Para establecer la columna Customers para enlazarse al control ComplexDataGridView  
  
1.  Abra **Form1** en el diseñador.  
  
2.  Expanda el nodo **Customers** en la ventana **Orígenes de datos**.  
  
3.  Haga clic en la flecha de lista desplegable en la columna **Customers** y elija **Personalizar**.  
  
4.  Seleccione **ComplexDataGridView** de la lista de **Controles asociados** en el cuadro de diálogo **Opciones de personalización de la interfaz de usuario de datos**.  
  
5.  Haga clic en la flecha de lista desplegable en la tabla `Customers` y elija **ComplexDataGridView** de la lista de controles.  
  
## Agregar controles al formulario  
 Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.  
  
#### Para crear controles enlazados en el formulario  
  
-   Arrastre el nodo principal **Customers** desde la ventana **Orígenes de datos** al formulario y compruebe que se usa el control **ComplexDataGridView** para mostrar los datos de la tabla.  
  
## Ejecutar la aplicación  
  
#### Para ejecutar la aplicación  
  
-   Presione F5 para ejecutar la aplicación.  
  
## Pasos siguientes  
 Según cuáles sean los requisitos de la aplicación, hay varios pasos que se pueden realizar después de crear un control que admite el enlace a datos.  Entre los pasos más habituales están los siguientes:  
  
-   Colocar los controles personalizados en una biblioteca de controles para poder reutilizarlos en otras aplicaciones.  
  
-   Crear controles que admitan escenarios de búsqueda.  Para obtener más información, vea [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## Vea también  
 [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Controles de Windows Forms](../Topic/Windows%20Forms%20Controls.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)