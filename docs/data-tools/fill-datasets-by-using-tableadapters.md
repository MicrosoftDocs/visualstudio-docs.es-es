---
title: Rellenar conjuntos de datos mediante TableAdapters
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a79f7b781944bb93a60794e748eefb9375723384
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301198"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Rellenar conjuntos de datos mediante TableAdapters

Un componente TableAdapter rellena un conjunto de datos con datos de la base de datos, en función de una o varias consultas o procedimientos almacenados que especifique. TableAdapters también puede realizar agregaciones, actualizaciones y eliminaciones en la base de datos para conservar los cambios que realice en el conjunto de datos. También puede emitir comandos globales que no estén relacionados con ninguna tabla específica.

> [!NOTE]
> TableAdapters son generados por los diseñadores de Visual Studio. Si va a crear conjuntos de datos mediante programación, use DataAdapter, que es una clase .NET.

Para obtener información detallada acerca de las operaciones de TableAdapter, puede saltar directamente a uno de estos temas:

|Tema|Descripción|
|-----------|-----------------|
|[Crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md)|Cómo utilizar los diseñadores para crear y configurar TableAdapters|
|[Crear consultas parametrizadas de TableAdapter](../data-tools/create-parameterized-tableadapter-queries.md)|Cómo permitir a los usuarios proporcionar argumentos a procedimientos o consultas de TableAdapter|
|[Obtener acceso directamente a la base de datos con un TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Cómo utilizar los métodos Dbdirect de TableAdapters|
|[Desactivar restricciones al llenar un conjunto de datos](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Cómo trabajar con restricciones de clave externa al actualizar datos|
|[Cómo extender la funcionalidad de un TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Cómo agregar código personalizado a TableAdapters|
|[Leer datos XML en un conjunto de datos](../data-tools/read-xml-data-into-a-dataset.md)|Cómo trabajar con XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>Introducción a TableAdapter

TableAdapters son componentes generados por el diseñador que se conectan a una base de datos, ejecutan consultas o procedimientos almacenados y rellenan su DataTable con los datos devueltos. TableAdapters también envían datos actualizados desde la aplicación a la base de datos. Puede ejecutar tantas consultas como desee en un TableAdapter siempre que devuelvan datos que se ajusten al esquema de la tabla con la que está asociado TableAdapter. En el diagrama siguiente se muestra cómo TableAdapters interactúan con bases de datos y otros objetos en la memoria:

![Flujo de datos de una aplicación cliente](../data-tools/media/clientdatadiagram.gif)

Mientras que TableAdapters se diseñan con el **Diseñador de conjuntos**de datos , las clases TableAdapter no se generan como clases anidadas de <xref:System.Data.DataSet>. Se encuentran en espacios de nombres independientes que son específicos de cada conjunto de datos. Por ejemplo, si tiene `NorthwindDataSet`un conjunto de datos denominado <xref:System.Data.DataTable>, `NorthwindDataSet` los TableAdapters que están asociados con s en el estaría en el `NorthwindDataSetTableAdapters` espacio de nombres. Para tener acceso a un TableAdapter determinado mediante programación, debe declarar una nueva instancia del TableAdapter. Por ejemplo:

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Esquema de DataTable asociado

Cuando se crea un TableAdapter, se usa la consulta inicial o el <xref:System.Data.DataTable>procedimiento almacenado para definir el esquema del archivo . Ejecute esta consulta inicial o procedimiento almacenado llamando `Fill` al método del TableAdapter (que rellena el TableAdapter asociado). <xref:System.Data.DataTable> Los cambios realizados en la consulta principal del TableAdapter se reflejan en el esquema de la tabla de datos asociada. Por ejemplo, al quitar una columna de la consulta principal también se quita la columna de la tabla de datos asociada. Si alguna consulta adicional en el TableAdapter usa instrucciones SQL que devuelven columnas que no están en la consulta principal, el diseñador intenta sincronizar los cambios de columna entre la consulta principal y las consultas adicionales.

## <a name="tableadapter-update-commands"></a>Comandos de actualización de TableAdapter

La funcionalidad de actualización de un TableAdapter depende de la cantidad de información disponible en la consulta principal en el **Asistente para TableAdapter**. Por ejemplo, TableAdapters que están configurados para `JOIN`capturar valores de varias tablas (mediante un ), valores escalares, vistas o los resultados de funciones de agregado no se crean inicialmente con la capacidad de enviar actualizaciones de nuevo a la base de datos subyacente. Sin embargo, `INSERT`puede `UPDATE`configurar `DELETE` los comandos , , y manualmente en la ventana **Propiedades.**

## <a name="tableadapter-queries"></a>consultas TableAdapter

![TableAdapter con múltiples consultas](../data-tools/media/tableadapter.gif)

TableAdapters puede contener varias consultas para rellenar sus tablas de datos asociadas. Puede definir tantas consultas para un TableAdapter como requiera la aplicación, con tal de que cada consulta devuelva datos que cumplan el mismo esquema que la tabla de datos asociada. Esta capacidad permite a un TableAdapter cargar resultados diferentes en función de criterios diferentes.

Por ejemplo, si la aplicación contiene una tabla con nombres de cliente, puede crear una consulta que llene la tabla con cada nombre de cliente que comience con una letra determinada y otra que llene la tabla con todos los clientes que se encuentran en el mismo estado. Para rellenar `Customers` una tabla con clientes en `FillByState` un estado determinado, puede crear una `SELECT * FROM Customers WHERE State = @State`consulta que tome un parámetro para el valor de estado de la siguiente manera: . Ejecute la consulta llamando `FillByState` al método y pasando el `CustomerTableAdapter.FillByState("WA")`valor del parámetro de la siguiente manera: .

Además de agregar consultas que devuelven datos del mismo esquema que la tabla de datos de TableAdapter, puede agregar consultas que devuelven valores escalares (únicos). Por ejemplo, una consulta que devuelve`SELECT Count(*) From Customers`un recuento `CustomersTableAdapter,` de clientes ( ) es válida para a aunque los datos que se devuelven no se ajustan al esquema de la tabla.

## <a name="clearbeforefill-property"></a>Propiedad ClearBeforeFill

De forma predeterminada, cada vez que se ejecuta una consulta para rellenar la tabla de datos de un TableAdapter, se borran los datos existentes y solo se cargan los resultados de la consulta en la tabla. Establezca la propiedad `ClearBeforeFill` de `false` TableAdapter en si desea agregar o combinar los datos que se devuelven de una consulta a los datos existentes en una tabla de datos. Independientemente de si borra los datos, debe enviar explícitamente las actualizaciones a la base de datos, si desea conservarlas. Por lo tanto, recuerde guardar los cambios en los datos de la tabla antes de ejecutar otra consulta que llene la tabla. Para obtener más información, vea [Actualizar datos mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>Herencia de TableAdapter

TableAdapters amplían la funcionalidad de los adaptadores <xref:System.Data.Common.DataAdapter> de datos estándar encapsulando una clase configurada. De forma predeterminada, el TableAdapter hereda de la <xref:System.ComponentModel.Component> <xref:System.Data.Common.DataAdapter> clase y no se puede convertir a la clase. La conversión de <xref:System.Data.Common.DataAdapter> un TableAdapter a la clase produce un <xref:System.InvalidCastException> error. Para cambiar la clase base de un TableAdapter, puede <xref:System.ComponentModel.Component> especificar una clase que deriva de la **clase base** propiedad de la TableAdapter en el **Diseñador de conjuntos**de datos .

## <a name="tableadapter-methods-and-properties"></a>Métodos y propiedades de TableAdapter

La clase TableAdapter no es un tipo .NET. Esto significa que no puede buscarlo en la documentación o en el **Examinador de objetos.** Se crea en tiempo de diseño cuando se utiliza uno de los asistentes mencionados anteriormente. El nombre que se asigna a un TableAdapter al crearlo se basa en el nombre de la tabla con la que está trabajando. Por ejemplo, al crear un TableAdapter basado en `Orders`una tabla de `OrdersTableAdapter`una base de datos denominada , el TableAdapter se denomina . Se puede cambiar el nombre de clase del TableAdapter utilizando la propiedad **Name** en el **Diseñador de DataSet**.

A continuación se muestran los métodos y propiedades más utilizados de TableAdapters:

|Member|Descripción|
|------------|-----------------|
|`TableAdapter.Fill`|Rellena la tabla de datos asociada de TableAdapter con `SELECT` los resultados del comando de TableAdapter.|
|`TableAdapter.Update`|Devuelve los cambios a la base de datos y devuelve un entero que representa el número de filas afectadas por la actualización. Para obtener más información, vea [Actualizar datos mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Devuelve un <xref:System.Data.DataTable> nuevo que está lleno de datos.|
|`TableAdapter.Insert`|Crea una nueva fila en la tabla de datos. Para obtener más información, consulte [Insertar nuevos registros en una base](../data-tools/insert-new-records-into-a-database.md)de datos.|
|`TableAdapter.ClearBeforeFill`|Determina si se vacía una tabla de datos antes de llamar a uno de los métodos `Fill`.|

## <a name="tableadapter-update-method"></a>Método de actualización de TableAdapter

Los TableAdapter utilizan comandos de datos para leer y escribir en la base de datos. Utilice la consulta inicial `Fill` (principal) del TableAdapter como base para crear el esquema `InsertCommand` `UpdateCommand`de `DeleteCommand` la tabla de `TableAdapter.Update` datos asociada, así como los comandos , y que están asociados con el método. Al llamar al `Update` método de un TableAdapter, se ejecutan las instrucciones que se crearon cuando se configuró originalmente TableAdapter, no una de las consultas adicionales que agregó con el Asistente para configuración de consultas de **TableAdapter**.

Cuando se usa un TableAdapter, realiza eficazmente las mismas operaciones con los comandos que normalmente realizaría. Por ejemplo, cuando se llama `Fill` al método del adaptador, `SelectCommand` el adaptador ejecuta el comando <xref:System.Data.SqlClient.SqlDataReader>de datos en su propiedad y utiliza un lector de datos (por ejemplo, ) para cargar el conjunto de resultados en la tabla de datos. De forma similar, cuando `Update` se llama al método del `UpdateCommand`adaptador, se ejecuta el comando adecuado (en las propiedades , `InsertCommand`, y) `DeleteCommand` para cada registro modificado en la tabla de datos.

> [!NOTE]
> Si hay bastante información en la consulta principal, se crean los comandos `InsertCommand`, `UpdateCommand` y `DeleteCommand` de manera predeterminada cuando se genera el TableAdapter. Si la consulta principal del TableAdapter es `SELECT` más que una sola instrucción de tabla, `UpdateCommand`es `DeleteCommand`posible que el diseñador no pueda generar `InsertCommand`, , y . Si no se generan estos comandos, es posible `TableAdapter.Update` que reciba un error al ejecutar el método.

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods

Además `InsertCommand` `UpdateCommand`de `DeleteCommand`, , y , TableAdapters se crean con métodos que se pueden ejecutar directamente en la base de datos. Puede llamar a`TableAdapter.Insert`estos `TableAdapter.Update`métodos ( , , y `TableAdapter.Delete`) directamente para manipular los datos de la base de datos. Esto significa que puede llamar a estos `TableAdapter.Update` métodos individuales desde el código en lugar de llamar para controlar las inserciones, actualizaciones y eliminaciones que están pendientes para la tabla de datos asociada.

Si no desea crear estos métodos directos, establezca el TableAdapter `false` **GenerateDbDirectMethods** propiedad (en el **propiedades** ventana). Las consultas adicionales que se agregan al TableAdapter son consultas independientes: no generan estos métodos.

## <a name="tableadapter-support-for-nullable-types"></a>Compatibilidad del objeto TableAdapter con los tipos que aceptan valores NULL

TableAdapters admiten `Nullable(Of T)` tipos `T?`que aceptan valores NULL y . Para más información sobre los tipos que aceptan valores NULL en Visual Basic, vea [Tipos que admiten valores null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Para obtener más información acerca de los tipos que aceptan valores NULL en C, vea [Usar tipos que aceptan valores NULL](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>Referencia de TableAdapterManager

De forma predeterminada, una clase TableAdapterManager genera al crear un conjunto de datos que contiene tablas relacionadas. Para evitar que se genere la clase, `Hierarchical Update` cambie el valor de la propiedad del conjunto de datos a false. Al arrastrar una tabla que tiene una relación a la superficie de diseño de un formulario Windows Forms o WPFWPF página, Visual Studio declara una variable miembro de la clase. Si no usa el enlace de datos, debe declarar manualmente la variable.

La clase TableAdapterManager no es un tipo .NET. Por lo tanto, no puede buscarlo en la documentación. Se crea en tiempo de diseño como parte del proceso de creación del conjunto de datos.

Los siguientes son los métodos y `TableAdapterManager` propiedades utilizados con frecuencia de la clase:

|Member|Descripción|
|------------|-----------------|
|Método `UpdateAll`|Guarda todos los datos de todas las tablas de datos.|
|Propiedad `BackUpDataSetBeforeUpdate`|Determina si se debe crear una copia de `TableAdapterManager.UpdateAll` seguridad del conjunto de datos antes de ejecutar el método. Booleana.|
|Propiedad *tableName* `TableAdapter`|Representa un TableAdapter. El TableAdapterManager generado contiene una `TableAdapter` propiedad para cada uno que administra. Por ejemplo, un conjunto de datos con un Customers `CustomersTableAdapter` and `OrdersTableAdapter` Orders tabla genera con un TableAdapterManager que contiene y propiedades.|
|Propiedad `UpdateOrder`|Controla el orden de los comandos individuales de inserción, actualización y eliminación. Establezca este valor en uno `TableAdapterManager.UpdateOrderOption` de los valores de la enumeración.<br /><br /> De forma `UpdateOrder` predeterminada, se establece en **InsertUpdateDelete**. Esto significa que las inserciones, las actualizaciones y, a continuación, las eliminaciones se realizan para todas las tablas del conjunto de datos.|

## <a name="security"></a>Seguridad

Cuando utilice comandos de datos con <xref:System.Data.CommandType.Text>una propiedad CommandType establecida en , compruebe cuidadosamente la información que se envía desde un cliente antes de pasarla a la base de datos. Usuarios con malas intenciones podrían intentar enviar (inyectar) instrucciones de SQL modificadas o adicionales con el fin de obtener acceso no autorizado o dañar la base de datos. Antes de transferir la entrada del usuario a una base de datos, compruebe siempre que la información es válida. Una práctica recomendada es usar siempre consultas parametrizadas o procedimientos almacenados cuando sea posible.

## <a name="see-also"></a>Consulte también

- [Herramientas de conjunto de datos](../data-tools/dataset-tools-in-visual-studio.md)
