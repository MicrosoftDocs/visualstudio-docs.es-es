---
title: Creación de tablas de búsqueda en aplicaciones WPF
description: Cree tablas de búsqueda en aplicaciones de WPF. Una tabla de búsqueda es un control que muestra información de una tabla de datos basada en un valor de campo de clave externa de otra tabla.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: cc390642155d33f75bf5c4a69236945658845639
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867105"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Creación de tablas de búsqueda en aplicaciones WPF

La *tabla de búsqueda* de términos (a veces denominada *enlace de búsqueda*) describe un control que muestra información de una tabla de datos en función del valor de un campo de clave externa de otra tabla. Puede crear una tabla de búsqueda arrastrando el nodo principal de una tabla o un objeto primario en la ventana **orígenes de datos** hasta un control que ya esté enlazado a una columna o propiedad de una tabla secundaria relacionada.

Por ejemplo, considérese una tabla de `Orders` en una base de datos de ventas. Cada registro de la `Orders` tabla incluye un `CustomerID` que indica qué cliente realizó el pedido. `CustomerID`Es una clave externa que señala a un registro de cliente en la `Customers` tabla. Cuando se muestra una lista de pedidos de la `Orders` tabla, es posible que desee mostrar el nombre real del cliente en lugar del `CustomerID` . Dado que el nombre del cliente está en la `Customers` tabla, debe crear una tabla de búsqueda para mostrar el nombre del cliente. La tabla de búsqueda utiliza el `CustomerID` valor del `Orders` registro para navegar por la relación y devolver el nombre del cliente.

## <a name="to-create-a-lookup-table"></a>Para crear una tabla de búsqueda

1. Agregue uno de los siguientes tipos de orígenes de datos con datos relacionados al proyecto:

    - Conjunto de Entity Data Model.

    - Servicio de datos de WCF, servicio de WCF o servicio Web. Para obtener más información, consulte [How to: Connect to Data in a Service](../data-tools/how-to-connect-to-data-in-a-service.md).

    - Objetos. Para obtener más información, vea [enlazar a objetos en Visual Studio](bind-objects-in-visual-studio.md).

    > [!NOTE]
    > Para poder crear una tabla de búsqueda, deben existir dos tablas u objetos relacionados como origen de datos para el proyecto.

2. Abra **WPF Designer** y asegúrese de que el diseñador contiene un contenedor que es un destino de colocación válido para los elementos de la ventana **orígenes de datos** .

     Para obtener más información sobre los destinos de colocación válidos, vea [enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

3. En el menú **Datos**, haga clic en **Mostrar orígenes de datos** para abrir la ventana **Orígenes de datos**.

4. Expanda los nodos en la ventana **orígenes de datos** , hasta que pueda ver la tabla o el objeto primario y el objeto o la tabla secundaria relacionada.

    > [!NOTE]
    > La tabla o el objeto secundario relacionado es el nodo que aparece como un nodo secundario expansible en el objeto o la tabla primaria.

5. Haga clic en el menú desplegable del nodo secundario y seleccione **detalles**.

6. Expanda el nodo secundario.

7. En el nodo secundario, haga clic en el menú desplegable del elemento que relaciona los datos primarios y secundarios. (En el ejemplo anterior, es el nodo **CustomerID** ). Seleccione uno de los siguientes tipos de controles que admiten el enlace de búsqueda:

    - **ComboBox**

    - **Identificación**

    - **ListView**

        > [!NOTE]
        > Si el control **ListBox** o **ListView** no aparece en la lista, puede agregar estos controles a la lista. Para obtener más información, vea [establecer el control que se creará al arrastrar desde la ventana orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    - Cualquier control personalizado que se derive de <xref:System.Windows.Controls.Primitives.Selector> .

        > [!NOTE]
        > Para obtener información sobre cómo agregar controles personalizados a la lista de controles que puede seleccionar para los elementos de la ventana **orígenes de datos** , vea [Agregar controles personalizados a la ventana orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8. Arrastre el nodo secundario desde la ventana **orígenes de datos** hasta un contenedor en WPF Designer. (En el ejemplo anterior, el nodo secundario es el nodo **Orders** ).

     Visual Studio genera XAML que crea nuevos controles enlazados a datos para cada uno de los elementos que se arrastran. El XAML también agrega un nuevo <xref:System.Windows.Data.CollectionViewSource> para la tabla o el objeto secundario a los recursos del destino de colocación. En el caso de algunos orígenes de datos, Visual Studio también genera código para cargar datos en la tabla o el objeto. Para obtener más información, vea [enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

9. Arrastre el nodo primario desde la ventana **orígenes de datos** hasta el control de enlace de búsqueda que creó anteriormente. (En el ejemplo anterior, el nodo primario es el nodo **Customers** ).

     Visual Studio establece algunas propiedades en el control para configurar el enlace de búsqueda. En la tabla siguiente se enumeran las propiedades que Visual Studio modifica. Si es necesario, puede cambiar estas propiedades en el código XAML o en la ventana **propiedades** .

    |Propiedad|Explicación del parámetro|
    |--------------| - |
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Esta propiedad especifica la colección o el enlace que se utiliza para obtener los datos que se muestran en el control. Visual Studio establece esta propiedad en <xref:System.Windows.Data.CollectionViewSource> para los datos primarios que ha arrastrado al control.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Esta propiedad especifica la ruta de acceso del elemento de datos que se muestra en el control. Visual Studio establece esta propiedad en la primera columna o propiedad de los datos primarios, después de la clave principal, que tiene un tipo de datos de cadena.<br /><br /> Si desea mostrar una columna o propiedad diferente en los datos primarios, cambie esta propiedad a la ruta de acceso de una propiedad diferente.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio enlaza esta propiedad a la columna o propiedad de los datos secundarios que arrastró al diseñador. Esta es la clave externa para los datos primarios.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio establece esta propiedad en la ruta de acceso de la columna o propiedad de los datos secundarios que son la clave externa para los datos primarios.|

## <a name="see-also"></a>Vea también

- [Enlace de controles de WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Mostrar datos relacionados en aplicaciones WPF](../data-tools/display-related-data-in-wpf-applications.md)
- [Tutorial: Mostrar datos relacionados en una aplicación WPF](../data-tools/display-related-data-in-wpf-applications.md)
