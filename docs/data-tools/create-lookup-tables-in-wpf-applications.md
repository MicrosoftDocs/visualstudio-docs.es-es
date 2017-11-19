---
title: "Crear tablas de búsqueda en aplicaciones WPF | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 78322512fdc59b4ba661bca0d40d1532ac4c98e2
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Crear tablas de búsqueda en aplicaciones WPF
El término *tabla de búsqueda* (a veces denominado un *enlace de búsqueda*) describe un control que muestra información de una tabla de datos en función del valor de un campo de clave externa de otra tabla. Puede crear una tabla de búsqueda arrastrando el nodo principal de una tabla primaria o de objeto en el **orígenes de datos** ventana en un control que ya está enlazado a una columna o propiedad en una tabla secundaria relacionada.  
  
Por ejemplo, considérese una tabla de `Orders` en una base de datos de ventas. Cada registro de la `Orders` tabla incluye una `CustomerID` que indica el cliente que realizó el pedido. El `CustomerID` es una clave externa que señala a un registro de cliente en el `Customers` tabla. Al mostrar una lista de pedidos de la `Orders` tabla, puede que desee mostrar el nombre real del cliente en lugar de la `CustomerID`. Dado que es el nombre del cliente en el `Customers` tabla, debe crear una tabla de búsqueda para mostrar el nombre del cliente. Los usos de la tabla de búsqueda la `CustomerID` valor en el `Orders` registrar para navegar por la relación y devolver el nombre del cliente.  
  
## <a name="to-create-a-lookup-table"></a>Para crear una tabla de búsqueda  
  
1.  Agregue uno de los siguientes tipos de orígenes de datos con los datos relacionados al proyecto:  
  
    -   Conjunto de datos o Entity Data Model. 
  
    -   Servicio de datos de WCF, servicio WCF o servicio Web. Para obtener más información, consulte [Cómo: conectarse a los datos en un servicio](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
    -   objetos. Para obtener más información, consulte [enlazar a objetos en Visual Studio](bind-objects-in-visual-studio.md).  
  
    > [!NOTE]
    >  Para poder crear una tabla de búsqueda, deben existir dos tablas u objetos relacionados como un origen de datos para el proyecto.  
  
2.  Abra la **WPF Designer**y asegúrese de que el diseñador contiene un contenedor que es un destino válido para los elementos de la **orígenes de datos** ventana.  
  
     Para obtener más información acerca de los destinos de colocación válidos, vea [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).  
  
3.  En el **datos** menú, haga clic en **Mostrar orígenes de datos** para abrir el **orígenes de datos** ventana.  
  
4.  Expanda los nodos en el **orígenes de datos** ventana, hasta que pueda ver la tabla primaria o el objeto y la tabla secundaria relacionada u objeto.  
  
    > [!NOTE]
    >  La tabla secundaria relacionada o el objeto es el nodo que aparece como un nodo secundario expandible en la tabla u objeto primario.  
  
5.  Haga clic en el menú desplegable del nodo secundario y seleccione **detalles**.  
  
6.  Expanda el nodo secundario.  
  
7.  En el nodo secundario, haga clic en el menú desplegable para el elemento que está relacionada con los datos primarios y secundarios. (En el ejemplo anterior, se trata de la **CustomerID** nodo.) Seleccione uno de los siguientes tipos de controles que admiten el enlace de búsqueda:  
  
    -   **ComboBox**  
  
    -   **ListBox**  
  
    -   **ListView**  
  
        > [!NOTE]
        >  Si el **ListBox** o **ListView** control no aparece en la lista, puede agregar estos controles a la lista. Para obtener información, consulte [establecer el control que se creará al arrastrar desde la ventana de orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    -   Cualquier control personalizado que deriva de <xref:System.Windows.Controls.Primitives.Selector>.  
  
        > [!NOTE]
        >  Para obtener información sobre cómo agregar controles personalizados a la lista de controles puede seleccionar para los elementos de la **orígenes de datos** ventana, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
8.  Arrastre el nodo secundario de la **orígenes de datos** ventana en un contenedor en el diseñador WPF. (En el ejemplo anterior, el nodo secundario es el **pedidos** nodo.)  
  
     Visual Studio genera XAML que crea nuevos controles enlazados a datos para cada uno de los elementos que se arrastran. El XAML también agrega un nuevo <xref:System.Windows.Data.CollectionViewSource> para la tabla u objeto secundario a los recursos del destino de eliminación. Para algunos orígenes de datos, Visual Studio también genera código para cargar datos en la tabla u objeto. Para obtener más información, consulte [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).  
  
9. Arrastre el nodo primario de la **orígenes de datos** ventana hasta el control de enlace de búsqueda que creó anteriormente. (En el ejemplo anterior, el nodo principal es la **clientes** nodo).  
  
     Visual Studio establece algunas propiedades en el control para configurar el enlace de búsqueda. En la tabla siguiente se enumera las propiedades que modifica Visual Studio. Si es necesario, puede cambiar estas propiedades en el XAML o en la **propiedades** ventana.  
  
    |Propiedad|Explicación del parámetro|  
    |--------------|----------------------------|  
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Esta propiedad especifica la colección o el enlace que se utiliza para obtener los datos que se muestran en el control. Visual Studio establece esta propiedad en el <xref:System.Windows.Data.CollectionViewSource> de los datos primarios que ha arrastrado al control.|  
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Esta propiedad especifica la ruta de acceso del elemento de datos que se muestra en el control. Visual Studio establece esta propiedad en la primera columna o propiedad en los datos primarios y, después de la clave principal, que tiene un tipo de datos de cadena.<br /><br /> Si desea mostrar una columna o propiedad diferente en los datos primarios, cambie esta propiedad a la ruta de acceso de una propiedad diferente.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio enlaza esta propiedad a la columna o propiedad de datos secundarios que se arrastran hasta el diseñador. Se trata de la clave externa a los datos primarios.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio establece esta propiedad en la ruta de acceso de la columna o propiedad de los datos secundarios que es la clave externa a los datos primarios.|  
  
## <a name="see-also"></a>Vea también
[Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)   
[Mostrar datos relacionados en aplicaciones WPF](../data-tools/display-related-data-in-wpf-applications.md)   
[Tutorial: Mostrar datos relacionados en una aplicación WPF](../data-tools/display-related-data-in-wpf-applications.md)