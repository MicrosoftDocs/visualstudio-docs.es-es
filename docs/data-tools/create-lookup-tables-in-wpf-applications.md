---
title: "C&#243;mo: Crear tablas de b&#250;squeda en aplicaciones WPF | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "datos [WPF], mostrar"
  - "enlace de datos, WPF"
  - "mostrar datos, WPF"
  - "WPF [WPF], datos"
  - "enlace de datos de WPF [Visual Studio]"
  - "WPF Designer, enlace de datos"
  - "WPF, enlace de datos en Visual Studio"
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Crear tablas de b&#250;squeda en aplicaciones WPF
Para crear una tabla de búsqueda, puede arrastrar el nodo principal de una tabla u objeto primario de la ventana **Orígenes de datos** hasta un control que ya esté enlazado a una columna o propiedad de una tabla secundaria relacionada.  El término *tabla de búsqueda* \(que también se conoce como *enlace de búsqueda*\) describe un control que muestra información de una tabla de datos según el valor de un campo de clave externa de otra tabla.  
  
 Por ejemplo, considérese una tabla de `Orders` en una base de datos de ventas.  Cada registro de la tabla `Orders` incluye un `CustomerID` que indica el cliente que ha realizado el pedido.  `CustomerID` es una clave externa que señala a un registro del cliente en la tabla `Customers`.  Al presentar una lista de pedidos de la tabla `Orders`, se puede mostrar el nombre real del cliente en lugar del `CustomerID`.  Dado que el nombre del cliente está en la tabla `Customers`, necesita crear una tabla de búsqueda para mostrar el nombre del cliente.  La tabla de búsqueda usa el valor `CustomerID` del registro `Orders` para navegar por la relación y devolver el nombre descriptivo del cliente.  
  
### Para crear una tabla de búsqueda  
  
1.  Agregue al proyecto uno de los siguientes tipos de orígenes de datos con datos relacionados:  
  
    -   Conjunto de datos o Entity Data Model.  Para obtener más información, vea [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
    -   Servicio de datos de WCF, servicio WCF o servicio Web.  Para obtener más información, vea [Cómo: Conectarse a los datos en un servicio](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
    -   Objetos.  Para obtener más información, vea [Cómo: Conectarse a los datos en objetos](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md).  
  
    > [!NOTE]
    >  Para poder crear una tabla de búsqueda, el proyecto debe tener dos tablas u objetos relacionados como origen de datos.  
  
2.  Abra **WPF Designer** y asegúrese de que el diseñador tiene un contenedor que sea un destino de colocación válido para los elementos de la ventana **Orígenes de datos**.  
  
     Para obtener más información acerca de los destinos de colocación válidos, vea [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
3.  En el menú **Datos**, haga clic en **Mostrar orígenes de datos** para abrir la ventana **Orígenes de datos**.  
  
4.  Expanda los nodos de la ventana **Orígenes de datos** hasta que pueda ver la tabla u objeto primario y la tabla u objeto secundario relacionado.  
  
    > [!NOTE]
    >  La tabla u objeto secundario relacionado es el nodo que aparece como un nodo secundario expansible bajo la tabla u objeto primario.  
  
5.  Haga clic en el menú desplegable del nodo secundario y seleccione **Detalles**.  
  
6.  Expanda el nodo secundario.  
  
7.  Bajo el nodo secundario, haga clic en el menú desplegable que corresponde al elemento que relaciona los datos secundarios y primarios \(en el ejemplo anterior, sería el nodo **CustomerID**\).  Seleccione uno de los siguientes tipos de controles que admiten enlaces de búsqueda:  
  
    -   **ComboBox**  
  
    -   **ListBox**  
  
    -   **ListView**  
  
        > [!NOTE]
        >  Si el control **ListBox** o **ListView** no aparece en la lista, puede agregarlos.  Para obtener más información, vea [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    -   Cualquier control personalizado que se derive de <xref:System.Windows.Controls.Primitives.Selector>.  
  
        > [!NOTE]
        >  Para obtener información sobre cómo agregar controles personalizados a la lista de controles que se pueden seleccionar para los elementos de la ventana **Orígenes de datos**, vea [Agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
8.  Arrastre el nodo secundario desde la ventana **Orígenes de datos** hasta un contenedor de WPF Designer \(en el ejemplo anterior, el nodo secundario sería el nodo **Orders**\).  
  
     Visual Studio genera XAML que crea nuevos controles enlazados a datos para cada uno de los elementos arrastrados.  El XAML también agrega un nuevo objeto <xref:System.Windows.Data.CollectionViewSource> para la tabla u objeto secundario a los recursos del destino de colocación.  En el caso de algunos orígenes de datos, Visual Studio genera también código que carga los datos en la tabla u objeto.  Para obtener más información, vea [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
9. Arrastre el nodo primario desde la ventana **Orígenes de datos** hasta el control de enlace de búsqueda que creó previamente \(en el ejemplo anterior, el nodo primario sería el nodo **Customers**\).  
  
     Visual Studio establece algunas propiedades en el control para configurar el enlace de búsqueda.  En la tabla siguiente se enumeran las propiedades que modifica Visual Studio.  Si es necesario, puede cambiar estas propiedades en el XAML o en la ventana **Propiedades**.  
  
    |Propiedad.|Explicación del parámetro|  
    |----------------|-------------------------------|  
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Esta propiedad especifica la colección o el enlace que se usa para obtener los datos que se muestran en el control.  Visual Studio establece esta propiedad en el objeto <xref:System.Windows.Data.CollectionViewSource> de los datos primarios que se arrastraron hasta el control.|  
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Esta propiedad especifica la ruta de acceso del elemento de datos que se muestra en el control.  Visual Studio establece esta propiedad en la primera columna o propiedad de los datos primarios, después de la clave principal, que tiene un tipo de datos String.<br /><br /> Si desea mostrar otra columna o propiedad en los datos primarios, cambie esta propiedad por la ruta de acceso de una propiedad diferente.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio enlaza esta propiedad a la columna o propiedad de los datos secundarios que se arrastraron hasta el diseñador.  Esta es la clave externa de los datos primarios.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio establece esta propiedad en la ruta de acceso de la columna o propiedad de los datos secundarios que es la clave externa de los datos primarios.|  
  
## Vea también  
 [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Cómo: Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Cómo: Mostrar datos relacionados en aplicaciones WPF](../data-tools/display-related-data-in-wpf-applications.md)   
 [Tutorial: Mostrar datos relacionados en una aplicación WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)