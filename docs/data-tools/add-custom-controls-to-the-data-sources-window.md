---
title: "Agregar controles personalizados a la ventana de or&#237;genes de datos | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.howtoaddcustomcontrol"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Ventana de orígenes de datos, agregar controles"
  - "controles [Visual Studio], agregar a la ventana de orígenes de datos"
  - "Clase DefaultBindingPropertyAttribute, usar"
  - "Clase LookupBindingPropertiesAttribute, usar"
  - "Clase ComplexBindingPropertiesAttribute, usar"
  - "Ventana de orígenes de datos, seleccionar controles"
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: 42
caps.handback.revision: 39
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar controles personalizados a la ventana de or&#237;genes de datos
Cuando arrastra un elemento de la ventana **Orígenes de datos** hacia una superficie de diseño para crear un control enlazado a datos, puede seleccionar el tipo de control que crea.  Cada elemento de la ventana tiene una lista desplegable que muestra los controles entre los que puede elegir.  El conjunto de controles asociados con cada elemento se determina por el tipo de datos del elemento.  Si el control que desea crear no aparece en la lista, puede seguir las instrucciones de este tema para agregarlo.  
  
 Para obtener más información sobre cómo seleccionar los controles enlazados a datos para crear para elementos en la ventana **Orígenes de datos**, vea [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, seleccione **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
##  <a name="customizinglist"></a> Personalización de la lista de controles enlazables para un tipo de datos  
 Siga estos pasos para agregar o quitar los controles de la lista de controles disponibles para los elementos de la ventana **Orígenes de datos** que tienen un tipo de datos concreto.  
  
#### Para seleccionar los controles que se van a mostrar para un tipo de datos  
  
1.  Asegúrese de que WPF Designer o el Diseñador de Windows Forms esté abierto.  
  
2.  En la ventana **Orígenes de datos**, haga clic en un elemento que forme parte de un origen de datos que agregó a la ventana y, a continuación, haga clic en el menú desplegable del elemento.  
  
3.  En el menú desplegable, haga clic en **Personalizar**.  Uno de los siguientes cuadros de diálogo se abre:  
  
    -   Si Diseñador de Windows Forms está abierto, la página **Personalización de la IU de datos** del cuadro de diálogo **Opciones** se abre.  
  
    -   Si WPF Designer está abierto, el cuadro de diálogo **Personalizar enlace a controles** se abre.  
  
4.  En el cuadro de diálogo, seleccione un tipo de datos en la lista desplegable **Tipo de datos**.  
  
    -   Para personalizar la lista de controles para una tabla u objeto, seleccione **\[Lista\]**.  
  
    -   Para personalizar la lista de controles para una columna de una tabla o una propiedad de un objeto, seleccione el tipo de datos de la columna o propiedad en el almacén de datos subyacente.  
  
    -   Para personalizar la lista de controles para mostrar objetos de datos que tienen las formas definidas por el usuario, seleccione **\[Otro\]**.  Por ejemplo, si la aplicación tiene un control personalizado que muestra los datos de más de una propiedad de un objeto, seleccione **\[Otro\]**.  
  
5.  En el cuadro **Controles asociados**, seleccione los controles que desee que estén disponible para el tipo de datos seleccionado o borre la selección de los controles que desee quitar de la lista.  
  
    > [!NOTE]
    >  Si el control que desea seleccionar no aparece en el cuadro **Controles asociados**, debe agregarlo a la lista.  Para obtener más información, vea [Agregar controles a la lista de controles asociados para un tipo de datos](#addingcontrols).  
  
6.  Haga clic en **Aceptar**.  
  
7.  En la ventana **Orígenes de datos**, haga clic en un elemento del tipo de datos al que asoció uno o más controles y, a continuación, haga clic en el menú desplegable del elemento.  
  
     Los controles que seleccionó en el cuadro **Controles asociados** aparecen ahora en el menú desplegable del elemento.  
  
##  <a name="addingcontrols"></a> Agregar controles a la lista de controles asociados para un tipo de datos  
 Si desea asociar un control a un tipo de datos pero el control no aparece en el cuadro **Controles asociados**, debe agregarlo a la lista.  El control se debe buscar en la solución actual o en un ensamblado al que se hace referencia, estar disponible en el **Cuadro de herramientas** y tener un atributo que especifique el comportamiento de enlace de datos del control.  
  
#### Para agregar controles a la lista de controles asociados  
  
1.  Agregue el control que desea al **Cuadro de herramientas** haciendo clic con el botón secundario del mouse en el **Cuadro de herramientas** y seleccionando **Elegir elementos**.  
  
     El control debe tener uno de los siguientes atributos.  
  
    |Atributo|Descripción|  
    |--------------|-----------------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implemente este atributo en controles sencillos que muestran una única columna \(o propiedad\) de datos, como un <xref:System.Windows.Forms.TextBox>.|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implemente este atributo en controles que muestren listas \(o tablas\) de datos, como <xref:System.Windows.Forms.DataGridView>.|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implemente este atributo en controles que muestren listas \(o tablas\) de datos, pero que también presenten una única columna o propiedad, como por ejemplo un <xref:System.Windows.Forms.ComboBox>.|  
  
2.  Abra la página **Personalización de la IU de datos** del cuadro de diálogo \(para Windows Forms\) **Opciones** o abra el cuadro de diálogo \(para WPF\) **Personalizar enlace de control**.  Para obtener más información, vea [Personalización de la lista de controles enlazables para un tipo de datos](#customizinglist).  
  
3.  El control que acaba de agregar al **Cuadro de herramientas** debe aparecer en la lista de **Controles asociados**.  
  
    > [!NOTE]
    >  Solo los controles ubicados dentro de la solución actual o en un ensamblado al que se hace referencia \(y que implementa uno de los atributos de enlace a datos de la tabla anterior\) están disponibles para agregarlos a la lista de controles asociados.  Para enlazar datos a un control personalizado que no está disponible en la ventana **Orígenes de datos**, arrastre el control desde el **Cuadro de herramientas** a la superficie de diseño y, a continuación, arrastre el elemento con el que se enlazará desde la ventana **Orígenes de datos** hasta el control.  
  
## Vea también  
 [Tutorial: Mostrar datos en Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)   
 [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos complejo](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)   
 [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)   
 [Customize Control Binding \(Personalizar enlace a controles\) \(Cuadro de diálogo\)](../data-tools/customize-control-binding-dialog-box.md)