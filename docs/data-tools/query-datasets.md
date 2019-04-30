---
title: Consultar conjuntos de datos
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: bec1c878dce59ccb5444d74ba0255c9ceb705780
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402737"
---
# <a name="query-datasets"></a>Consultar conjuntos de datos
Para buscar registros específicos de un conjunto de datos, use el `FindBy` método en la tabla de datos, escribir su propia instrucción foreach para recorrer la colección de filas de la tabla, o use [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

## <a name="dataset-case-sensitivity"></a>Conjunto de datos entre mayúsculas y minúsculas
Dentro de un conjunto de datos, los nombres de columna y tabla distinguen mayúsculas de minúsculas de forma predeterminada, es decir, una tabla en un conjunto de datos denominado "Customers" también se puede hacer referencia a como "customers". Esto coincide con las convenciones de nomenclatura en muchas bases de datos, incluido SQL Server. En SQL Server, el comportamiento predeterminado es que los nombres de elementos de datos no pueden distinguirse sólo por caso.

> [!NOTE]
> A diferencia de conjuntos de datos, documentos XML distinguen mayúsculas de minúsculas, por lo que los nombres de elementos de datos definidos en esquemas distinguen mayúsculas de minúsculas. Por ejemplo, el protocolo de esquema permite el esquema definir una tabla denominada "Clientes" y otra tabla denominada a "customers". Esto puede producir conflictos de nombres cuando se usa un esquema que contiene elementos que difieran solo por caso para generar una clase de conjunto de datos.

Mayúsculas y minúsculas, sin embargo, pueden ser un factor en cómo interpretar los datos del conjunto de datos. Por ejemplo, si filtra los datos en una tabla de conjunto de datos, los criterios de búsqueda podrían devolver resultados diferentes dependiendo de si la comparación distingue entre mayúsculas y minúsculas. Puede controlar las mayúsculas y minúsculas de filtrado, búsqueda y ordenación mediante el establecimiento del conjunto de datos <xref:System.Data.DataSet.CaseSensitive%2A> propiedad. Todas las tablas del conjunto de datos heredan el valor de esta propiedad de forma predeterminada. (Puede invalidar esta propiedad para cada tabla individual mediante el establecimiento de la tabla <xref:System.Data.DataTable.CaseSensitive%2A> propiedad.)

## <a name="locate-a-specific-row-in-a-data-table"></a>Buscar una fila específica en una tabla de datos

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Para buscar una fila en un dataset con tipo con un valor de clave principal

- Para buscar una fila, llame a fuertemente tipado `FindBy` método que usa la clave principal de la tabla.

     En el ejemplo siguiente, la `CustomerID` columna es la clave principal de la `Customers` tabla. Esto significa que el generado `FindBy` método es `FindByCustomerID`. En el ejemplo se muestra cómo asignar un determinado <xref:System.Data.DataRow> a una variable mediante el uso de generado `FindBy` método.

     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Para buscar una fila en un conjunto de datos sin tipo con un valor de clave principal

- Llame a la <xref:System.Data.DataRowCollection.Find%2A> método de un <xref:System.Data.DataRowCollection> colección, pasando la clave principal como un parámetro.

     El ejemplo siguiente muestra cómo declarar una nueva fila denominada `foundRow` y asignarle el valor devuelto de la <xref:System.Data.DataRowCollection.Find%2A> método. Si se encuentra la clave principal, el contenido del índice de columna 1 se muestra en un cuadro de mensaje.

     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]

## <a name="find-rows-by-column-values"></a>Buscar filas por valores de columna

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Para buscar filas en función de los valores de cualquier columna

- Las tablas de datos se crean con el <xref:System.Data.DataTable.Select%2A> método, que devuelve una matriz de <xref:System.Data.DataRow>s según la expresión que se pasa a la <xref:System.Data.DataTable.Select%2A> método. Para obtener más información sobre la creación de expresiones válidas, vea la sección "Sintaxis de expresión" de la página la <xref:System.Data.DataColumn.Expression%2A> propiedad.

     El ejemplo siguiente muestra cómo usar el <xref:System.Data.DataTable.Select%2A> método de la <xref:System.Data.DataTable> localizar filas específicas.

     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]

## <a name="access-related-records"></a>Acceso a registros relacionados
Cuando están relacionadas las tablas en un conjunto de datos, un <xref:System.Data.DataRelation> objeto puede disponer de los registros relacionados en otra tabla. Por ejemplo, un conjunto de datos que contiene `Customers` y `Orders` tablas pueden estar disponibles.

Puede usar un <xref:System.Data.DataRelation> objeto para buscar registros relacionados mediante una llamada a la <xref:System.Data.DataRow.GetChildRows%2A> método de un <xref:System.Data.DataRow> en la tabla primaria. Este método devuelve una matriz de registros secundarios relacionados. O bien, puede llamar el <xref:System.Data.DataRow.GetParentRow%2A> método de un <xref:System.Data.DataRow> en la tabla secundaria. Este método devuelve un único <xref:System.Data.DataRow> de la tabla primaria.

Esta página ofrece ejemplos de uso de conjuntos de datos con tipo. Para obtener información sobre la navegación por relaciones en conjuntos de datos sin tipo, vea [navegar por objetos DataRelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).

> [!NOTE]
> Si está trabajando en una aplicación de Windows Forms y con las características de enlace de datos para mostrar los datos, el formulario generado por el diseñador puede proporcionar suficiente funcionalidad para la aplicación. Para obtener más información, consulte [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). En concreto, consulte [relaciones en conjuntos de datos](relationships-in-datasets.md).

Ejemplos de código siguientes muestran cómo desplazarse arriba y abajo de las relaciones en conjuntos de datos con tipo. El uso de ejemplos de código escrito <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) y el generado FindBy*PrimaryKey* (`FindByCustomerID`) métodos para buscar una fila deseada y devolver los registros relacionados. Los ejemplos de compilación y ejecutan correctamente solo si tiene:

- Una instancia de un conjunto de datos denominado `NorthwindDataSet` con un `Customers` tabla.

- Un `Orders` tabla.

- Una relación llamada `FK_Orders_Customers`relacionados con las dos tablas.

Además, ambas tablas deben rellenarse con datos de cualquier registro que se va a devolver.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Para devolver los registros de un registro primario seleccionado

- Llame a la <xref:System.Data.DataRow.GetChildRows%2A> método de un determinado `Customers` datos de fila y devolver una matriz de filas de la `Orders` tabla:

     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Para devolver el registro primario de un registro secundario seleccionado

- Llame a la <xref:System.Data.DataRow.GetParentRow%2A> método de un determinado `Orders` fila de datos y devolver una sola fila de la `Customers` tabla:

     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>Vea también

- [Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)