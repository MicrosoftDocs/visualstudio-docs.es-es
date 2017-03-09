---
title: "Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos simple | Microsoft Docs"
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
  - "controles personalizados [Visual Studio], Orígenes de datos (ventana)"
  - "Orígenes de datos (ventana), controles"
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos simple
Cuando muestra datos en formularios de las aplicaciones Windows, puede elegir controles existentes en el **Cuadro de herramientas** o crear controles personalizados si la aplicación requiere funcionalidad que no está disponible en los controles estándar.  En este tutorial se muestra cómo crear un control que implementa <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  Los controles que implementan <xref:System.ComponentModel.DefaultBindingPropertyAttribute> pueden contener una propiedad que se puede enlazar a datos.  Tales controles son similares a <xref:System.Windows.Forms.TextBox> o <xref:System.Windows.Forms.CheckBox>.  
  
 Para obtener más información sobre la creación de controles, vea [Desarrollar controles de formularios Windows Forms en tiempo de diseño](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
 Al crear controles para usarlos en escenarios de enlace de datos, es necesario implementar uno de los atributos de enlace de datos siguientes:  
  
|Uso de atributo de enlace de datos|  
|----------------------------------------|  
|Implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute> en controles sencillos, como un <xref:System.Windows.Forms.TextBox>, que muestra una única columna \(o propiedad\) de datos.  \(Este proceso se describe en esta página del tutorial.\)|  
|Implemente el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.DataGridView>, que muestra listas \(o tablas\) de datos.  Para obtener más información, vea [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos complejo](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implemente el <xref:System.ComponentModel.LookupBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.ComboBox>, que muestren listas \(o tablas\) de datos, pero que también necesiten presentar una única columna o propiedad.  Para obtener más información, vea [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 En este tutorial se crea un control simple que muestra los datos de una sola columna en una tabla.  En este ejemplo se usa la columna `Phone` de la tabla `Customers` de la base de datos de ejemplo Northwind.  El control de usuario simple mostrará los números de teléfono del cliente en un formato de número telefónico estándar, usando para ello un <xref:System.Windows.Forms.MaskedTextBox> y estableciendo la máscara en un número de teléfono.  
  
 Durante este tutorial aprenderá a:  
  
-   Crear una nueva **aplicación para Windows**.  
  
-   Agregue un nuevo **Control de usuario** a su proyecto.  
  
-   Diseñe visualmente el control de usuario.  
  
-   Implemente el atributo `DefaultBindingProperty`.  
  
-   Cree un conjunto de datos con el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Establezca la columna **Phone** de la ventana **Orígenes de datos** de forma que se use el nuevo control.  
  
-   Cree un formulario para mostrar los datos en el nuevo control.  
  
## Requisitos previos  
 Para poder completar este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind.  Para obtener más información, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Crear una aplicación para Windows  
 El primer paso es crear una **Aplicación para Windows**.  
  
#### Para crear el nuevo proyecto de Windows  
  
1.  En Visual Studio, en el menú **Archivo** cree un nuevo **Proyecto**.  
  
2.  Asigne el nombre **TutorialDeControlSimple** al proyecto.  
  
3.  Seleccione **Aplicación para Windows** y haga clic en **Aceptar**.  Para obtener más información, vea [Aplicaciones cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     El proyecto **TutorialDeControlSimple** se crea y se agrega al **Explorador de soluciones**.  
  
## Agregar un control de usuario al proyecto  
 En este tutorial se crea un control simple enlazable a datos a partir de un **Control de usuario**, por lo que debe agregar un elemento **Control de usuario** al proyecto **TutorialDeControlSimple**.  
  
#### Para agregar un control de usuario al proyecto  
  
1.  En el menú **Proyecto**, elija **Agregar control de usuario**.  
  
2.  Escriba `PhoneNumberBox` en el área Nombre y haga clic en **Agregar**.  
  
     El control **PhoneNumberBox** se agrega al **Explorador de soluciones** y se abre en el diseñador.  
  
## Diseñar el control PhoneNumberBox  
 Este tutorial se basa en el <xref:System.Windows.Forms.MaskedTextBox> existente y lo amplía para crear el control `PhoneNumberBox`.  
  
#### Para diseñar el control PhoneNumberBox  
  
1.  Arrastre un control <xref:System.Windows.Forms.MaskedTextBox> del **Cuadro de herramientas** hasta la superficie de diseño del control del usuario.  
  
2.  Seleccione la etiqueta inteligente en el <xref:System.Windows.Forms.MaskedTextBox> que acaba de arrastrar y elija **Establecer máscara**.  
  
3.  Seleccione **Número de teléfono** en el cuadro de diálogo **Máscara de entrada** y haga clic en **Aceptar** para establecer la máscara.  
  
## Agregar el atributo de enlace de datos requerido  
 En el caso de los controles simples que admiten enlaces de datos, implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  
  
#### Para implementar el atributo DefaultBindingProperty  
  
1.  Cambie el control `PhoneNumberBox` a la vista de código.  \(En el menú **Ver**, elija **Código**.\)  
  
2.  Reemplace el código de `PhoneNumberBox` por lo siguiente:  
  
     [!code-cs[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]  
  
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
  
## Establecer la columna Phone para que use el control PhoneNumberBox  
 Dentro de la ventana **Orígenes de datos** puede establecer el control que se va a crear antes de arrastrar elementos a un formulario.  
  
#### Para establecer la columna Phone para enlazarse al control PhoneNumberBox  
  
1.  Abra **Form1** en el diseñador.  
  
2.  Expanda el nodo **Customers** en la ventana **Orígenes de datos**.  
  
3.  Haga clic en la flecha de lista desplegable en el nodo **Customers** y elija **Detalles** de la lista de control.  
  
4.  Haga clic en la flecha de lista desplegable en la columna **Phone** y elija **Personalizar**.  
  
5.  Seleccione **PhoneNumberBox** de la lista de **Controles asociados** en el cuadro de diálogo **Opciones de personalización de la interfaz de usuario de datos**.  
  
6.  Haga clic en la flecha de lista desplegable en la columna **Phone** y elija **PhoneNumberBox**.  
  
## Agregar controles al formulario  
 Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.  
  
#### Para crear controles enlazados en el formulario  
  
-   Arrastre el nodo principal **Customers** desde la ventana **Orígenes de datos** al formulario y compruebe que se usa el control `PhoneNumberBox` para mostrar los datos de la columna `Phone`.  
  
     Los controles enlazados a datos con etiquetas descriptivas aparecen en el formulario, junto con una barra de herramientas \(<xref:System.Windows.Forms.BindingNavigator>\) para navegar por los registros.  En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.  
  
## Ejecutar la aplicación  
  
#### Para ejecutar la aplicación  
  
-   Presione F5 para ejecutar la aplicación.  
  
## Pasos siguientes  
 Según cuáles sean los requisitos de la aplicación, hay varios pasos que se pueden realizar después de crear un control que admite el enlace a datos.  Entre los pasos más habituales están los siguientes:  
  
-   Colocar los controles personalizados en una biblioteca de controles para poder reutilizarlos en otras aplicaciones.  
  
-   Crear controles que admitan escenarios de enlace a datos más complejos.  Para obtener más información, vea [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos complejo](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) y [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## Vea también  
 [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general de las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)