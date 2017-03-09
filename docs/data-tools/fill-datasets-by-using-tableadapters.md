---
title: "Rellenar los conjuntos de datos con datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "datos [Visual Studio], conjuntos de datos"
  - "datos [Visual Studio], recuperar"
  - "recuperación de datos"
  - "conjuntos de datos [Visual Basic]"
  - "conjuntos de datos [Visual Basic], rellenar"
  - "conjuntos de datos [Visual Basic], cargar datos"
  - "recuperar datos"
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 32
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Rellenar los conjuntos de datos con datos
El mecanismo típico de Visual Studio para ejecutar consultas Transact\-SQL y para rellenar conjuntos de datos es el TableAdapter.  
  
 Puede ejecutar instrucciones SQL o procedimientos almacenados en un origen de datos mediante TableAdapters u objetos de comando \(por ejemplo, <xref:System.Data.SqlClient.SqlCommand>\).  Para cargar datos en conjuntos de datos creados mediante las herramientas de diseño en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], use TableAdapters.  Para cargar datos en conjuntos de datos creados mediante programación, utilice adaptadores de datos.  Si su aplicación no usa conjuntos de datos, utilice los objetos de comando para ejecutar instrucciones SQL o procedimientos almacenados directamente contra una base de datos.  
  
 En los siguientes temas se proporcionan detalles para llenar conjuntos de datos en Visual Studio:  
  
|Tema|Descripción|  
|----------|-----------------|  
|[Cómo: Llenar un conjunto de datos con datos](../data-tools/how-to-fill-a-dataset-with-data.md)|Proporciona detalles para cargar datos en conjuntos de datos utilizando TableAdapters y DataAdapters.|  
|[Cómo: Crear y ejecutar una instrucción SQL que devuelva filas](../Topic/How%20to:%20Create%20and%20Execute%20an%20SQL%20Statement%20that%20Returns%20Rows.md)|Proporciona detalles para crear y ejecutar instrucciones SQL que devuelven filas utilizando consultas de TableAdapter y objetos Command.|  
|[Cómo: Crear y ejecutar una instrucción SQL que devuelve un único valor](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value.md)|Proporciona detalles para crear y ejecutar instrucciones SQL que devuelven valores únicos utilizando consultas de TableAdapter y objetos Command.|  
|[Cómo: Crear y ejecutar una instrucción SQL que no devuelva ningún valor](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-no-value.md)|Proporciona detalles para crear y ejecutar instrucciones SQL que no devuelven ningún valor utilizando consultas de TableAdapter y objetos Command.|  
|[Cómo: Ejecutar un procedimiento almacenado que devuelve filas](../Topic/How%20to:%20Execute%20a%20Stored%20Procedure%20that%20Returns%20Rows.md)|Proporciona detalles para ejecutar procedimientos almacenados que devuelven filas utilizando consultas de TableAdapter y objetos Command.|  
|[Cómo: Ejecutar un procedimiento almacenado que devuelve un único valor](../data-tools/how-to-execute-a-stored-procedure-that-returns-a-single-value.md)|Proporciona detalles para ejecutar procedimientos almacenados que devuelven valores únicos utilizando consultas de TableAdapter y objetos Command.|  
|[Cómo: Ejecutar un procedimiento almacenado que no devuelve valores](../data-tools/how-to-execute-a-stored-procedure-that-returns-no-value.md)|Proporciona detalles para ejecutar procedimientos almacenados que no devuelven ningún valor utilizando consultas de TableAdapter y objetos Command.|  
|[Cómo: Establecer y obtener parámetros para objetos de comandos](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)|Proporciona detalles para asignar valores a los parámetros en consultas y procedimientos almacenados, y leer valores en los parámetros devueltos a partir de comandos ejecutados.|  
|[Tutorial: Rellenar un conjunto de datos con datos](../Topic/Walkthrough:%20Filling%20a%20Dataset%20with%20Data.md)|Proporciona detalles para crear un conjunto de datos y rellenarlo con los datos de una base de datos.|  
|[Tutorial: Leer datos XML e introducirlos en un conjunto de datos](../data-tools/read-xml-data-into-a-dataset.md)|Proporciona detalles para crear una aplicación para Windows que carga datos XML en un conjunto de datos y, a continuación, muestra el conjunto de datos en un control <xref:System.Windows.Forms.DataGridView>.|  
  
