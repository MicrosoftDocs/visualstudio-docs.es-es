---
title: Crear tablas de búsqueda en aplicaciones de Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9fe49ee90dba3edd0e2777817c4903c6101a1b47
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586775"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Crear tablas de búsqueda en aplicaciones de Windows Forms

El término *tabla de búsqueda* describe controles enlazados con dos tablas de datos relacionadas. Estos controles de búsqueda muestran datos de la primera tabla basándose en un valor seleccionado en la segunda tabla.

Puede crear tablas de búsqueda arrastrando el nodo principal de una tabla primaria (desde la [ventana orígenes de datos](add-new-data-sources.md#data-sources-window)) hasta un control del formulario que ya esté enlazado a la columna de la tabla secundaria relacionada.

Por ejemplo, considérese una tabla de `Orders` en una base de datos de ventas. Cada registro de la tabla `Orders` incluye un `CustomerID` que indica el cliente que ha realizado el pedido. El `CustomerID` es una clave externa que señala a un registro del cliente en la tabla `Customers`. En este escenario, expanda la tabla `Orders` en la ventana **orígenes de datos** y establezca el nodo principal en **detalles**. A continuación, establezca la columna `CustomerID` para usar un <xref:System.Windows.Forms.ComboBox> (o cualquier otro control que admita el enlace de búsqueda) y arrastre el nodo `Orders` al formulario. Por último, arrastre el nodo `Customers` al control que está enlazado a la columna relacionada; en este caso, el <xref:System.Windows.Forms.ComboBox> enlazado a la columna `CustomerID`.

## <a name="to-databind-a-lookup-control"></a>Para enlazar con datos un control de búsqueda

1. Con el proyecto abierto, abra la **ventana orígenes de datos** eligiendo **Ver** > **otras ventanas** > **orígenes de datos**.

    > [!NOTE]
    > Las tablas de búsqueda requieren que dos tablas u objetos relacionados estén disponibles en la ventana **Orígenes de datos**. Para obtener más información, vea [relaciones en conjuntos de](relationships-in-datasets.md)datos.

2. Expanda los nodos de la ventana **Orígenes de datos** hasta que pueda ver la tabla primaria y todas sus columnas y la tabla secundaria relacionada y todas sus columnas.

    > [!NOTE]
    > El nodo de la tabla secundaria es el nodo que aparece como un nodo secundario expandible en la tabla primaria.

3. Cambie el tipo Drop de la tabla secundaria a **Detalles** seleccionando **Detalles** en la lista de control del nodo de la tabla secundaria. Para obtener más información, vea [establecer el control que se creará al arrastrar desde la ventana orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. Busque el nodo que relaciona las dos tablas (el nodo `CustomerID` en el ejemplo anterior). Cambie su tipo de colocación a un <xref:System.Windows.Forms.ComboBox>; para ello, seleccione **ComboBox** en la lista de controles.

5. Arrastre el nodo de tabla secundaria principal de la ventana **Orígenes de datos** a su formulario.

     En el formulario aparecen controles de enlace de datos (con etiquetas descriptivas) y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>). Aparece un componente [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator> en la bandeja de componentes.

6. Arrastre ahora el nodo de tabla primario principal de la ventana **Orígenes de datos** directamente al control de búsqueda (<xref:System.Windows.Forms.ComboBox>).

     En este momento se establecen los enlaces de búsqueda. Consulte en la tabla siguiente las propiedades específicas que se establecieron en el control.

    |La propiedad|Explicación del parámetro|
    |--------------| - |
    |**DataSource**|Visual Studio establece esta propiedad en el elemento <xref:System.Windows.Forms.BindingSource> creado para la tabla que ha arrastrado al control (a diferencia del elemento <xref:System.Windows.Forms.BindingSource> creado al mismo tiempo que el control).<br /><br /> Si necesita efectuar un ajuste, establézcalo en la <xref:System.Windows.Forms.BindingSource> de la tabla con la columna que desea mostrar.|
    |**DisplayMember**|Visual Studio establece esta propiedad en la primera columna tras la clave principal que tiene un tipo de datos String para la tabla que ha arrastrado al control.<br /><br /> Si necesita efectuar un ajuste, establézcalo en el nombre de columna que desea mostrar.|
    |**ValueMember**|Visual Studio establece esta propiedad en la primera columna que participa de la clave principal, o la primera columna de la tabla si no se ha definido ninguna clave.<br /><br /> Si necesita efectuar un ajuste, establézcalo en la clave principal de la tabla con la columna que desea mostrar.|
    |**SelectedValue**|Visual Studio establece esta propiedad en la columna original quitada de la ventana **Orígenes de datos**.<br /><br /> Si necesita efectuar un ajuste, establézcalo en la columna de clave externa de la tabla relacionada.|

## <a name="see-also"></a>Vea también

- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
