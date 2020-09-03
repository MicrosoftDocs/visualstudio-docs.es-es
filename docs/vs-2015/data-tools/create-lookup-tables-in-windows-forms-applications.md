---
title: Crear tablas de búsqueda en aplicaciones de Windows Forms | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3979d08757445e9df5fc159fe7642b04bf74b995
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72630932"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Crear tablas de búsqueda en aplicaciones de Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El término *tabla de búsqueda* describe controles enlazados con dos tablas de datos relacionadas. Estos controles de búsqueda muestran datos de la primera tabla basándose en un valor seleccionado en la segunda tabla.

 Puede crear tablas de búsqueda arrastrando el nodo principal de una tabla primaria (desde la [ventana orígenes de datos](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)) hasta un control del formulario que ya esté enlazado a la columna de la tabla secundaria relacionada.

 Por ejemplo, considérese una tabla de `Orders` en una base de datos de ventas. Cada registro de la tabla `Orders` incluye un `CustomerID` que indica el cliente que ha realizado el pedido. El `CustomerID` es una clave externa que señala a un registro del cliente en la tabla `Customers`. En este escenario, expanda la `Orders` tabla en la ventana **orígenes de datos** y establezca el nodo principal en **detalles**. A continuación, establezca la `CustomerID` columna para que use un <xref:System.Windows.Forms.ComboBox> (o cualquier otro control que admita el enlace de búsqueda) y arrastre el `Orders` nodo al formulario. Finalmente, arrastre el `Customers` nodo al control que está enlazado a la columna relacionada, en este caso, el <xref:System.Windows.Forms.ComboBox> enlazado a la `CustomerID` columna.

## <a name="to-databind-a-lookup-control"></a>Para enlazar con datos un control de búsqueda

1. Abra la ventana **Orígenes de datos**.

    > [!NOTE]
    > Las tablas de búsqueda requieren que dos tablas u objetos relacionados estén disponibles en la ventana **Orígenes de datos**.

2. Expanda los nodos de la ventana **Orígenes de datos** hasta que pueda ver la tabla primaria y todas sus columnas y la tabla secundaria relacionada y todas sus columnas.

    > [!NOTE]
    > El nodo de la tabla secundaria es el nodo que aparece como un nodo secundario expandible en la tabla primaria.

3. Cambie el tipo Drop de la tabla secundaria a **Detalles** seleccionando **Detalles** en la lista de control del nodo de la tabla secundaria. Para obtener más información, vea [establecer el control que se creará al arrastrar desde la ventana orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. Busque el nodo que relaciona las dos tablas (el `CustomerID` nodo en el ejemplo anterior). Cambie su tipo de colocación a seleccionando <xref:System.Windows.Forms.ComboBox> **ComboBox** en la lista de controles.

5. Arrastre el nodo de tabla secundaria principal de la ventana **Orígenes de datos** a su formulario.

     En el formulario aparecen controles de enlace de datos (con etiquetas descriptivas) y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>). Un [conjunto](../data-tools/dataset-tools-in-visual-studio.md)de objetos, TableAdapter, <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator> aparecen en la bandeja de componentes.

6. Ahora, arrastre el nodo principal de la tabla principal desde la ventana **orígenes de datos** directamente al control de búsqueda ( <xref:System.Windows.Forms.ComboBox> ).

     En este momento se establecen los enlaces de búsqueda. Consulte en la tabla siguiente las propiedades concretas establecidas en el control.

    |Propiedad|Explicación del parámetro|
    |--------------|----------------------------|
    |**DataSource**|Visual Studio establece esta propiedad en el elemento <xref:System.Windows.Forms.BindingSource> creado para la tabla que ha arrastrado al control (a diferencia del elemento <xref:System.Windows.Forms.BindingSource> creado al mismo tiempo que el control).<br /><br /> Si necesita realizar un ajuste, establezca esta propiedad en el elemento <xref:System.Windows.Forms.BindingSource> de la tabla con la columna que desea mostrar.|
    |**DisplayMember**|Visual Studio establece esta propiedad en la primera columna tras la clave principal que tiene un tipo de datos String para la tabla que ha arrastrado al control.<br /><br /> Si necesita realizar un ajuste, establezca esta propiedad en el nombre de columna que desea mostrar.|
    |**ValueMember**|Visual Studio establece esta propiedad en la primera columna que participa de la clave principal, o la primera columna de la tabla si no se ha definido ninguna clave.<br /><br /> Si necesita realizar un ajuste, establezca esta propiedad en la clave principal de la tabla con la columna que desea mostrar.|
    |**SelectedValue**|Visual Studio establece esta propiedad en la columna original quitada de la ventana **Orígenes de datos**.<br /><br /> Si necesita realizar un ajuste, establezca esta propiedad en la columna de clave externa en la tabla relacionada.|

## <a name="see-also"></a>Consulte también
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
