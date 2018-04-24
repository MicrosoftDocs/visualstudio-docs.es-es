---
title: Filtrar y ordenar datos en una aplicación de formularios Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ff5c31b14f13252fbcad0f42762627a14e610591
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrar y ordenar datos en una aplicación de formularios Windows Forms
Los datos se filtran estableciendo la propiedad <xref:System.Windows.Forms.BindingSource.Filter%2A> en una expresión de cadena que devuelve los registros deseados.

 Puede ordenar los datos estableciendo la propiedad <xref:System.Windows.Forms.BindingSource.Sort%2A> en el nombre de columna por la que desea ordenar; anexe `DESC` para realizar la ordenación en sentido descendente, o bien, `ASC` para hacerlo en sentido ascendente.

> [!NOTE]
>  Si la aplicación no usa <xref:System.Windows.Forms.BindingSource> componentes, puede filtrar y ordenar los datos mediante el uso de <xref:System.Data.DataView> objetos. Para obtener más información, consulte [DataView](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Para filtrar datos mediante un componente BindingSource

-   Establezca la propiedad <xref:System.Windows.Forms.BindingSource.Filter%2A> en la expresión que desea devolver. Por ejemplo, el código siguiente devuelve los clientes cuyo valor de `CompanyName` empieza por "B":

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Para ordenar los datos mediante el uso de un componente BindingSource

-   Establezca la propiedad <xref:System.Windows.Forms.BindingSource.Sort%2A> en la columna por la que desea ordenar. Por ejemplo, el código siguiente ordena los clientes por la columna `CompanyName` en orden descendente:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Vea también

- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)