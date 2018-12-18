---
title: Consultar conjuntos de datos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a6e1ff0cd6f77d2155ff4982ca02657a741c02d7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890574"
---
# <a name="query-datasets"></a>Consultar conjuntos de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Para buscar registros específicos de un conjunto de datos, utilice el método FindBy en la tabla de datos, escribir su propio bucle de foreach a través de la colección de filas de la tabla o usar [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17). LINQ to DataSet.  
  
## <a name="dataset-case-sensitivity"></a>Conjunto de datos entre mayúsculas y minúsculas  
 Dentro de un conjunto de datos, los nombres de columna y tabla distinguen mayúsculas de minúsculas de forma predeterminada, es decir, una tabla en un conjunto de datos denominado "Customers" también se puede hacer referencia a como "customers". Esto coincide con las convenciones de nomenclatura en muchas bases de datos, incluidos SQL del servidor de SQL Server, el comportamiento predeterminado es que los nombres de elementos de datos no pueden distinguirse sólo por caso.  
  
> [!NOTE]
>  A diferencia de conjuntos de datos, documentos XML distinguen mayúsculas de minúsculas, por lo que los nombres de elementos de datos definidos en esquemas distinguen mayúsculas de minúsculas. Por ejemplo, el protocolo de esquema permite el esquema definir una tabla denominada "Clientes" y otra tabla denominada a "customers". Esto puede producir conflictos de nombres cuando se usa un esquema que contiene elementos que difieran solo por caso para generar una clase de conjunto de datos.  
  
 Mayúsculas y minúsculas, sin embargo, pueden ser un factor en cómo interpretar los datos del conjunto de datos. Por ejemplo, si filtra los datos en una tabla de conjunto de datos, los criterios de búsqueda podrían devolver resultados diferentes dependiendo de si la comparación distingue entre mayúsculas y minúsculas. Puede controlar las mayúsculas y minúsculas de filtrado, búsqueda y ordenación mediante el establecimiento del conjunto de datos <xref:System.Data.DataSet.CaseSensitive%2A> propiedad. Todas las tablas del conjunto de datos heredan el valor de esta propiedad de forma predeterminada. (Puede invalidar esta propiedad para cada tabla individual mediante el establecimiento de la tabla <xref:System.Data.DataTable.CaseSensitive%2A> propiedad.)  
  
## <a name="locate-a-specific-row-in-a-data-table"></a>Buscar una fila específica en una tabla de datos  
  
#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Para buscar una fila en un dataset con tipo con un valor de clave principal  
  