## Rellenar conjuntos de datos  
 Si crea un conjunto de datos con una herramienta en tiempo de diseño de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(como el [Diseñador de DataSet](../data-tools/creating-and-editing-typed-datasets.md) o el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png)\), deberá usar un TableAdapter para rellenarlo.  Los TableAdapters ejecutan las instrucciones SQL o procedimientos almacenados.  
  
 Si crea un conjunto de datos sin herramientas en tiempo de diseño, deberá utilizar los adaptadores de datos para rellenar y actualizar los datos.  \(Los TableAdapters no son realmente clases de [.NET Framework 4.5 y 4.6](../Topic/.NET%20Framework%204.6%20and%204.5.md), por lo que no son adecuados para trabajar con conjuntos de datos creados sin utilizar herramientas en tiempo de diseño\).  Para obtener más información sobre cómo cargar datos en conjuntos de datos con TableAdapters o adaptadores de datos, vea [Cómo: Llenar un conjunto de datos con datos](../data-tools/how-to-fill-a-dataset-with-data.md).  
  
## Consultas de TableAdapter  
 Se pueden ejecutar consultas de TableAdapter para rellenar los datos en conjuntos de datos \(más específicamente, cargar datos en las DataTables que constituyen un conjunto de datos\).  Se puede crear consultas de TableAdapter utilizando [Asistente para la configuración de consultas de TableAdapter](../data-tools/editing-tableadapters.md) en el **Diseñador de DataSet**.  Las consultas de TableAdapter aparecen como métodos con nombre en un TableAdapter y se ejecutan llamando al método TableAdapter.  Para obtener más información sobre cómo crear y ejecutar consultas de TableAdapter, vea las páginas siguientes:  
  
-   [Cómo: Crear y ejecutar una instrucción SQL que devuelva filas](../Topic/How%20to:%20Create%20and%20Execute%20an%20SQL%20Statement%20that%20Returns%20Rows.md)  
  
-   [Cómo: Crear y ejecutar una instrucción SQL que devuelve un único valor](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value.md)  
  
-   [Cómo: Crear y ejecutar una instrucción SQL que no devuelva ningún valor](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-no-value.md)  
  
-   [Cómo: Ejecutar un procedimiento almacenado que devuelve filas](../Topic/How%20to:%20Execute%20a%20Stored%20Procedure%20that%20Returns%20Rows.md)  
  
-   [Cómo: Ejecutar un procedimiento almacenado que devuelve un único valor](../data-tools/how-to-execute-a-stored-procedure-that-returns-a-single-value.md)  
  
-   [Cómo: Ejecutar un procedimiento almacenado que no devuelve valores](../data-tools/how-to-execute-a-stored-procedure-that-returns-no-value.md)  
  
## Objetos Command  
 Los objetos de comando proporcionan la capacidad de ejecutar instrucciones SQL y procedimientos almacenados directamente contra una base de datos, sin necesidad de un <xref:System.Data.DataSet>, TableAdapter o <xref:System.Data.Common.DataAdapter>.  \(El término *objeto de comando* se refiere al comando concreto para el proveedor de datos de .NET Framework que utiliza su aplicación.  Por ejemplo, si su aplicación utiliza el proveedor de datos de .NET Framework para el servidor SQL Server, el objeto de comando sería <xref:System.Data.SqlClient.SqlCommand>.\)  
  
 El usuario configura comandos para consultar datos utilizando instrucciones SQL o procedimientos almacenados mediante el establecimiento de la propiedad `CommandType` del comando de datos en uno de los valores en la enumeración <xref:System.Data.IDbCommand.CommandType%2A>.  Establezca el `CommandType` en <xref:System.Data.CommandType> para ejecutar instrucciones SQL o establézcalo en <xref:System.Data.CommandType> para ejecutar procedimientos almacenados.  A continuación, establezca la propiedad `CommandText` en una instrucción SQL o el nombre del procedimiento almacenado.  Entonces puede ejecutar el comando de datos llamando a uno de sus métodos de ejecución \(`ExecuteReader`, `ExecuteScalar`, `ExecuteNonQuery`\).  
  
 Cada uno de los [Proveedores de datos .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md) ofrece un objeto de comando optimizado para bases de datos concretas.  
  
 Con los comandos de datos, puede realizar las siguientes acciones en la aplicación:  
  
-   Ejecutar comandos Select que devuelvan un resultado que se pueda leer directamente, en vez de cargarlo en un conjunto de datos.  Para leer los resultados, utilice un lector de datos \(<xref:System.Data.OleDb.OleDbDataReader>, <xref:System.Data.SqlClient.SqlDataReader>, <xref:System.Data.Odbc.OdbcDataReader> o el objeto <xref:System.Data.OracleClient.OracleDataReader>\), el cual funciona como un cursor de sólo lectura y sólo hacia delante, al que puede enlazar los controles.  Ésta es una estrategia útil para reducir el uso de memoria y cargar datos de sólo lectura muy rápido.  
  
-   Ejecutar comandos de definición de base de datos \(DDL\) para crear, editar y quitar tablas, procedimientos almacenados y otras estructuras de base de datos.  Por supuesto, debe tener permisos para realizar estas acciones.  
  
