---
title: "Enlazar controles de Windows Forms a datos en Visual Studio | Microsoft Docs"
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
  - "datos [Windows Forms], orígenes de datos"
  - "datos [Windows Forms], mostrar"
  - "orígenes de datos, mostrar datos"
  - "mostrar datos en formularios"
  - "mostrar datos, Windows Forms"
  - "formularios, mostrar datos"
  - "Windows Forms, enlace de datos"
  - "Windows Forms, mostrar datos"
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 37
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Enlazar controles de Windows Forms a datos en Visual Studio
Para mostrar datos a los usuarios de la aplicación, puede enlazarlos a Windows Forms.  Puede arrastrar los elementos de la ventana **Orígenes de datos** al Diseñador de Windows Forms en Visual Studio para crear estos controles enlazados a datos.  En este tema se describen algunas de las tareas, herramientas y clases más comunes para crear aplicaciones de Windows Forms enlazadas a datos.  
  
 Para obtener información general sobre el modo de crear controles enlazados a datos en Visual Studio, vea [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  Para obtener más información acerca del enlace de datos en Windows Forms, vea [Enlace de datos en Windows Forms](../Topic/Windows%20Forms%20Data%20Binding.md).  
  
## Presentar datos en un formulario de una aplicación Windows  
 En la siguiente tabla se incluyen las tareas comunes relacionadas con mostrar datos en un formulario de una aplicación Windows.  
  
|Tarea|Más información|  
|-----------|---------------------|  
|Crear controles enlazados a datos.<br /><br /> Enlazar controles existentes a datos.|[Cómo: Enlazar controles de Windows Forms a datos](../data-tools/bind-windows-forms-controls-to-data.md)|  
|Crear controles que muestren los datos relacionados de una relación primaria\-secundaria: cuando el usuario selecciona un registro de datos en un control, otro control muestra los datos relacionados correspondientes al registro seleccionado.|[Cómo: Mostrar datos relacionados en una aplicación de Windows Forms](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)|  
|Crear una *tabla de búsqueda*.  Una tabla de búsqueda muestra información de una tabla basada en el valor de un campo de clave externa de otra tabla.|[Cómo: Crear tablas de búsqueda en aplicaciones de Windows Forms](../data-tools/create-lookup-tables-in-windows-forms-applications.md)|  
|Dar formato a la manera en la que los controles muestran los datos.|[Formatting and Advanced Binding Dialog Box](http://msdn.microsoft.com/es-es/42638120-9e6f-436b-985f-4036664230fd)|  
|Cambiar el comportamiento de la característica de titulación inteligente en la ventana **Orígenes de datos**.|[Cómo: Personalizar el modo en que Visual Studio crea los títulos de controles enlazados a datos](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
|Agregar controles que ejecutan una consulta parametrizada.|[Cómo: Agregar una consulta parametrizada a una aplicación de Windows Forms](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md)|  
|Establecer una columna para utilizar un control de imagen con el fin de mostrar las imágenes de una base de datos.|[Cómo: Enlazar controles a imágenes desde una base de datos](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
|Filtrar u ordenar los datos en un conjunto de datos.|[Cómo: Filtrar y ordenar los datos en una aplicación Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
  
 En los siguientes temas se proporcionan ejemplos sobre enlaces de controles Windows Forms a datos.  
  
 [Tutorial: Mostrar datos en Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)  
 Proporciona detalles paso a paso sobre cómo consultar datos de una base de datos y cómo mostrarlos en un Windows Form.  
  
 [Tutorial: Mostrar datos relacionados en Windows Forms](../data-tools/walkthrough-displaying-related-data-on-a-windows-form.md)  
 Proporciona detalles paso a paso para mostrar los datos de dos tablas relacionadas en un Windows Form.  
  
 [Tutorial: Crear Windows Forms para buscar datos](../data-tools/create-a-windows-form-to-search-data.md)  
 Proporciona detalles paso a paso para crear un Windows Form que lleva a cabo una búsqueda de base de datos según los datos proporcionados por el usuario.  
  
 [Tutorial: Crear una tabla de búsqueda en una aplicación Windows Forms](../Topic/Walkthrough:%20Creating%20a%20Lookup%20Table%20in%20a%20Windows%20Forms%20Application.md)  
 Proporciona detalles paso a paso sobre cómo mostrar datos de una tabla basándose en los datos seleccionados en otra tabla.  
  
 [Tutorial: Pasar datos entre formularios Windows Forms](../data-tools/pass-data-between-forms.md)  
 Proporciona detalles paso a paso sobre cómo pasar valores de un formulario a otro en una aplicación.  
  
 [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)  
 Proporciona instrucciones paso a paso sobre la creación de un control personalizado que se pueda usar en la ventana **Orígenes de datos**.  
  
 [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos complejo](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)  
 Proporciona instrucciones paso a paso sobre la creación de un control personalizado que se pueda usar en la ventana **Orígenes de datos**.  
  
 [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)  
 Proporciona instrucciones paso a paso sobre la creación de un control personalizado que se pueda usar en la ventana **Orígenes de datos**.  
  
## Etiquetas inteligentes de datos  
 En varios controles existen etiquetas inteligentes específicas para trabajar con datos.  Cuando ciertos controles se agregan a un formulario, hay un conjunto de posibles acciones relacionadas con los datos disponible en la etiqueta inteligente.  
  
## Componente BindingSource  
 El componente <xref:System.Windows.Forms.BindingSource> sirve para dos propósitos.  Primero, proporciona una capa de abstracción cuando se enlazan los controles de su formulario a los datos.  Los controles del formulario se enlazan al componente <xref:System.Windows.Forms.BindingSource> \(en lugar de enlazarlos directamente a un origen de datos\).  
  
 Segundo, puede administrar una colección de objetos.  Al agregar un tipo a <xref:System.Windows.Forms.BindingSource>, se crea una lista de ese tipo.  
  
 Para obtener más información acerca del componente <xref:System.Windows.Forms.BindingSource>, vea:  
  
-   [BindingSource \(Componente\)](../Topic/BindingSource%20Component.md)  
  
-   [Información general sobre el componente BindingSource](../Topic/BindingSource%20Component%20Overview.md)  
  
-   [Arquitectura del componente BindingSource](../Topic/BindingSource%20Component%20Architecture.md)  
  
## Control BindingNavigator  
 Este componente proporciona una interfaz de usuario para navegar por los datos mostrados en una aplicación Windows.  Para obtener más información, vea [BindingNavigator \(Control\)](../Topic/BindingNavigator%20Control%20\(Windows%20Forms\).md).  
  
## Control DataGridView  
 El control <xref:System.Windows.Forms.DataGridView> permite mostrar y editar los datos en tablas a partir de numerosos tipos diferentes de orígenes de datos.  Puede enlazar datos a un <xref:System.Windows.Forms.DataGridView> mediante la propiedad <xref:System.Windows.Forms.DataGridView.DataSource%2A>.  Para obtener más información, vea [Información general del control DataGridView](../Topic/DataGridView%20Control%20Overview%20\(Windows%20Forms\).md).  
  
## Vea también  
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Tutorial: Mostrar datos en Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)   
 [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos complejo](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)   
 [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)