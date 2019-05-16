---
title: Llenar conjuntos de datos mediante TableAdapters | Documentos de Microsoft
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
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fb06c1d97c854aae05d993c086069e10e35518f5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704980"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Rellenar conjuntos de datos mediante TableAdapters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un componente de TableAdapter rellena un dataset con los datos de la base de datos, en función de una o varias consultas o procedimientos almacenados que especifique. También puede llevar a cabo los TableAdapters agrega, actualiza y elimina la base de datos para conservar los cambios realizados en el conjunto de datos. También puede emitir comandos globales que están relacionados con una tabla específica.  
  
> [!NOTE]
> Los TableAdapters son generados por los diseñadores de Visual Studio. Si va a crear conjuntos de datos mediante programación, a continuación, usar DataAdapter, que es una clase de .NET Framework.  
  
 Para obtener información detallada acerca de las operaciones de TableAdapter, puede ir directamente a uno de estos temas:  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md)|Cómo utilizar los diseñadores para crear y configurar TableAdapters|  
|[Crear consultas parametrizadas de TableAdapter](../data-tools/create-parameterized-tableadapter-queries.md)|Cómo habilitar usuarios proporcionar argumentos a las consultas o procedimientos de TableAdapter|  
|[Obtener acceso directamente a la base de datos con un TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Cómo usar los métodos Dbdirect de TableAdapter|  
|[Desactivar restricciones al llenar un conjunto de datos](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Cómo trabajar con restricciones foreign key durante la actualización de datos|  
|[Cómo extender la funcionalidad de un TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Cómo agregar código personalizado a los TableAdapters|  
|[Leer datos XML en un conjunto de datos](../data-tools/read-xml-data-into-a-dataset.md)|Cómo trabajar con XML|  
  
## <a name="tableadapters-overview"></a>Información general de TableAdapters  
 Los TableAdapters son componentes generados por diseñador que se conectan a una base de datos, ejecutar consultas o procedimientos almacenados y completar su DataTable con los datos devueltos. Los TableAdapters también enviar datos actualizados desde la aplicación a la base de datos. Puede ejecutar tantas consultas como desee en un TableAdapter, siempre se devuelven los datos que se ajustan al esquema de la tabla que está asociado al TableAdapter. El siguiente diagrama muestra cómo interactúan los TableAdapters con bases de datos y otros objetos en memoria:  
  
 ![Flujo de datos en una aplicación cliente](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Aunque los TableAdapters están diseñados con la **Diseñador de Dataset**, las clases TableAdapter no se generan como clases anidadas de <xref:System.Data.DataSet>. Se encuentran en espacios de nombres independientes que son específicas de cada conjunto de datos. Por ejemplo, si tiene un conjunto de datos denominado `NorthwindDataSet`, los TableAdapters asociadas <xref:System.Data.DataTable>s en el `NorthwindDataSet` estaría en el `NorthwindDataSetTableAdapters` espacio de nombres. Para tener acceso a un TableAdapter determinado mediante programación, debe declarar una nueva instancia del TableAdapter. Por ejemplo:  
  
 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]  
  
## <a name="associated-datatable-schema"></a>Esquema de DataTable asociado  
 Al crear un TableAdapter, utilice la consulta inicial o procedimiento almacenado para definir el esquema del TableAdapter asociado a la <xref:System.Data.DataTable>. Ejecute esta consulta inicial o procedimiento almacenado mediante una llamada del TableAdapter `Fill` método (que rellena el TableAdapter asociado <xref:System.Data.DataTable>). Los cambios realizados en la consulta principal del TableAdapter se reflejan en el esquema de la tabla de datos asociada. Por ejemplo, al quitar una columna de la consulta principal también quita la columna de la tabla de datos asociados. Si alguna consulta adicional del TableAdapter utiliza instrucciones SQL que devuelven columnas que no están en la consulta principal, el diseñador intenta sincronizar los cambios de columna entre la consulta principal y las consultas adicionales. Para obtener más información, vea [Cómo: Editar TableAdapters](https://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
## <a name="tableadapter-update-commands"></a>Comandos de actualización de TableAdapter  
 La funcionalidad de actualización de un objeto TableAdapter depende de la cantidad de información está disponible en la consulta principal en el Asistente de TableAdapter. Por ejemplo, los TableAdapter configurados para obtener valores de varias tablas (consultas JOIN), valores escalares, vistas o los resultados de funciones de agregado no se crean inicialmente con la capacidad de enviar actualizaciones a la base de datos subyacente. Sin embargo, puede configurar los comandos INSERT, UPDATE y DELETE manualmente en el **propiedades** ventana.  
  
## <a name="tableadapter-queries"></a>consultas TableAdapter  
 ![TableAdapter con varias consultas](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Los TableAdapter pueden contener varias consultas que rellenan las tablas de datos asociados. Puede definir tantas consultas para un TableAdapter como requiera la aplicación, con tal de que cada consulta devuelva datos que cumplan el mismo esquema que la tabla de datos asociada. Esta función se habilita un TableAdapter cargar los resultados diferentes según distintos criterios.  
  
 Por ejemplo, si la aplicación contiene una tabla con los nombres de cliente, puede crear una consulta que rellena la tabla con todos los nombres de cliente comienza con una letra determinada y otra que rellena la tabla con todos los clientes que se encuentran en el mismo estado. Para rellenar un `Customers` tabla con los clientes en un estado determinado, puede crear un `FillByState` consulta que toma un parámetro para el valor de estado como sigue: `SELECT * FROM Customers WHERE State = @State`. Ejecute la consulta mediante una llamada a la `FillByState` como este método y pasando el valor del parámetro: `CustomerTableAdapter.FillByState("WA")`.  
  
 Además de agregar consultas que devuelven datos del mismo esquema como tabla de datos del TableAdapter, puede agregar consultas que devuelven los valores escalares (únicos). Por ejemplo, una consulta que devuelve un recuento de clientes (`SELECT Count(*) From Customers`) es válida para un `CustomersTableAdapter,` , aunque los datos que se devuelven no se ajustan al esquema de la tabla.  
  
## <a name="clearbeforefill-property"></a>Propiedad ClearBeforeFill  
 De forma predeterminada, cada vez que ejecute una consulta para rellenar la tabla de datos de un TableAdapter, se borran los datos existentes y se cargan solamente los resultados de la consulta en la tabla. Establecer el TableAdapter `ClearBeforeFill` propiedad `false` si desea agregar o combinar los datos que se devuelven de una consulta a los datos existentes en una tabla de datos. Independientemente de si borra los datos, deberá enviar explícitamente las actualizaciones a la base de datos, si desea guardarlos. Así que recuerde guardar los cambios a los datos en la tabla antes de ejecutar otra consulta que rellena la tabla. Para obtener más información, consulte [actualizar datos mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## <a name="tableadapter-inheritance"></a>Herencia de TableAdapter  
 Los TableAdapter amplían la funcionalidad de los adaptadores de datos estándar encapsulando un <xref:System.Data.Common.DataAdapter> clase? qualifyHint = False & autoUpgrade = True. De forma predeterminada, el objeto TableAdapter hereda el <xref:System.ComponentModel.Component> clase y no puede convertirse el <xref:System.Data.Common.DataAdapter> clase. Convertir un TableAdapter a la <xref:System.Data.Common.DataAdapter> clase da como resultado un <xref:System.InvalidCastException> error? qualifyHint = False & autoUpgrade = True. Para cambiar la clase base de un TableAdapter, puede escribir una clase que derive de <xref:System.ComponentModel.Component> en el **clase Base** propiedad del TableAdapter en el **Diseñador de Dataset**.  
  
## <a name="tableadapter-methods-and-properties"></a>Métodos y propiedades de TableAdapter  
 La clase TableAdapter no es parte de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Esto significa que no puede buscarla en la documentación o **Examinador de objetos**. Se crea en tiempo de diseño cuando se usa uno de los asistentes que se ha mencionado anteriormente. El nombre que se asigna a un TableAdapter al crearlo se basa en el nombre de la tabla que está trabajando. Por ejemplo, cuando se crea un TableAdapter basado en una tabla en una base de datos denominada `Orders`, lo TableAdapter se denomina `OrdersTableAdapter`. Se puede cambiar el nombre de clase del TableAdapter utilizando la propiedad **Name** en el **Diseñador de DataSet**.  
  
 Siguiente es las propiedades de los TableAdapters y los métodos más utilizados:  
  
|Miembro|Descripción|  
|------------|-----------------|  
|`TableAdapter.Fill`|Rellena la tabla de datos asociada del TableAdapter con los resultados del comando SELECT del TableAdapter.|  
|`TableAdapter.Update`|Envía los cambios a la base de datos y devuelve un entero que representa el número de filas afectadas por la actualización. Para obtener más información, consulte [actualizar datos mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Devuelve un nuevo <xref:System.Data.DataTable> que se rellena con datos.|  
|`TableAdapter.Insert`|Crea una nueva fila en la tabla de datos. Para obtener más información, consulte [insertar nuevos registros en una base de datos](../data-tools/insert-new-records-into-a-database.md).|  
|`TableAdapter.ClearBeforeFill`|Determina si se vacía una tabla de datos antes de llamar a uno de los métodos `Fill`.|  
  
## <a name="tableadapter-update-method"></a>Método de actualización de TableAdapter  
 Los TableAdapter utilizan comandos de datos para leer y escribir en la base de datos. Inicial de TableAdapter `Fill` consulta (principal) se usa como base para crear el esquema de la tabla de datos asociados, así como el `InsertCommand`, `UpdateCommand`, y `DeleteCommand` comandos que están asociados con el `TableAdapter.Update` método. Una llamada a un TableAdapter `Update` método ejecuta las instrucciones que se crearon al TableAdapter era originalmente configurado, no una de las consultas adicionales que se ha agregado con el **TableAdapter Query Configuration Wizard**.  
  
 Cuando utiliza un TableAdapter, éste realiza las mismas operaciones con los comandos que realizaría habitualmente. Por ejemplo, cuando se llama el adaptador `Fill` método, el adaptador ejecuta el comando de datos su `SelectCommand` propiedad y utiliza un lector de datos (por ejemplo, <xref:System.Data.SqlClient.SqlDataReader>) para cargar el conjunto de resultados en la tabla de datos. De forma similar, cuando se llama el adaptador `Update` método, ejecuta el comando adecuado (en el `UpdateCommand`, `InsertCommand`, y `DeleteCommand` propiedades) para cada registro modificado de la tabla de datos.  
  
> [!NOTE]
> Si hay bastante información en la consulta principal, se crean los comandos `InsertCommand`, `UpdateCommand` y `DeleteCommand` de manera predeterminada cuando se genera el TableAdapter. Si la consulta principal de TableAdapter es más que una instrucción SELECT de tabla única, es posible que el diseñador no podrá generar `InsertCommand`, `UpdateCommand`, y `DeleteCommand`. Si no se generan estos comandos, podría recibir un error cuando ejecute el `TableAdapter.Update` método.  
  
## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods  
 Además `InsertCommand`, `UpdateCommand`, y `DeleteCommand`, los TableAdapters se crean con métodos que se pueden ejecutar directamente en la base de datos. Se puede llamar a estos métodos (`TableAdapter.Insert`, `TableAdapter.Update` y `TableAdapter.Delete`) para manipular los datos directamente en la base de datos. Esto significa que puede llamar a estos métodos individuales desde el código en lugar de llamar `TableAdapter.Update` para controlar las inserciones, actualizaciones y eliminaciones que están pendientes de la tabla de datos asociados.  
  
 Si no desea crear estos métodos directos, establezca el TableAdapter **GenerateDbDirectMethods** propiedad `false` (en el **propiedades** ventana). Las consultas adicionales que se agregan al objeto TableAdapter son consultas independientes, que no generan estos métodos.  
  
## <a name="tableadapter-support-for-nullable-types"></a>Compatibilidad del objeto TableAdapter con los tipos que aceptan valores NULL  
 Los TableAdapters admiten tipos que aceptan valores NULL `Nullable(Of T)` y `T?`. Para más información sobre los tipos que aceptan valores NULL en Visual Basic, vea [Tipos que admiten valores null](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6). Para obtener más información acerca de los tipos que aceptan valores NULL en C#, vea [utilizar tipos que aceptan valores NULL](https://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28).  
  
## <a name="security"></a>Seguridad  
 Al utilizar los comandos de datos con un `CommandType` propiedad establecida en <xref:System.Data.CommandType>, cuidadosamente Compruebe la información que se envía desde un cliente antes de pasarla a la base de datos. Usuarios con malas intenciones podrían intentar enviar (inyectar) instrucciones de SQL modificadas o adicionales con el fin de obtener acceso no autorizado o dañar la base de datos. Antes de transferir la entrada del usuario a una base de datos, compruebe siempre que la información es válida. Una práctica recomendada es usar siempre las consultas parametrizadas o procedimientos almacenados cuando sea posible.  
  
## <a name="see-also"></a>Vea también  
 [Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
