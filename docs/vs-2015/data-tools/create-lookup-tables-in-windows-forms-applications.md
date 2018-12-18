---
title: Crear tablas de búsqueda en aplicaciones de Windows Forms | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 334acba1e70545f1f8be758e34c8fc4843878406
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223902"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Crear tablas de búsqueda en aplicaciones de Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
El término *tabla de búsqueda* describe controles enlazados a dos tablas relacionadas. Estos controles de búsqueda muestran datos de la primera tabla basándose en un valor seleccionado en la segunda tabla.  
  
 Puede crear tablas de búsqueda arrastrando el nodo principal de una tabla primaria (desde el [ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)) a un control en el formulario que ya está enlazado a la columna de la tabla secundaria relacionada.  
  
 Por ejemplo, considérese una tabla de `Orders` en una base de datos de ventas. Cada registro de la `Orders` tabla incluye un `CustomerID`, que indica qué cliente realizó el pedido. El `CustomerID` es una clave externa que señala a un registro del cliente en la tabla `Customers`. En este escenario, se expande el `Orders` de tabla en la **orígenes de datos** ventana y establezca el nodo principal en **detalles**. A continuación, establezca el `CustomerID` columna que se utilizará un <xref:System.Windows.Forms.ComboBox> (o cualquier otro control que admite el enlace de búsqueda) y arrastre el `Orders` nodo hasta el formulario. Por último, arrastre el `Customers` nodo hasta el control que está enlazado a la columna relacionada, en este caso, el <xref:System.Windows.Forms.ComboBox> enlazado a la `CustomerID` columna.  
  
## <a name="to-databind-a-lookup-control"></a>Para enlazar con datos un control de búsqueda  
  
1.  Abra el **orígenes de datos** ventana.  
  
    > [!NOTE]
    >  Las tablas de búsqueda requieren que dos tablas u objetos relacionados están disponibles en el **orígenes de datos** ventana. Para más información, consulte [Cómo: Mostrar datos relacionados en una aplicación de Windows Forms](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
2.  Expanda los nodos en el **orígenes de datos** ventana hasta que pueda ver la tabla primaria y todas sus columnas y la tabla secundaria relacionada y todas sus columnas.  
  
    > [!NOTE]
    >  El nodo de la tabla secundaria es el nodo que aparece como un nodo secundario expandible en la tabla primaria.  
  
3.  Cambiar el tipo de colocación de la tabla secundaria a **detalles** seleccionando **detalles** desde la lista de control en el nodo de la tabla secundaria. Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
4.  Busque el nodo que relaciona las dos tablas (el `CustomerID` nodo en el ejemplo anterior). Cambie su tipo de colocación para un <xref:System.Windows.Forms.ComboBox> seleccionando **ComboBox** desde la lista de control.  
  
5.  Arrastre el nodo de la tabla secundaria principal de la **orígenes de datos** ventana hasta su formulario.  
  
     En el formulario aparecen controles de enlace de datos (con etiquetas descriptivas) y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>). Un [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes.  
  
6.  Ahora, arrastre el nodo de tabla primario principal desde el **orígenes de datos** ventana directamente al control de búsqueda (el <xref:System.Windows.Forms.ComboBox>).  
  
     En este momento se establecen los enlaces de búsqueda. Consulte en la tabla siguiente las propiedades concretas establecidas en el control.  
  
    |Property|Explicación del parámetro|  
    |--------------|----------------------------|  
    |**Origen de datos**|Visual Studio establece esta propiedad en el elemento <xref:System.Windows.Forms.BindingSource> creado para la tabla que ha arrastrado al control (a diferencia del elemento <xref:System.Windows.Forms.BindingSource> creado al mismo tiempo que el control).<br /><br /> Si necesita realizar un ajuste, establezca esta propiedad en el elemento <xref:System.Windows.Forms.BindingSource> de la tabla con la columna que desea mostrar.|  
    |**DisplayMember**|Visual Studio establece esta propiedad en la primera columna tras la clave principal que tiene un tipo de datos String para la tabla que ha arrastrado al control.<br /><br /> Si necesita realizar un ajuste, establezca esta propiedad en el nombre de columna que desea mostrar.|  
    |**ValueMember**|Visual Studio establece esta propiedad en la primera columna que participa de la clave principal, o la primera columna de la tabla si no se ha definido ninguna clave.<br /><br /> Si necesita realizar un ajuste, establezca esta propiedad en la clave principal de la tabla con la columna que desea mostrar.|  
    |**SelectedValue**|Visual Studio establece esta propiedad en la columna original quitada de la **orígenes de datos** ventana.<br /><br /> Si necesita realizar un ajuste, establezca esta propiedad en la columna de clave externa en la tabla relacionada.|  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

