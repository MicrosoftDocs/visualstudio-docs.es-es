---
title: Volver a guardar los datos en la base de datos | Microsoft Docs
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
- datasets [Visual Basic], validating data
- data validation, datasets
- data [Visual Studio], saving
- row version
- updating datasets, constraints
- datasets [Visual Basic], about datasets
- datasets [Visual Basic], merging
- updates, constraints in datasets
- saving data, about saving data
- datasets [Visual Basic], constraints
- TableAdapters
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1b1a54d8be5ab4aa9703d318d0b537deff53b6f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652868"
---
# <a name="save-data-back-to-the-database"></a>Guardar los datos de nuevo en la base de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El conjunto de datos es una copia en memoria de los datos. Si modifica los datos, se recomienda volver a guardarlos en la base de datos. Esto se realiza de una de estas tres maneras:

- Llamando a uno de los `Update` métodos de un TableAdapter

- Llamando a uno de los métodos DBDirect de TableAdapter

- Llamando al método UpdateAll en `TableAdapterManager` que Visual Studio genera automáticamente cuando el conjunto de objetos contiene tablas que están relacionadas con otras tablas del conjunto de elementos.

  Al enlazar datos de tablas de conjuntos de datos a controles en una página XAML o Windows Forms, la arquitectura de enlace de datos realiza todo el trabajo por usted.

  Si está familiarizado con los TableAdapters, puede ir directamente a uno de estos temas:

