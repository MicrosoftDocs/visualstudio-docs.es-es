---
title: "C&#243;mo: Enlazar controles de Windows Forms a datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "datos [Windows Forms], mostrar"
  - "orígenes de datos, mostrar"
  - "mostrar datos, controles de Windows Forms"
  - "Windows Forms, mostrar datos"
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 28
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Enlazar controles de Windows Forms a datos
Enlace datos a controles Windows Forms arrastrando los objetos de [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md).  Antes de arrastrar los elementos de la ventana **Orígenes de datos**, puede establecer el tipo de control de la tabla en **Detalles** para los controles individuales o **DataGridView** para <xref:System.Windows.Forms.DataGridView>.  Para obtener más información, vea [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
 Si los controles necesarios para la aplicación no están disponibles en la ventana de **Orígenes de datos** , puede agregar controles.  Para obtener más información, vea [Agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Mostrar una tabla de datos completa en controles individuales  
 Se puede mostrar una tabla de datos completa en controles individuales si se arrastra la tabla \(o un nodo que representa una colección si se utiliza un origen de datos de objeto\) desde la ventana **Orígenes de datos** a un formulario en una aplicación para Windows.  
  
#### Para mostrar una tabla de datos completa  
  
1.  Abra la ventana **Orígenes de datos**.  Para obtener más información, vea [Cómo: Abrir la ventana Orígenes de datos](../data-tools/how-to-open-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Si la ventana **Orígenes de datos** está vacía, agréguele un origen de datos.  Para obtener más información, vea [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md).  
  
2.  Abra el formulario en el **Diseñador de Windows Forms**.  
  
3.  Seleccione una tabla en la ventana **Orígenes de datos**, haga clic en la flecha de lista desplegable y seleccione **Detalles**.  
  
4.  Arrastre la tabla desde la ventana **Orígenes de datos** a un formulario.  
  
     En el formulario se crea un control enlazado a datos individual para cada columna o propiedad, acompañado de un control adecuadamente titulado Etiqueta.  
  
## Mostrar columnas de datos seleccionadas en controles individuales  
 Es posible mostrar columnas de datos individuales en controles individuales si se arrastran columnas individuales \(o propiedades si se utiliza un origen de datos de objeto\) desde la ventana **Orígenes de datos** a un formulario en una aplicación para Windows.  
  
#### Para mostrar columnas seleccionadas de datos  
  
1.  Abra la ventana **Orígenes de datos**.  Para obtener más información, vea [Cómo: Abrir la ventana Orígenes de datos](../data-tools/how-to-open-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Si la ventana **Orígenes de datos** está vacía, agréguele un origen de datos.  Para obtener más información, vea [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md).  
  
2.  Expanda la tabla para mostrar las columnas individuales.  
  
    > [!TIP]
    >  Para establecer el control que se crea para cada columna, seleccione la columna en la ventana **Orígenes de datos**, haga clic en la flecha de lista desplegable y seleccione un control de la lista de controles disponibles.  Para obtener más información, vea [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Abra el formulario en el **Diseñador de Windows Forms**.  
  
4.  Arrastre las columnas deseadas desde la ventana **Orígenes de datos** a un formulario.  
  
     Por cada columna o propiedad que arrastre, se crea un control enlazado a datos individual en el formulario, junto con el control de etiqueta con título correspondiente.  
  
 También puede arrastrar los elementos de la ventana **Orígenes de datos** a los controles existentes \(controles que ya están en un formulario\) para enlazar el control a los datos.  Un control que ya esté enlazado a datos restablece sus enlaces a datos al elemento que se haya arrastrado sobre él en último término.  
  
> [!NOTE]
>  Para ser destinos válidos de la acción de colocación, los controles deben poder mostrar el tipo de datos subyacente del elemento arrastrado desde la ventana **Orígenes de datos**.  Por ejemplo, no es válido arrastrar un elemento que tenga un tipo de datos de <xref:System.DateTime> hasta un control <xref:System.Windows.Forms.CheckBox>, porque el control <xref:System.Windows.Forms.CheckBox> no puede mostrar fechas.  
  
#### Para enlazar un control existente a datos  
  
1.  Abra la ventana **Orígenes de datos**.  Para obtener más información, vea [Cómo: Abrir la ventana Orígenes de datos](../data-tools/how-to-open-the-data-sources-window.md).  
  
2.  Abra el formulario en [Windows Forms Designer](http://msdn.microsoft.com/es-es/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
3.  Expanda una tabla u objeto en la ventana **Orígenes de datos** para mostrar sus columnas o propiedades individuales.  
  
4.  Arrastre el elemento deseado desde la ventana **Orígenes de datos** a un control existente.  
  
     Ahora el control está enlazado al elemento seleccionado.  
  
## Mostrar datos en un control DataGridView  
  
#### Para mostrar los datos en un nuevo control DataGridView de formulario Windows Forms  
  
1.  Abra la ventana **Orígenes de datos**.  Para obtener más información, vea [Cómo: Abrir la ventana Orígenes de datos](../data-tools/how-to-open-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Si la ventana **Orígenes de datos** está vacía, agréguele un origen de datos.  Para obtener más información, vea [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md).  
  
2.  Abra el formulario en el **Diseñador de Windows Forms**.  
  
3.  Seleccione una tabla en la ventana **Orígenes de datos**, haga clic en la flecha de lista desplegable y seleccione **DataGridView**.  
  
4.  Arrastre la tabla de la ventana **Orígenes de datos** a un formulario.  
  
     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas \(<xref:System.Windows.Forms.BindingNavigator>\) para navegar por los registros.  Aparece un componente [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator> en la bandeja de componentes.  
  
#### Para mostrar los datos en un control DataGridView de formularios Windows Forms existente  
  
1.  Abra la ventana **Orígenes de datos**.  Para obtener más información, vea [Cómo: Abrir la ventana Orígenes de datos](../data-tools/how-to-open-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Si la ventana **Orígenes de datos** está vacía, agréguele un origen de datos.  Para obtener más información, vea [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md).  
  
2.  Abra el formulario en el **Diseñador de Windows Forms**.  
  
3.  Seleccione una tabla en la ventana **Orígenes de datos**, haga clic en la flecha de lista desplegable y seleccione **DataGridView**.  
  
4.  Arrastre la tabla de la ventana **Orígenes de datos** a <xref:System.Windows.Forms.DataGridView> en el formulario.  
  
     El control <xref:System.Windows.Forms.DataGridView> se enlaza ahora a la tabla que ha arrastrado hasta él.  Aparece un componente [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/tableadapter-overview.md) y <xref:System.Windows.Forms.BindingSource> en la bandeja de componentes.  
  
## Vea también  
 [Tutorial: Mostrar datos en Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)   
 [Información general sobre el componente BindingSource](../Topic/BindingSource%20Component%20Overview.md)   
 [Información general sobre el control BindingNavigator](../Topic/BindingNavigator%20Control%20Overview%20\(Windows%20Forms\).md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)   
 [Herramientas para trabajar con orígenes de datos en Visual Studio](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)