-   Ejecutar comandos para obtener información del catálogo de base de datos.  
  
-   Ejecutar comandos SQL dinámicos para actualizar, insertar o eliminar registros, en vez de actualizar tablas de un conjunto de datos y, a continuación, copiar los cambios a la base de datos.  
  
-   Ejecutar comandos que devuelvan un valor escalar \(es decir, un valor único\), como los resultados de una función de agregado \(SUM, COUNT, AVG, etc.\).  
  
-   Ejecutar comandos que devuelvan datos de una base de datos de SQL Server \(versión 7.0 o posterior\) en formato XML.  Un uso habitual es ejecutar una consulta y devolver datos en formato XML, aplicarle una transformación XSLT para convertir los datos a HTML y, a continuación, enviar el resultado a un explorador.  
  
 Las propiedades de un comando contienen toda la información necesaria para ejecutar un comando contra una base de datos.  Esto incluye:  
  
-   **Una conexión** El comando hace referencia a una conexión que utiliza para comunicarse con la base de datos.  
  
-   **El nombre o el texto de un comando** El comando incluye el texto real de una instrucción SQL o el nombre de un procedimiento almacenado que se va a ejecutar.  
  
-   **Parámetros** Un comando podría requerir que se pasen valores de parámetros junto con el comando \(parámetros de entrada\).  En comando también podría devolver valores en el formato de un valor devuelto o valores del parámetro de salida.  Cada comando tiene una colección de parámetros que puede establecer o leer individualmente para pasar o recibir valores.  Para obtener más información, vea [Cómo: Establecer y obtener parámetros para objetos de comandos](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md).  
  
 El usuario ejecuta un comando mediante un método apropiado de acuerdo con los resultados que espera obtener.  Por ejemplo, si espera obtener filas, se invoca al método `ExecuteReader` del comando, el cual devuelve registros a un lector de datos.  Si ejecuta un comando UPDATE, INSERT o DELETE, llamará al método `ExecuteNonQuery`, el cual devuelve un valor que indica el número de filas afectadas.  Si realiza una función de agregado, como devolver el recuento de pedidos para un cliente, se llama al método `ExecuteScalar`.  
  
### Conjuntos de resultados múltiples  
 Un uso típico de un objeto de comando es devolver una tabla única de datos \(un conjunto de filas\).  No obstante, los comandos de datos pueden ejecutar procedimientos que devuelvan conjuntos de resultados múltiples.  Esto puede ocurrir de varias formas.  Una forma es que el comando haga referencia a un procedimiento almacenado que devuelva varios conjuntos de resultados.  El comando también puede tener dos \(o más\) instrucciones o nombres de procedimientos almacenados.  En este caso, las instrucciones o los procedimientos se ejecutan secuencialmente y devuelven varios resultados con una única llamada.  
  
 Si especifica varias instrucciones o procedimientos para un comando, todos deben ser del mismo tipo.  Por ejemplo, puede ejecutar instrucciones SQL o procedimientos almacenados sucesivos.  No obstante, no puede mezclar llamadas a un procedimiento almacenado y a instrucciones SQL en el mismo comando.  Para obtener más información, vea [Recuperar datos mediante DataReader](../Topic/Retrieving%20Data%20Using%20a%20DataReader.md).  
  
> [!NOTE]
>  Para Oracle, el proveedor de datos de .NET Framework para Oracle no admite instrucciones SQL en lotes.  Sin embargo, sí permite utilizar varios parámetros de salida REF CURSOR para llenar un conjunto de datos, cada uno en su propia tabla de datos.  Debe definir los parámetros, marcarlos como parámetros de salida e indicar que son tipos de datos REF CURSOR.  Tenga en cuenta que no podrá utilizar el método `Update` cuando el objeto <xref:System.Data.OracleClient.OracleDataAdapter> se llene con parámetros REF CURSOR en un procedimiento almacenado, porque Oracle no proporciona la información necesaria para determinar el nombre de la tabla y de las columnas cuando se ejecuta la instrucción SQL.  
  
## Seguridad  
 Al utilizar comandos de datos con una propiedad `CommandType` establecida en <xref:System.Data.CommandType>, compruebe minuciosamente la información enviada por un cliente antes de pasarla a la base de datos.  Usuarios con malas intenciones podrían intentar enviar \(inyectar\) instrucciones de SQL modificadas o adicionales con el fin de obtener acceso no autorizado o dañar la base de datos.  Antes de transferir los datos proporcionados por el usuario a una base de datos, siempre debe comprobar que la información sea válida.  Un procedimiento recomendado es utilizar consultas parametrizadas o procedimientos almacenados cuando sea posible.  
  
## Vea también  
 [Información general de las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)   
 [Herramientas para trabajar con orígenes de datos en Visual Studio](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)