|Tema|Descripción|
|-----------|-----------------|
|[Insertar nuevos registros en una base de datos](../data-tools/insert-new-records-into-a-database.md)|Cómo realizar actualizaciones e inserciones mediante TableAdapters u objetos de comando|
|[Actualizar datos mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Cómo realizar actualizaciones con TableAdapters|
|[Actualización jerárquica](../data-tools/hierarchical-update.md)|Cómo realizar actualizaciones desde un conjunto de información con dos o más tablas relacionadas|
|[Tratar las excepciones de simultaneidad](../data-tools/handle-a-concurrency-exception.md)|Cómo controlar excepciones cuando dos usuarios intentan cambiar los mismos datos en una base de datos al mismo tiempo|
|[Guardar datos mediante una transacción](../data-tools/save-data-by-using-a-transaction.md)|Cómo guardar datos en una transacción mediante el espacio de nombres System. Transactions y el objeto TransactionScope|
|[Guardar datos en una transacción](../data-tools/save-data-in-a-transaction.md)|Cómo guardar datos en una transacción mediante el espacio de nombres System. Transactions|
|[Guardar datos en una base de datos (varias tablas)](../data-tools/save-data-to-a-database-multiple-tables.md)|Cómo editar registros y guardar cambios en varias tablas de nuevo en la base de datos|
|[Guardar los datos de un objeto en una base de datos](../data-tools/save-data-from-an-object-to-a-database.md)|Cómo pasar datos de un objeto que no está en un conjunto de datos a una base de datos mediante un método DbDirect de TableAdapter|
|[Guardar datos con los métodos DBDirect de un TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Cómo usar el TableAdapter para enviar consultas SQL directamente a la base de datos|
|[Guardar un conjunto de datos como XML](../data-tools/save-a-dataset-as-xml.md)|Cómo guardar un conjunto de información en un documento XML|

## <a name="two-stage-updates"></a>Actualizaciones en dos fases
 La actualización de un origen de datos es un proceso de dos pasos. El primer paso es actualizar el conjunto de archivos con nuevos registros, registros modificados o registros eliminados. Si la aplicación nunca vuelve a enviar los cambios al origen de datos, ha terminado con la actualización.

 Si vuelve a enviar los cambios a la base de datos, se requiere un segundo paso. Si no está utilizando controles enlazados a datos, tendrá que llamar manualmente al método Update del mismo TableAdapter (o adaptador de datos) que utilizó para rellenar el conjunto de datos. Sin embargo, también puede utilizar adaptadores diferentes, por ejemplo, para trasladar datos de un origen de datos a otro o para actualizar varios orígenes de datos. Si no está utilizando el enlace de datos y está guardando los cambios de las tablas relacionadas, tendrá que crear manualmente una instancia de una variable de la clase TableAdapterManager generada automáticamente y, a continuación, llamar a su método UpdateAll.

 ![Actualizaciones de Visual Basic DataSet](../data-tools/media/vbdatasetupdates.gif "vbDatasetUpdates") Proceso de actualización en dos fases y el rol de DataRowVersion en una actualización correcta

 Un conjunto de DataSet contiene colecciones de tablas, que contienen colecciones de filas. Si piensa actualizar un origen de datos subyacente más adelante, debe utilizar los métodos de la propiedad DataTable. DataRowCollection al agregar o quitar filas. Estos métodos realizan el seguimiento de cambios necesario para actualizar el origen de datos. Si se llama a la colección RemoveAt en la propiedad Rows, la eliminación no volverá a comunicarse con la base de datos.

## <a name="merge-datasets"></a>Combinar conjuntos de valores
 Puede actualizar el contenido de un conjunto de DataSet *combinándolos* con otro conjunto de los mismos. Esto implica copiar el contenido de un conjunto de *orígenes de origen* en el conjunto de código que realiza la llamada (denominado conjunto de orígenes de *destino* ). Cuando se fusionan mediante combinación conjuntos de datos, los registros nuevos del conjunto de datos de origen se agregan al conjunto de datos de destino. Asimismo, las columnas adicionales del conjunto de datos de origen se agregan al conjunto de datos de destino. La combinación de conjuntos de aplicaciones resulta útil cuando se tiene un conjunto de valores local y se obtiene un segundo conjunto de los mismos desde otra aplicación. También resulta útil cuando se obtiene un segundo conjunto de datos de un componente, como un servicio Web XML, o cuando se necesita integrar datos de varios conjuntos de datos.

 Al combinar conjuntos de valores, se puede pasar un argumento booleano ( `preserveChanges` ) que indica al <xref:System.Data.DataSet.Merge%2A> método si se deben conservar las modificaciones existentes en el conjunto de de destino. Debido a que los conjuntos de datos mantienen varias versiones de los registros, es importante recordar que se está combinado más de una versión de los registros. En la tabla siguiente se muestra cómo se combina un registro en dos conjuntos de registros:

|DataRowVersion|Conjunto de datos de destino|Conjunto de datos de origen|
|--------------------|--------------------|--------------------|
|Original|James Wilson|James C. Wilson|
|Current|Jim Wilson|James C. Wilson|

 Al llamar al <xref:System.Data.DataSet.Merge%2A> método en la tabla anterior, se `preserveChanges=false targetDataset.Merge(sourceDataset)` obtiene el siguiente resultado:

|DataRowVersion|Conjunto de datos de destino|Conjunto de datos de origen|
|--------------------|--------------------|--------------------|
|Original|James C. Wilson|James C. Wilson|
|Current|James C. Wilson|James C. Wilson|

 Al llamar al método <xref:System.Data.DataSet.Merge%2A> con `preserveChanges = true targetDataset.Merge(sourceDataset, true)`, se obtiene el siguiente resultado:

|DataRowVersion|Conjunto de datos de destino|Conjunto de datos de origen|
|--------------------|--------------------|--------------------|
|Original|James C. Wilson|James C. Wilson|
|Current|Jim Wilson|James C. Wilson|

> [!CAUTION]
> En el `preserveChanges = true` escenario, si <xref:System.Data.DataSet.RejectChanges%2A> se llama al método en un registro del conjunto de datos de destino, se revierte a los datos originales del conjunto de datos de *origen* . Esto significa que, si intenta actualizar el origen de datos original con el conjunto de datos de destino, es posible que no pueda encontrar la fila original que se va a actualizar. Puede evitar una infracción de simultaneidad rellenando otro conjunto de datos con los registros actualizados del origen de datos y, a continuación, realizando una combinación para evitar una infracción de simultaneidad. (Una infracción de simultaneidad se produce cuando otro usuario modifica un registro del origen de datos después de que se ha rellenado el conjunto de datos.)

## <a name="update-constraints"></a>Restricciones de actualización
 Para realizar cambios en una fila de datos existente, agregue o actualice los datos de las columnas individuales. Si el conjunto de registros contiene restricciones (como claves externas o restricciones que no aceptan valores NULL), es posible que el registro esté temporalmente en un estado de error cuando lo actualice. Es decir, puede estar en un estado de error después de terminar de actualizar una columna, pero antes de llegar a la siguiente.

 Para impedir que se produzcan infracciones de restricciones prematuras, puede suspender temporalmente las restricciones de actualización. Esta suspensión tiene dos fines:

- Impide que se produzca un error después de que haya terminado de actualizar una columna pero no haya empezado a actualizar otra.

- Impide que se generen determinados eventos de actualización (eventos que se suelen usar para la validación).

  Después de completar una actualización, puede volver a habilitar la comprobación de restricciones, que también vuelve a habilitar los eventos de actualización y los genera.

> [!NOTE]
> En Windows Forms, la arquitectura de enlace de datos integrada en DataGrid suspende la comprobación de restricciones hasta que el foco sale de una fila y no es necesario llamar explícitamente a los <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A> métodos, o <xref:System.Data.DataRow.CancelEdit%2A> .

 Las restricciones se deshabilitan automáticamente cuando se invoca el método <xref:System.Data.DataSet.Merge%2A> en un conjunto de datos. Una vez completada la combinación, si hay alguna restricción en el conjunto de DataSet que no se pueda habilitar, <xref:System.Data.ConstraintException> se produce una excepción. En esta situación, la propiedad <xref:System.Data.DataSet.EnforceConstraints%2A> se establece en `false,` y todas las infracciones de las restricciones se deben resolver antes de restablecer la propiedad <xref:System.Data.DataSet.EnforceConstraints%2A> a `true`.

 Después de completar una actualización, puede volver a habilitar la comprobación de restricciones, que también vuelve a habilitar los eventos de actualización y los genera.

 Para obtener más información sobre la suspensión de eventos, vea [desactivar restricciones al llenar un conjunto](../data-tools/turn-off-constraints-while-filling-a-dataset.md)de datos.

## <a name="dataset-update-errors"></a>Errores de actualización de conjuntos de datos
 Cuando se actualiza un registro de un conjunto de datos, existe la posibilidad de que se produzca un error. Por ejemplo, podría escribir accidentalmente datos del tipo incorrecto en una columna o datos demasiado largos o datos que tengan algún otro problema de integridad. O bien, puede que tenga comprobaciones de validación específicas de la aplicación que pueden provocar errores personalizados durante cualquier fase de un evento de actualización. Para obtener más información, vea [Validate Data in datasets](../data-tools/validate-data-in-datasets.md).

## <a name="maintaining-information-about-changes"></a>Mantener información acerca de los cambios
 La información sobre los cambios en un conjunto de datos se mantiene de dos maneras: marcando filas que indican que han cambiado ( <xref:System.Data.DataRow.RowState%2A> ) y manteniendo varias copias de un registro ( <xref:System.Data.DataRowVersion> ). Con esta información, los procesos pueden determinar qué ha cambiado en el conjunto de datos y pueden enviar las actualizaciones correspondientes al origen de datos.

### <a name="rowstate-property"></a>Propiedad RowState
 La propiedad <xref:System.Data.DataRow.RowState%2A> de un objeto <xref:System.Data.DataRow> es un valor que proporciona información sobre el estado de una fila de datos determinada.

 En la tabla siguiente se detallan los posibles valores de la enumeración <xref:System.Data.DataRowState>:

|Valor de DataRowState|Descripción|
|------------------------|-----------------|
|<xref:System.Data.DataRowState>|La fila se ha agregado como elemento a <xref:System.Data.DataRowCollection>. (Una fila de este estado no tiene una versión original correspondiente, ya que no existía cuando <xref:System.Data.DataRow.AcceptChanges%2A> se llamó al último método).|
|<xref:System.Data.DataRowState>|La fila se eliminó utilizando el método <xref:System.Data.DataRow.Delete%2A> de un objeto <xref:System.Data.DataRow>.|
|<xref:System.Data.DataRowState>|La fila se ha creado pero no forma parte de ninguna <xref:System.Data.DataRowCollection>. Un <xref:System.Data.DataRow> objeto está en este estado inmediatamente después de que se haya creado, antes de que se haya agregado a una colección y después de que se haya quitado de una colección.|
|<xref:System.Data.DataRowState>|Un valor de columna de la fila ha cambiado de alguna manera.|
|<xref:System.Data.DataRowState>|La fila no ha cambiado desde la última vez que se llamó a <xref:System.Data.DataRow.AcceptChanges%2A>.|

### <a name="datarowversion-enumeration"></a>DataRowVersion (enumeración)
 Los conjuntos de datos mantienen varias versiones de los registros. La enumeración <xref:System.Data.DataRowVersion> de un objeto <xref:System.Data.DataRow> es un valor que se puede utilizar para devolver una versión específica de un objeto <xref:System.Data.DataRow>.

 En la tabla siguiente se detallan los posibles valores de la enumeración <xref:System.Data.DataRowVersion>:

|Valor de DataRowVersion|Descripción|
|--------------------------|-----------------|
|<xref:System.Data.DataRowVersion>|La versión actual de un registro contiene todas las modificaciones que se han realizado en el registro desde la última vez que <xref:System.Data.DataRow.AcceptChanges%2A> se llamó a. Si la fila se ha eliminado, no existe una versión actual.|
|<xref:System.Data.DataRowVersion>|Es el valor predeterminado de un registro, tal como se define en el esquema del conjunto de datos o en el origen de datos.|
|<xref:System.Data.DataRowVersion>|La versión original de un registro es una copia del registro tal como se encontraba la última vez que se confirmaron cambios en el conjunto de datos. En términos prácticos, suele ser la versión de un registro leído de un origen de datos.|
|<xref:System.Data.DataRowVersion>|Es la versión propuesta de un registro que está disponible temporalmente, mientras está en curso una actualización, es decir, el intervalo que transcurre desde que se llama al método <xref:System.Data.DataRow.BeginEdit%2A> hasta que se llama al método <xref:System.Data.DataRow.EndEdit%2A>. Normalmente, se obtiene acceso a la versión propuesta de un registro en un controlador de un evento tal como <xref:System.Data.DataTable.RowChanging>. Al invocar al método <xref:System.Data.DataRow.CancelEdit%2A>, se anulan los cambios y se elimina la versión propuesta de la fila de datos.|

 Las versiones original y actual son de utilidad cuando se transmite la información de actualización a un origen de datos. Normalmente, cuando envía una actualización al origen de datos, la nueva información de la base de datos está en la versión actual de un registro. Para buscar el registro que actualizar se utiliza información de la versión original.

 Por ejemplo, en un caso en el que se cambia la clave principal de un registro, necesita una manera de buscar el registro correcto en el origen de datos para actualizar los cambios. Si no existiese una versión original, lo más probable es que el registro se agregase al final del origen de datos, con lo que se obtendría no sólo un registro adicional no deseado, sino que, además, sería inexacto y obsoleto. Las dos versiones también se usan en el control de simultaneidad. Puede comparar la versión original con un registro del origen de datos para determinar si el registro ha cambiado desde que se cargó en el conjunto de datos.

 La versión propuesta es de utilidad cuando se necesita realizar una validación antes de confirmar los cambios en el conjunto de datos.

 Incluso aunque los registros hayan cambiado, no siempre hay versiones originales o actuales de esa fila. Cuando se inserta una fila nueva en la tabla, no hay versión original, sólo una versión actual. Lo mismo sucede si se elimina una fila mediante una llamada al método `Delete` de la tabla: hay una versión original, pero no hay versión actual.

 Para comprobar si existe una versión específica de un registro, haga una consulta al método <xref:System.Data.DataRow.HasVersion%2A> de una fila de datos. Para obtener acceso a cualquiera de las versiones de un registro, pase un valor de la enumeración <xref:System.Data.DataRowVersion> como argumento opcional cuando solicite el valor de una columna.

## <a name="getting-changed-records"></a>Obtener registros modificados
 Es una práctica común no actualizar todos los registros de un conjunto de registros. Por ejemplo, un usuario puede estar trabajando con un control <xref:System.Windows.Forms.DataGridView> de formularios Windows Forms que muestre muchos registros, pero puede actualizar sólo algunos, eliminar uno e insertar otro. Los conjuntos de datos y las tablas de datos proporcionan un método (`GetChanges`) para devolver sólo las filas que se hayan modificado.

 Es posible crear subconjuntos de registros modificados con el método `GetChanges` de cualquiera de las tablas de datos (<xref:System.Data.DataTable.GetChanges%2A>) o del propio conjunto de datos (<xref:System.Data.DataSet.GetChanges%2A>). Si se llama al método de la tabla de datos, devuelve una copia de la tabla donde sólo se muestran los registros cambiados. De igual forma, si llama al método en el conjunto de datos, obtiene un nuevo conjunto de datos solo con los registros modificados.

 `GetChanges` por sí solo devuelve todos los registros modificados. Por el contrario, si se pasa el <xref:System.Data.DataRowState> elemento deseado como parámetro al `GetChanges` método, se puede especificar el subconjunto de registros modificados que se desea: registros recién agregados, registros que se marcan para su eliminación, registros desasociados o registros modificados.

 Obtener un subconjunto de registros modificados resulta útil cuando se desea enviar registros a otro componente para su procesamiento. En lugar de enviar todo el conjunto de datos, se puede reducir la sobrecarga de la comunicación con el otro componente al obtener únicamente los registros necesarios. Para obtener más información, vea [Cómo: recuperar filas modificadas](https://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).

## <a name="committing-changes-in-the-dataset"></a>Confirmar los cambios en el conjunto de DataSet
 Cuando se realizan cambios en el conjunto de datos, se establece la propiedad <xref:System.Data.DataRow.RowState%2A> de las filas modificadas. La propiedad establece, mantiene y pone a su disposición las versiones original y actual de los registros <xref:System.Data.DataRowView.RowVersion%2A> . Los metadatos que se almacenan en las propiedades de estas filas cambiadas son necesarios para enviar las actualizaciones correctas al origen de datos.

 Si los cambios reflejan el estado actual del origen de datos, ya no es necesario mantener esta información. Normalmente, el conjunto de datos y su origen están sincronizados en dos ocasiones:

- Inmediatamente después de haber cargado información en el conjunto de datos; por ejemplo, cuando lee datos del origen.

- Después de enviar los cambios del conjunto de datos al origen de datos (pero no antes, porque perdería la información de cambios necesaria para enviar los cambios a la base de datos).

  Para confirmar los cambios pendientes en el conjunto de datos, puede llamar al método <xref:System.Data.DataSet.AcceptChanges%2A>. Normalmente, <xref:System.Data.DataSet.AcceptChanges%2A> se llama a durante las siguientes horas en la aplicación.

- Después de cargar el conjunto de DataSet. Si se carga un conjunto de datos mediante una llamada al método `Fill` del TableAdapter, este adaptador confirma los cambios automáticamente. Sin embargo, si carga un conjunto de datos mediante la combinación de otro conjunto de datos, los cambios se deben confirmar manualmente.

  > [!NOTE]
  > Puede evitar que el adaptador confirme automáticamente los cambios cuando se llama al `Fill` método estableciendo la `AcceptChangesDuringFill` propiedad del adaptador en `false` . Si se establece en `false` , el <xref:System.Data.DataRow.RowState%2A> de cada fila que se inserta durante el rellenado se establece en <xref:System.Data.DataRowState> .

- Después de enviar los cambios del conjunto de código a otro proceso, como un servicio Web XML.

  > [!CAUTION]
  > Si confirma el cambio de este modo, se borra la información sobre cambios existente. No confirme los cambios hasta que termine de realizar operaciones que requieran que la aplicación sepa qué cambios se han realizado en el conjunto de elementos.

  Este método realiza las funciones siguientes:

- Escribe la <xref:System.Data.DataRowVersion> versión de un registro en su <xref:System.Data.DataRowVersion> versión y sobrescribe la versión original.

- Quita todas las filas en las que la <xref:System.Data.DataRow.RowState%2A> propiedad está establecida en <xref:System.Data.DataRowState> .

- Establece la propiedad <xref:System.Data.DataRow.RowState%2A> de un registro en <xref:System.Data.DataRowState>.

  El método <xref:System.Data.DataSet.AcceptChanges%2A> está disponible en tres niveles. Puede llamarlo en un <xref:System.Data.DataRow> objeto para confirmar los cambios solo para esa fila. También puede llamarlo en un <xref:System.Data.DataTable> objeto para confirmar todas las filas de una tabla. Por último, puede llamarlo en el <xref:System.Data.DataSet> objeto para confirmar todos los cambios pendientes en todos los registros de todas las tablas del conjunto de archivos.

  En la tabla siguiente se describen los cambios que se confirman en función del objeto en el que se llame el método.

|Método|Resultado|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Los cambios se confirman solo en una fila específica.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Los cambios se confirman en todas las filas de una tabla específica.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Los cambios se confirman en todas las filas de todas las tablas del conjunto de datos.|

> [!NOTE]
> Si carga un conjunto de objetos llamando al método de un TableAdapter `Fill` , no es necesario que acepte explícitamente los cambios. De forma predeterminada, el `Fill` método llama al `AcceptChanges` método después de que termine de rellenar la tabla de datos.

 Un método relacionado, `RejectChanges` , deshace el efecto de los cambios copiando la <xref:System.Data.DataRowVersion> versión en la <xref:System.Data.DataRowVersion> versión de los registros. También establece <xref:System.Data.DataRow.RowState%2A> de nuevo el de cada registro en <xref:System.Data.DataRowState> .

## <a name="data-validation"></a>Validación de datos
 Para comprobar que los datos de una aplicación satisfacen los requisitos de los procesos a los que se pasan, normalmente se agrega validación. Esto puede implicar la comprobación de que la entrada de un usuario en un formulario es correcta, la validación de los datos que se envían a la aplicación por otra aplicación, o incluso la comprobación de que la información calculada dentro del componente se encuentra dentro de las restricciones de los requisitos de la aplicación y el origen de datos.

 Los datos se pueden validar de distintas maneras:

- En la capa de empresa, agregando código a la aplicación para validar los datos. Un lugar en el que puede hacerlo es en el conjunto de datos. El diseñador de DataSet proporciona algunas de las ventajas de la validación de back-end, como la capacidad de validar los cambios a medida que se modifican los valores de columna y fila. Para obtener más información, vea [Validate Data in datasets](../data-tools/validate-data-in-datasets.md).

- En la capa de presentación, agregando validación a los formularios. Para obtener más información, consulte [validación de entradas de usuario en Windows Forms](https://msdn.microsoft.com/library/4ec07681-1dee-4bf9-be5e-718f635a33a1).

- En el servidor de datos, al enviar los datos al origen de datos, por ejemplo la base de datos, y dejar que éste los acepte o los rechace. Si trabaja con una base de datos que incluye funciones sofisticadas para validar datos y proporcionar información sobre errores, puede ser un planteamiento práctico, porque los datos se pueden validar sea cual sea su procedencia. Sin embargo, este enfoque podría no adaptarse a los requisitos de validación específicos de la aplicación. Además, si el origen de datos valida los datos, pueden producirse numerosos viajes de ida y vuelta al origen de datos, en función de cómo facilite la aplicación la resolución de los errores de validación generados por el back-end.

  > [!IMPORTANT]
  > Al utilizar comandos de datos con una <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> propiedad establecida en <xref:System.Data.CommandType> , compruebe cuidadosamente la información que se envía desde un cliente antes de pasarla a la base de datos. Usuarios con malas intenciones podrían intentar enviar (inyectar) instrucciones de SQL modificadas o adicionales con el fin de obtener acceso no autorizado o dañar la base de datos. Antes de transferir la entrada del usuario a una base de datos, compruebe siempre que la información es válida. Es recomendable usar siempre consultas con parámetros o procedimientos almacenados cuando sea posible. Para más información, consulte [Información general sobre los ataques mediante scripts](https://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).

  Después de modificar un conjunto de datos, se pueden transmitir los cambios a un origen de datos. Lo más frecuente será hacerlo mediante una llamada al método `Update` del TableAdapter (o adaptador de datos). El método recorre en bucle cada registro de una tabla de datos, determina qué tipo de actualización se requiere (actualización, inserción o eliminación), si existe, y, a continuación, ejecuta el comando adecuado.

## <a name="transmitting-updates-to-the-data-source"></a>Transmisión de actualizaciones al origen de datos
 Como ejemplo de cómo se realizan las actualizaciones, supongamos que la aplicación utiliza un conjunto de datos que contiene una sola tabla de datos. La aplicación obtiene dos filas de la base de datos. Después de recuperarlas, la tabla de datos en memoria sería como la siguiente:

```
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

 Su aplicación cambia el estado de Nancy Buchanan a "Preferred". Como resultado de este cambio, el valor de la propiedad <xref:System.Data.DataRow.RowState%2A> de esa fila cambia de <xref:System.Data.DataRowState> a <xref:System.Data.DataRowState>. El valor de la propiedad <xref:System.Data.DataRow.RowState%2A> de la primera fila se mantiene como <xref:System.Data.DataRowState>. Ahora, la tabla de datos tiene este aspecto:

```
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

 Llegados a este punto, su aplicación llama al método `Update` para transmitir el conjunto de datos a la base de datos. El método inspecciona cada fila de una en una. En la primera fila, el método no transmite ninguna instrucción SQL a la base de datos, porque esa fila no ha cambiado desde la primera vez que se obtuvo de la base de datos.

 Sin embargo, para la segunda fila, el `Update` método invoca automáticamente el comando de datos correcto y lo transmite a la base de datos. La sintaxis específica de la instrucción SQL depende del dialecto de SQL que sea compatible con el almacén de datos subyacente. Con todo, cabe señalar los siguientes rasgos generales de la instrucción SQL transmitida:

- Es una instrucción UPDATE. El adaptador sabe cómo utilizar una instrucción UPDATE, porque el valor de la propiedad <xref:System.Data.DataRow.RowState%2A> es <xref:System.Data.DataRowState>.

- Incluye una cláusula WHERE que indica que el destino de la instrucción UPDATE es la fila donde `CustomerID = 'c400'`. Esta parte de la instrucción SELECT distingue la fila de destino de las demás porque `CustomerID` es la clave principal de la tabla de destino. La información de la cláusula WHERE se deriva de la versión original del registro ( `DataRowVersion.Original` ), en caso de que cambien los valores necesarios para identificar la fila.

- Incluye la cláusula SET para establecer los nuevos valores de las columnas modificadas.

    > [!NOTE]
    > Si la propiedad `UpdateCommand` del TableAdapter se ha establecido en el nombre de un procedimiento almacenado, el adaptador no construye una instrucción SQL. En su lugar, invoca al procedimiento almacenado pasando los parámetros correspondientes.

## <a name="passing-parameters"></a>Pasar parámetros
 Normalmente, se usan parámetros para pasar los valores de los registros que se van a actualizar en la base de datos.  Cuando el método del TableAdapter `Update` ejecuta una instrucción UPDATE, debe rellenar los valores de los parámetros. Dichos valores los obtiene de la colección `Parameters` del comando de datos correspondiente, en este caso, el objeto `UpdateCommand` de TableAdapter.

 Si ha usado las herramientas de Visual Studio para generar un adaptador de datos, el `UpdateCommand` objeto contiene una colección de parámetros que se corresponden con cada marcador de posición de parámetro de la instrucción.

 La propiedad <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> de cada parámetro señala a una columna en la tabla de datos. Por ejemplo, la `SourceColumn` propiedad de los `au_id` `Original_au_id` parámetros y se establece en la columna de la tabla de datos que contiene el identificador del autor. Cuando el método del adaptador `Update` se ejecuta, lee la columna de ID. de autor del registro que se está actualizando y rellena los valores en la instrucción.

 En una instrucción UPDATE, debe especificar los valores nuevos (los que se escribirán en el registro), así como los valores antiguos (para que el registro se pueda encontrar en la base de datos). Por tanto, hay dos parámetros para cada valor: uno para la cláusula SET y otro diferente para la cláusula WHERE. Ambos parámetros leen los datos del registro que se está actualizando, pero obtienen versiones diferentes del valor de la columna basándose en la [propiedad SqlParameter. SourceVersion](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.sourceversion.aspx)del parámetro. El parámetro de la cláusula SET obtiene la versión actual y el parámetro de la cláusula WHERE obtiene la versión original.

> [!NOTE]
> También puede establecer los valores de la colección `Parameters` en el código; en ese caso, sería necesario hacerlo en un controlador de eventos para el evento <xref:System.Data.DataTable.RowChanging> del adaptador de datos.

## <a name="see-also"></a>Consulte también
 [Actualizar datos mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) [preparar la aplicación para recibir](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [controles de enlace de datos a los datos de la validación de datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md) [Validating Data](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)
