---
title: Filtrar y ordenar los datos en una aplicación Windows Forms
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 596397cc22cf0f0134463256c0861127dcfb81e1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586619"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrar y ordenar los datos en una aplicación Windows Forms

Los datos se filtran estableciendo la propiedad <xref:System.Windows.Forms.BindingSource.Filter%2A> en una expresión de cadena que devuelve los registros deseados.

Los datos se ordenan estableciendo la propiedad <xref:System.Windows.Forms.BindingSource.Sort%2A> en el nombre de columna en el que se desea ordenar; Anexe `DESC` para ordenar en orden descendente, o anexe `ASC` para ordenar en orden ascendente.

> [!NOTE]
> Si la aplicación no usa componentes de <xref:System.Windows.Forms.BindingSource>, puede filtrar y ordenar los datos mediante <xref:System.Data.DataView> objetos. Para obtener más información, vea las [vistas](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews)de datos.

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Para filtrar los datos mediante un componente BindingSource

- Establezca la propiedad <xref:System.Windows.Forms.BindingSource.Filter%2A> en la expresión que desea devolver. Por ejemplo, el código siguiente devuelve los clientes cuyo valor de `CompanyName` empieza por "B":

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Para ordenar los datos mediante un componente BindingSource

- Establezca la propiedad <xref:System.Windows.Forms.BindingSource.Sort%2A> en la columna por la que desea ordenar. Por ejemplo, el código siguiente ordena los clientes por la columna `CompanyName` en orden descendente:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Vea también

- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
