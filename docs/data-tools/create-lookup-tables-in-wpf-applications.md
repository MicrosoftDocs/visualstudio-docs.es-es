---
title: Crear tablas de búsqueda en aplicaciones WPF
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c76f769234d8b8c14ccd44d8c2cf4c669bf48ffd
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305486"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Crear tablas de búsqueda en aplicaciones WPF

El término *tabla de búsqueda* (a veces denominado un *enlace búsqueda*) describe un control que muestra información de una tabla de datos en función del valor de un campo de clave externa de otra tabla. Puede crear una tabla de búsqueda arrastrando el nodo principal de una tabla primaria o de objeto en el **orígenes de datos** ventana a un control que ya está enlazado a una columna o propiedad en una tabla secundaria relacionada.

Por ejemplo, considérese una tabla de `Orders` en una base de datos de ventas. Cada registro de la `Orders` tabla incluye una `CustomerID` que indica qué cliente realizó el pedido. El `CustomerID` es una clave externa que señala a un registro de cliente en el `Customers` tabla. Al mostrar una lista de pedidos desde el `Orders` tabla, es posible que desee mostrar el nombre real del cliente en lugar de la `CustomerID`. Dado que es el nombre del cliente en el `Customers` tabla, deberá crear una tabla de búsqueda para mostrar el nombre del cliente. Los usos de la tabla de búsqueda el `CustomerID` valor en el `Orders` grabar para navegar por la relación y devolver el nombre del cliente.

## <a name="to-create-a-lookup-table"></a>Para crear una tabla de búsqueda

1.  Agregue uno de los siguientes tipos de orígenes de datos con datos relacionados al proyecto:

    -   Conjunto de datos o Entity Data Model.

    -   Servicio de datos de WCF, servicio WCF o servicio web. Para obtener más información, consulte [Cómo: conectarse a datos en un servicio](../data-tools/how-to-connect-to-data-in-a-service.md).

    -   Objects Para obtener más información, consulte [enlazar a objetos en Visual Studio](bind-objects-in-visual-studio.md).

    > [!NOTE]
    > Para poder crear una tabla de búsqueda, deben existir dos tablas u objetos relacionados como un origen de datos para el proyecto.

2.  Abra el **WPF Designer**y asegúrese de que el diseñador contiene un contenedor que sea un destino válido para los elementos de la **orígenes de datos** ventana.

     Para obtener más información acerca de los destinos de colocación válidos, vea [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

3.  En el menú Datos **, haga clic en Mostrar orígenes de datos** para abrir la ventana Orígenes de datos **.

4.  Expanda los nodos en el **orígenes de datos** ventana hasta que pueda ver la tabla primaria o el objeto y la tabla secundaria relacionada u objeto.

    > [!NOTE]
    > La tabla secundaria relacionada o el objeto es el nodo que aparece como un nodo secundario expandible en la tabla u objeto primario.

5.  Haga clic en el menú desplegable del nodo secundario y seleccione **detalles**.

6.  Expanda el nodo secundario.

7.  En el nodo secundario, haga clic en el menú desplegable para el elemento que se relaciona con los datos primarios y secundarios. (En el ejemplo anterior, se trata la **CustomerID** nodo.) Seleccione uno de los siguientes tipos de controles que admiten el enlace de búsqueda:

    -   **ComboBox**

    -   **ListBox**

    -   **ListView**

        > [!NOTE]
        > Si el **ListBox** o **ListView** control no aparece en la lista, puede agregar estos controles a la lista. Para obtener información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    -   Cualquier control personalizado que se deriva de <xref:System.Windows.Controls.Primitives.Selector>.

        > [!NOTE]
        > Para obtener información sobre cómo agregar controles personalizados a la lista de controles puede seleccionar elementos en el **orígenes de datos** ventana, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8.  Arrastre el nodo secundario de la **orígenes de datos** ventana a un contenedor en el diseñador WPF. (En el ejemplo anterior, el nodo secundario es el **pedidos** nodo.)

     Visual Studio genera XAML que crea nuevos controles enlazados a datos para cada uno de los elementos que arrastra. El XAML también agrega un nuevo <xref:System.Windows.Data.CollectionViewSource> para la tabla u objeto secundario a los recursos de destino. Para algunos orígenes de datos, Visual Studio también genera código para cargar datos en la tabla u objeto. Para obtener más información, consulte [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

9. Arrastre el nodo primario de la **orígenes de datos** ventana al control de búsqueda de enlace que creó anteriormente. (En el ejemplo anterior, el nodo primario es el **clientes** nodo).

     Visual Studio establece algunas propiedades en el control para configurar el enlace de búsqueda. En la tabla siguiente se enumera las propiedades que Visual Studio modifica. Si es necesario, puede cambiar estas propiedades en el XAML o en el **propiedades** ventana.

    |Propiedad.|Explicación del parámetro|
    |--------------| - |
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Esta propiedad especifica la colección o enlace que se usa para obtener los datos que se muestran en el control. Visual Studio establece esta propiedad en el <xref:System.Windows.Data.CollectionViewSource> para los datos primarios que se ha arrastrado al control.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Esta propiedad especifica la ruta de acceso del elemento de datos que se muestra en el control. Visual Studio establece esta propiedad en la primera columna o propiedad en los datos primarios y, después de la clave principal, que tiene un tipo de datos de cadena.<br /><br /> Si desea mostrar una columna o propiedad diferente en los datos primarios, puede cambiar esta propiedad a la ruta de acceso de una propiedad diferente.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio enlaza esta propiedad a la columna o propiedad de los datos secundarios que se arrastran hasta el diseñador. Se trata de la clave externa a los datos primarios.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio establece esta propiedad en la ruta de acceso de la columna o propiedad de los datos y que es la clave externa a los datos primarios y secundarios.|

## <a name="see-also"></a>Vea también

- [Enlace de controles de WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Mostrar datos relacionados en aplicaciones WPF](../data-tools/display-related-data-in-wpf-applications.md)
- [Tutorial: Mostrar datos relacionados en una aplicación WPF](../data-tools/display-related-data-in-wpf-applications.md)