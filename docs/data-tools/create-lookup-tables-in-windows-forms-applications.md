---
title: Crear tablas de búsqueda en aplicaciones de Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 315bed179a21ec99a256fcc8cb16f6fc1164f238
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Crear tablas de búsqueda en aplicaciones de Windows Forms
El término *tabla de búsqueda* describe los controles que están enlazados a dos tablas relacionadas. Estos controles de búsqueda muestran datos de la primera tabla basándose en un valor seleccionado en la segunda tabla.

 Puede crear tablas de búsqueda arrastrando el nodo principal de una tabla primaria (desde el [ventana Orígenes de datos](add-new-data-sources.md)) a un control en el formulario que ya esté enlazado a la columna de la tabla secundaria relacionada.

 Por ejemplo, considérese una tabla de `Orders` en una base de datos de ventas. Cada registro de la `Orders` tabla incluye una `CustomerID`, que indica el cliente que realizó el pedido. El `CustomerID` es una clave externa que señala a un registro del cliente en la tabla `Customers`. En este escenario, se expande el `Orders` tabla el **orígenes de datos** ventana y establecería el nodo principal en **detalles**. A continuación, establezca el `CustomerID` columna que se va a usar un <xref:System.Windows.Forms.ComboBox> (o cualquier otro control que admita el enlace de búsqueda) y arrastre la `Orders` nodo hasta el formulario. Por último, arrastre el `Customers` nodo en el control que está enlazado a la columna relacionada, en este caso, el <xref:System.Windows.Forms.ComboBox> enlazados a la `CustomerID` columna.

## <a name="to-databind-a-lookup-control"></a>Para enlazar con datos un control de búsqueda

1.  Abra la **orígenes de datos** ventana.

    > [!NOTE]
    >  Tablas de búsqueda requieren que dos tablas u objetos relacionados están disponibles en la **orígenes de datos** ventana. Para obtener más información, consulte [relaciones en conjuntos de datos](relationships-in-datasets.md).

2.  Expanda los nodos en el **orígenes de datos** ventana hasta que pueda ver la tabla primaria y todas sus columnas y la tabla secundaria relacionada y todas sus columnas.

    > [!NOTE]
    >  El nodo de la tabla secundaria es el nodo que aparece como un nodo secundario expandible en la tabla primaria.

3.  Cambie el tipo drop de la tabla secundaria a **detalles** seleccionando **detalles** desde la lista de control de los secundarios del nodo de tabla. Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana de orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4.  Busque el nodo que relaciona las dos tablas (el `CustomerID` nodo en el ejemplo anterior). Cambie su tipo drop para un <xref:System.Windows.Forms.ComboBox> seleccionando **ComboBox** desde la lista de control.

5.  Arrastre el nodo de tabla secundaria principal de la **orígenes de datos** ventana hasta el formulario.

     En el formulario aparecen controles de enlace de datos (con etiquetas descriptivas) y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>). A [conjunto de datos](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes.

6.  Ahora, arrastre el nodo de tabla primario principal de la **orígenes de datos** ventana directamente en el control de búsqueda (la <xref:System.Windows.Forms.ComboBox>).

     En este momento se establecen los enlaces de búsqueda. Consulte en la tabla siguiente las propiedades concretas establecidas en el control.

    |Property|Explicación del parámetro|
    |--------------|----------------------------|
    |**Origen de datos**|Visual Studio establece esta propiedad en el elemento <xref:System.Windows.Forms.BindingSource> creado para la tabla que ha arrastrado al control (a diferencia del elemento <xref:System.Windows.Forms.BindingSource> creado al mismo tiempo que el control).<br /><br /> Si necesita realizar un ajuste, establezca esta propiedad en el elemento <xref:System.Windows.Forms.BindingSource> de la tabla con la columna que desea mostrar.|
    |**DisplayMember**|Visual Studio establece esta propiedad en la primera columna tras la clave principal que tiene un tipo de datos String para la tabla que ha arrastrado al control.<br /><br /> Si necesita realizar un ajuste, establezca esta propiedad en el nombre de columna que desea mostrar.|
    |**ValueMember**|Visual Studio establece esta propiedad en la primera columna que participa de la clave principal, o la primera columna de la tabla si no se ha definido ninguna clave.<br /><br /> Si necesita realizar un ajuste, establezca esta propiedad en la clave principal de la tabla con la columna que desea mostrar.|
    |**SelectedValue**|Visual Studio establece esta propiedad en la columna original quitada de la **orígenes de datos** ventana.<br /><br /> Si necesita realizar un ajuste, establezca esta propiedad en la columna de clave externa en la tabla relacionada.|

## <a name="see-also"></a>Vea también

- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)