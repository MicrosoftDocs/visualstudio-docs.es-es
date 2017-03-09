---
title: "C&#243;mo: Crear tablas de b&#250;squeda en aplicaciones de Windows Forms | Microsoft Docs"
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
  - "tablas de búsqueda"
  - "tablas de búsqueda, crear"
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Crear tablas de b&#250;squeda en aplicaciones de Windows Forms
Puede crear tablas de búsqueda arrastrando el nodo principal de una tabla primaria \(desde [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md)\) a un control del formulario ya enlazado con la columna de la tabla secundaria relacionada.  
  
 El término *tabla de búsqueda* describe controles enlazados con dos tablas de datos relacionadas.  Estos controles de búsqueda muestran datos de la primera tabla basándose en un valor seleccionado en la segunda tabla.  
  
 Por ejemplo, considérese una tabla de `Orders` en una base de datos de ventas.  Cada registro de la tabla `Orders` incluye un `CustomerID` que indica el cliente que ha realizado el pedido.  El `CustomerID` es una clave externa que señala a un registro del cliente en la tabla `Customers`.  En este escenario expandiría la tabla `Orders` en la ventana **Orígenes de datos** y establecería el nodo principal en **Detalles**, establecería la columna `CustomerID` para usar un elemento <xref:System.Windows.Forms.ComboBox> \(o cualquier otro control que admita el enlace de búsqueda\) y arrastraría el nodo `Orders` al formulario.  A continuación, arrastraría el nodo `Customers` al control enlazado con la columna relacionada, en este caso, <xref:System.Windows.Forms.ComboBox> se enlaza con la columna `CustomerID`.  
  
### Para enlazar con datos un control de búsqueda  
  
1.  Abra la ventana **Orígenes de datos**.  
  
    > [!NOTE]
    >  Las tablas de búsqueda requieren que dos tablas u objetos relacionados estén disponibles en la ventana **Orígenes de datos**.  Para obtener más información, vea [Cómo: Mostrar datos relacionados en una aplicación de Windows Forms](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
2.  Expanda los nodos de la ventana **Orígenes de datos** hasta que pueda ver la tabla primaria y todas sus columnas y la tabla secundaria relacionada y todas sus columnas.  
  
    > [!NOTE]
    >  El nodo de la tabla secundaria es el nodo que aparece como un nodo secundario expandible en la tabla primaria.  
  
3.  Cambie el tipo Drop de la tabla secundaria a **Detalles** seleccionando **Detalles** en la lista de control del nodo de la tabla secundaria.  Para obtener más información, vea [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
4.  Busque el nodo que relaciona las dos tablas \(el nodo `CustomerID` en el ejemplo anterior\) y cambie su tipo Drop a <xref:System.Windows.Forms.ComboBox> seleccionando **ComboBox** en la lista de control.  
  
5.  Arrastre el nodo de tabla secundaria principal de la ventana **Orígenes de datos** a su formulario.  
  
     En el formulario aparecen controles de enlace de datos \(con etiquetas descriptivas\) y una barra de herramientas \(<xref:System.Windows.Forms.BindingNavigator>\).  Aparece un componente [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator> en la bandeja de componentes.  
  
6.  Arrastre ahora el nodo de tabla primario principal de la ventana **Orígenes de datos** directamente al control de búsqueda \(<xref:System.Windows.Forms.ComboBox>\).  
  
     En este momento se establecen los enlaces de búsqueda.  Consulte en la tabla siguiente las propiedades concretas establecidas en el control.  
  
    |Propiedad|Explicación del parámetro|  
    |---------------|-------------------------------|  
    |**DataSource**|Visual Studio establece esta propiedad en el elemento <xref:System.Windows.Forms.BindingSource> creado para la tabla que ha arrastrado al control \(a diferencia del elemento <xref:System.Windows.Forms.BindingSource> creado al mismo tiempo que el control\).<br /><br /> Si necesita realizar un ajuste, establezca esta propiedad en el elemento <xref:System.Windows.Forms.BindingSource> de la tabla con la columna que desea mostrar.|  
    |**DisplayMember**|Visual Studio establece esta propiedad en la primera columna tras la clave principal que tiene un tipo de datos String para la tabla que ha arrastrado al control.<br /><br /> Si necesita realizar un ajuste, establezca esta propiedad en el nombre de columna que desea mostrar.|  
    |**ValueMember**|Visual Studio establece esta propiedad en la primera columna que participa de la clave principal, o la primera columna de la tabla si no se ha definido ninguna clave.<br /><br /> Si necesita realizar un ajuste, establezca esta propiedad en la clave principal de la tabla con la columna que desea mostrar.|  
    |**SelectedValue**|Visual Studio establece esta propiedad en la columna original quitada de la ventana **Orígenes de datos**.<br /><br /> Si necesita realizar un ajuste, establezca esta propiedad en la columna de clave externa en la tabla relacionada.|  
  
## Vea también  
 [Tutorial: Crear una tabla de búsqueda en una aplicación Windows Forms](../Topic/Walkthrough:%20Creating%20a%20Lookup%20Table%20in%20a%20Windows%20Forms%20Application.md)   
 [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)   
 [Cómo: Crear una tabla de búsqueda para un control ComboBox, ListBox o CheckedListBox de Windows Forms](../Topic/How%20to:%20Create%20a%20Lookup%20Table%20for%20a%20Windows%20Forms%20ComboBox,%20ListBox,%20or%20CheckedListBox%20Control.md)   
 [Cómo: Crear una tabla de búsqueda con el componente BindingSource de formularios Windows Forms](../Topic/How%20to:%20Create%20a%20Lookup%20Table%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)   
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)