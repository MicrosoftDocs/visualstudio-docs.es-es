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
ms.openlocfilehash: c52e5f157dcbc6dcfeacf72df465bd3d8d9d172e
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304941"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Crear tablas de búsqueda en aplicaciones de Windows Forms

El término *tabla de búsqueda* describe controles enlazados con dos tablas de datos relacionadas. Estos controles de búsqueda muestran datos de la primera tabla basándose en un valor seleccionado en la segunda tabla.

Puede crear tablas de búsqueda arrastrando el nodo principal de una tabla primaria (desde el [ventana Orígenes de datos](add-new-data-sources.md#data-sources-window)) a un control en el formulario que ya está enlazado a la columna de la tabla secundaria relacionada.

Por ejemplo, considérese una tabla de `Orders` en una base de datos de ventas. Cada registro de la tabla `Orders` incluye un `CustomerID` que indica el cliente que ha realizado el pedido. El `CustomerID` es una clave externa que señala a un registro del cliente en la tabla `Customers`. En este escenario, se expande el `Orders` de tabla en la **orígenes de datos** ventana y establezca el nodo principal en **detalles**. A continuación, establezca el `CustomerID` columna que se utilizará un <xref:System.Windows.Forms.ComboBox> (o cualquier otro control que admite el enlace de búsqueda) y arrastre el `Orders` nodo hasta el formulario. Por último, arrastre el `Customers` nodo hasta el control que está enlazado a la columna relacionada, en este caso, el <xref:System.Windows.Forms.ComboBox> enlazado a la `CustomerID` columna.

## <a name="to-databind-a-lookup-control"></a>Para enlazar con datos un control de búsqueda

1.  Con el proyecto abierto, abra el **orígenes de datos** ventana eligiendo **vista** > **Other Windows** > **losorígenesdedatos**.

    > [!NOTE]
    > Las tablas de búsqueda requieren que dos tablas u objetos relacionados estén disponibles en la ventana **Orígenes de datos**. Para obtener más información, consulte [relaciones en conjuntos de datos](relationships-in-datasets.md).

2.  Expanda los nodos de la ventana **Orígenes de datos** hasta que pueda ver la tabla primaria y todas sus columnas y la tabla secundaria relacionada y todas sus columnas.

    > [!NOTE]
    > El nodo de la tabla secundaria es el nodo que aparece como un nodo secundario expandible en la tabla primaria.

3.  Cambie el tipo Drop de la tabla secundaria a **Detalles** seleccionando **Detalles** en la lista de control del nodo de la tabla secundaria. Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4.  Busque el nodo que relaciona las dos tablas (el `CustomerID` nodo en el ejemplo anterior). Cambie su tipo de colocación para un <xref:System.Windows.Forms.ComboBox> seleccionando **ComboBox** desde la lista de control.

5.  Arrastre el nodo de tabla secundaria principal de la ventana **Orígenes de datos** a su formulario.

     En el formulario aparecen controles de enlace de datos (con etiquetas descriptivas) y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>). Aparece un componente [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator> en la bandeja de componentes.

6.  Arrastre ahora el nodo de tabla primario principal de la ventana **Orígenes de datos** directamente al control de búsqueda (<xref:System.Windows.Forms.ComboBox>).

     En este momento se establecen los enlaces de búsqueda. Consulte la siguiente tabla para las propiedades específicas que se establecieron en el control.

    |Propiedad.|Explicación del parámetro|
    |--------------| - |
    |**DataSource**|Visual Studio establece esta propiedad en el elemento <xref:System.Windows.Forms.BindingSource> creado para la tabla que ha arrastrado al control (a diferencia del elemento <xref:System.Windows.Forms.BindingSource> creado al mismo tiempo que el control).<br /><br /> Si necesita realizar un ajuste, establezca esta opción en el <xref:System.Windows.Forms.BindingSource> de la tabla con la columna que desea mostrar.|
    |**DisplayMember**|Visual Studio establece esta propiedad en la primera columna tras la clave principal que tiene un tipo de datos String para la tabla que ha arrastrado al control.<br /><br /> Si necesita realizar un ajuste, establezca esta opción en el nombre de columna que desea mostrar.|
    |**ValueMember**|Visual Studio establece esta propiedad en la primera columna que participa de la clave principal, o la primera columna de la tabla si no se ha definido ninguna clave.<br /><br /> Si necesita realizar un ajuste, establezca esta opción en la clave principal en la tabla con la columna que desea mostrar.|
    |**SelectedValue**|Visual Studio establece esta propiedad en la columna original quitada de la ventana **Orígenes de datos**.<br /><br /> Si necesita realizar un ajuste, establezca esta opción en la columna de clave externa en la tabla relacionada.|

## <a name="see-also"></a>Vea también

- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)