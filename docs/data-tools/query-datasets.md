---
title: Consultar conjuntos de datos
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4ef1c806914b0f134702e010b58229ee3fc15c7a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281869"
---
# <a name="query-datasets"></a>Consultar conjuntos de datos
Para buscar registros específicos en un conjunto de registros, use el `FindBy` método en DataTable, escriba su propia instrucción foreach para recorrer la colección de filas de la tabla o use [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

## <a name="dataset-case-sensitivity"></a>Distinción de mayúsculas y minúsculas
Dentro de un conjunto de DataSet, los nombres de tabla y de columna no distinguen mayúsculas de minúsculas de forma predeterminada, es decir, una tabla de un conjunto de información denominada "Customers" también puede denominarse "Customers". Esto coincide con las convenciones de nomenclatura de muchas bases de datos, incluidas SQL Server. En SQL Server, el comportamiento predeterminado es que los nombres de los elementos de datos no se pueden distinguir solo por el uso de mayúsculas o minúsculas.

> [!NOTE]
> A diferencia de los conjuntos de datos, los documentos XML distinguen mayúsculas de minúsculas, por lo que los nombres de los elementos de datos definidos en esquemas distinguen mayúsculas de minúsculas. Por ejemplo, el protocolo de esquema permite que el esquema defina una tabla denominada "Customers" y otra tabla denominada "Customers". Esto puede dar lugar a conflictos de nombres cuando se utiliza un esquema que contiene elementos que solo se diferencian por el uso de mayúsculas y minúsculas para generar una clase de conjunto de resultados.

Sin embargo, la distinción entre mayúsculas y minúsculas puede ser un factor de cómo se interpretan los datos en el conjunto de datos. Por ejemplo, si filtra los datos en una tabla de conjunto de datos, los criterios de búsqueda podrían devolver resultados diferentes en función de si la comparación distingue entre mayúsculas y minúsculas. Puede controlar la distinción de mayúsculas y minúsculas del filtrado, la búsqueda y la ordenación estableciendo la propiedad del conjunto de valores <xref:System.Data.DataSet.CaseSensitive%2A> . Todas las tablas del conjunto de valores heredan el valor de esta propiedad de forma predeterminada. (Puede invalidar esta propiedad para cada tabla individual estableciendo la propiedad de la tabla <xref:System.Data.DataTable.CaseSensitive%2A> ).

## <a name="locate-a-specific-row-in-a-data-table"></a>Buscar una fila específica en una tabla de datos

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Para buscar una fila en un conjunto de tipos con un valor de clave principal

- Para buscar una fila, llame al método fuertemente tipado `FindBy` que usa la clave principal de la tabla.

     En el ejemplo siguiente, la `CustomerID` columna es la clave principal de la `Customers` tabla. Esto significa que el `FindBy` método generado es `FindByCustomerID` . En el ejemplo se muestra cómo asignar un específico <xref:System.Data.DataRow> a una variable mediante el `FindBy` método generado.

     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Para buscar una fila en un conjunto de filas sin tipo con un valor de clave principal

- Llame al <xref:System.Data.DataRowCollection.Find%2A> método de una <xref:System.Data.DataRowCollection> colección, pasando la clave principal como parámetro.

     En el ejemplo siguiente se muestra cómo declarar una nueva fila denominada `foundRow` y asignarle el valor devuelto del <xref:System.Data.DataRowCollection.Find%2A> método. Si se encuentra la clave principal, el contenido del índice de columna 1 se muestra en un cuadro de mensaje.

     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]

## <a name="find-rows-by-column-values"></a>Buscar filas por valores de columna

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Para buscar filas basadas en los valores de una columna

- Las tablas de datos se crean con el <xref:System.Data.DataTable.Select%2A> método, que devuelve una matriz de <xref:System.Data.DataRow> s basándose en la expresión pasada al <xref:System.Data.DataTable.Select%2A> método. Para obtener más información sobre la creación de expresiones válidas, vea la sección "Sintaxis de expresiones" de la página sobre la <xref:System.Data.DataColumn.Expression%2A> propiedad.

     En el ejemplo siguiente se muestra cómo utilizar el <xref:System.Data.DataTable.Select%2A> método de <xref:System.Data.DataTable> para buscar filas específicas.

     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]

## <a name="access-related-records"></a>Acceder a los registros relacionados
Cuando las tablas de un conjunto de registros están relacionadas, un <xref:System.Data.DataRelation> objeto puede hacer que los registros relacionados estén disponibles en otra tabla. Por ejemplo, un conjunto de DataSet que contiene `Customers` `Orders` tablas y puede estar disponible.

Puede utilizar un <xref:System.Data.DataRelation> objeto para buscar registros relacionados llamando al <xref:System.Data.DataRow.GetChildRows%2A> método de <xref:System.Data.DataRow> en la tabla primaria. Este método devuelve una matriz de registros secundarios relacionados. O bien, puede llamar al <xref:System.Data.DataRow.GetParentRow%2A> método de un <xref:System.Data.DataRow> en la tabla secundaria. Este método devuelve un único <xref:System.Data.DataRow> de la tabla primaria.

En esta página se proporcionan ejemplos de uso de conjuntos de DataSet con tipo. Para obtener información sobre cómo navegar por las relaciones en conjuntos de datos sin tipo, vea [explorar objetos DataRelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).

> [!NOTE]
> Si está trabajando en una aplicación Windows Forms y usa las características de enlace de datos para mostrar los datos, el formulario generado por el diseñador podría proporcionar la funcionalidad suficiente para la aplicación. Para obtener más información, vea [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). En concreto, vea [relaciones en conjuntos de valores](relationships-in-datasets.md).

En los siguientes ejemplos de código se muestra cómo desplazarse por las relaciones hacia arriba y hacia abajo en conjuntos de tipos de DataSet. En los ejemplos de código se usan tipos <xref:System.Data.DataRow> s ( `NorthwindDataSet.OrdersRow` ) y los métodos FindBy*PrimaryKey* () generados `FindByCustomerID` para buscar una fila deseada y devolver los registros relacionados. Los ejemplos se compilan y ejecutan correctamente solo si tiene:

- Instancia de un conjunto de información denominado `NorthwindDataSet` con una `Customers` tabla.

- Una `Orders` tabla.

- Relación denominada `FK_Orders_Customers` que relaciona las dos tablas.

Además, ambas tablas deben rellenarse con datos para que se devuelvan los registros.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Para devolver los registros secundarios de un registro primario seleccionado

- Llame al <xref:System.Data.DataRow.GetChildRows%2A> método de una `Customers` fila de datos específica y devuelva una matriz de filas de la `Orders` tabla:

     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Para devolver el Registro primario de un registro secundario seleccionado

- Llame al <xref:System.Data.DataRow.GetParentRow%2A> método de una `Orders` fila de datos específica y devuelva una sola fila de la `Customers` tabla:

     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>Consulte también

- [Herramientas de conjunto de herramientas en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