-   Para buscar una fila, llame a fuertemente tipado `FindBy` método que usa la clave principal de la tabla.  
  
     En el ejemplo siguiente, la `CustomerID` columna es la clave principal de la `Customers` tabla. Esto significa que el generado `FindBy` método es `FindByCustomerID`. En el ejemplo se muestra cómo asignar un determinado <xref:System.Data.DataRow> a una variable mediante el uso de generado `FindBy` método.  
  
     [!code-csharp[VbRaddataEditing#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#18)]
     [!code-vb[VbRaddataEditing#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#18)]  
  
#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Para buscar una fila en un conjunto de datos sin tipo con un valor de clave principal  
  
-   Llame a la <xref:System.Data.DataRowCollection.Find%2A> método de un <xref:System.Data.DataRowCollection> colección, pasando la clave principal como un parámetro.  
  
     El ejemplo siguiente muestra cómo declarar una nueva fila denominada `foundRow` y asignarle el valor devuelto de la <xref:System.Data.DataRowCollection.Find%2A> método. Si se encuentra la clave principal, el contenido del índice de columna 1 se muestra en un cuadro de mensaje.  
  
     [!code-csharp[VbRaddataEditing#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#19)]
     [!code-vb[VbRaddataEditing#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#19)]  
  
## <a name="findrows-by-column-values"></a>FindRows por valores de columna  
  
#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Para buscar filas en función de los valores de cualquier columna  
  
-   Las tablas de datos se crean con el<xref:System.Data.DataTable.Select%2A> método, que devuelve una matriz de <xref:System.Data.DataRow>s según la expresión que se pasa a la <xref:System.Data.DataTable.Select%2A> método. Para obtener más información sobre la creación de expresiones válidas, vea la sección "Sintaxis de expresión" de la página la <xref:System.Data.DataColumn.Expression%2A> propiedad.  
  
     El ejemplo siguiente muestra cómo usar el <xref:System.Data.DataTable.Select%2A> método de la <xref:System.Data.DataTable> localizar filas específicas.  
  
     [!code-csharp[VbRaddataEditing#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#20)]
     [!code-vb[VbRaddataEditing#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#20)]  
  
## <a name="accessrelated-records"></a>Registros de Accessrelated  
 Cuando están relacionadas las tablas en un conjunto de datos, un <xref:System.Data.DataRelation> objeto puede disponer de los registros relacionados en otra tabla. Por ejemplo, un conjunto de datos que contiene `Customers` y `Orders` tablas pueden estar disponibles.  
  
 Puede usar un <xref:System.Data.DataRelation> objeto para buscar registros relacionados mediante una llamada a la <xref:System.Data.DataRow.GetChildRows%2A> método de un <xref:System.Data.DataRow> en la tabla primaria. Este método devuelve una matriz de registros secundarios relacionados. O bien puede llamar el <xref:System.Data.DataRow.GetParentRow%2A> método de un <xref:System.Data.DataRow> en la tabla secundaria. Este método devuelve un único <xref:System.Data.DataRow> de la tabla primaria.  
  
 Esta página ofrece ejemplos de uso de conjuntos de datos con tipo. Para obtener información sobre la navegación por relaciones en conjuntos de datos sin tipo, vea [navegar por objetos DataRelation](http://msdn.microsoft.com/library/e5e673f4-9b44-45ae-aaea-c504d1cc5d3e).  
  
> [!NOTE]
>  Si está trabajando en una aplicación de Windows Forms y con las características de enlace de datos para mostrar los datos, el formulario generado por el diseñador puede proporcionar suficiente funcionalidad para la aplicación. Para obtener más información, consulte [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). En concreto, consulte[Cómo: mostrar datos relacionados en una aplicación de Windows Forms](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md) y [Tutorial: mostrar datos relacionados en un formulario Windows Forms](../data-tools/walkthrough-displaying-related-data-on-a-windows-form.md).  
  
 Ejemplos de código siguientes muestran cómo desplazarse arriba y abajo de las relaciones en conjuntos de datos con tipo. El uso de ejemplos de código escrito <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) y el generado `FindBy` *PrimaryKey* (`FindByCustomerID`) métodos para buscar una fila deseada y devolver los registros relacionados. Los ejemplos de compilación y ejecutan correctamente solo si tiene:  
  
- Una instancia de un conjunto de datos denominado `NorthwindDataSet` con un `Customers` tabla.  
  
- Un `Orders` tabla.  
  
- Una relación llamada `FK_Orders_Customers`relacionados con las dos tablas disponibles en el ámbito del código  
  
  Además, ambas tablas deben rellenarse con datos de cualquier registro que se va a devolver.  
  
#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Para devolver los registros de un registro primario seleccionado  
  
-   Llame a la <xref:System.Data.DataRow.GetChildRows%2A> método de un determinado `Customers` datos de fila y devolver una matriz de filas de la `Orders` tabla:  
  
     [!code-csharp[VbRaddataDatasets#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDatasets#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#6)]  
  
#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Para devolver el registro primario de un registro secundario seleccionado  
  
-   Llame a la <xref:System.Data.DataRow.GetParentRow%2A> método de un determinado `Orders` fila de datos y devolver una sola fila de la `Customers` tabla:  
  
     [!code-csharp[VbRaddataDatasets#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDatasets#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#7)]

