---
title: "C&#243;mo: Crear y ejecutar una instrucci&#243;n SQL que no devuelva ning&#250;n valor | Microsoft Docs"
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
  - "llamar a métodos, ejemplos"
  - "llamadas a métodos, ejemplos"
  - "instrucciones SQL, crear"
  - "instrucciones SQL, ejecutar"
ms.assetid: 612d3046-0cfa-4d90-be6e-c4d6bcbd5aee
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Crear y ejecutar una instrucci&#243;n SQL que no devuelva ning&#250;n valor
Para ejecutar una instrucción SQL que no devuelva valores, puede ejecutar una consulta de TableAdapter configurada para ejecutar una instrucción SQL \(por ejemplo, `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`\).  
  
 Si la aplicación no utiliza TableAdapters, llame al método `ExecuteNonQuery` en un objeto de comando, estableciendo su propiedad `CommandType` en <xref:System.Data.CommandType>.  \(El objeto "Command"" hace referencia al comando concreto para el [Proveedor de datos de .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md) que utiliza su aplicación.  Por ejemplo, si su aplicación utiliza el proveedor de datos de .NET Framework para el servidor SQL Server, el objeto de comando sería <xref:System.Data.SqlClient.SqlCommand>.\)  
  
 Los ejemplos siguientes muestran cómo ejecutar instrucciones SQL que no devuelva ningún valor desde una base de datos utilizando TableAdapters u objetos de comando.  Para obtener más información sobre cómo realizar consultas con TableAdapters y comandos, vea [Rellenar los conjuntos de datos con datos](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
## Ejecutar instrucciones SQL que no devuelvan valores mediante un TableAdapter  
 Este ejemplo muestra cómo crear una consulta de TableAdapter mediante [Asistente para la configuración de consultas de TableAdapter](../data-tools/editing-tableadapters.md) y, a continuación, proporciona información acerca de cómo declarar una instancia de TableAdapter y ejecutar la consulta.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para crear una instrucción SQL que no devuelva valores mediante un TableAdapter  
  
1.  Abra un conjunto de datos en el **Diseñador de Dataset**.  Para obtener más información, vea [Cómo: Abrir un objeto Dataset en el Diseñador de Dataset](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Si no tiene uno ya, cree un TableAdapter.  Para obtener más información sobre cómo crear TableAdapters, vea [Cómo: Crear TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Si ya tiene una consulta en el TableAdapter que utiliza una instrucción SQL y que no devuelve ningún valor, pase al procedimiento siguiente, "Para declarar una instancia del TableAdapter y ejecutar la consulta". De lo contrario, continúe con el paso 4 para crear una nueva consulta que no devuelva valores.  
  
4.  Haga clic con el botón secundario del mouse en el TableAdapter deseado y utilice el menú contextual para agregar una consulta.  
  
     El **Asistente para la configuración de consultas de TableAdapter** se abre.  
  
5.  Deje el valor predeterminado de **Usar instrucciones SQL** y, a continuación, haga clic en **Siguiente**.  
  
6.  Elija la opción **UPDATE**, **INSERT** o **DELETE** y, a continuación, haga clic en **Siguiente**.  
  
7.  Escriba su instrucción SQL o utilice el **Generador de consultas** para que le ayude a crear una y, a continuación, haga clic en **Siguiente**.  
  
8.  Proporcione un nombre para la consulta.  
  
9. Finalice el asistente; la consulta se agrega al TableAdapter.  
  
10. Compilar el proyecto.  
  
#### Para declarar una instancia de TableAdapter y ejecutar la consulta  
  
1.  Declare una instancia de TableAdapter que contenga la consulta que desea ejecutar.  
  
    -   Para crear una instancia mediante las herramientas en tiempo de diseño, arrastre el TableAdapter que desee desde el **Cuadro de herramientas**.  \(Los componentes del proyecto aparecen ahora en el **Cuadro de herramientas** debajo de un encabezado que coincide con el nombre del proyecto.\) Si el TableAdapter no aparece en el **Cuadro de herramientas**, quizá deba compilar el proyecto.  
  
         O bien  
  
    -   Para crear una instancia de código, reemplace el código siguiente con los nombres de <xref:System.Data.DataSet> y TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  La búsqueda de TableAdapters no se realiza realmente dentro de sus clases de conjunto de datos asociadas.  Cada conjunto de datos tiene una colección correspondiente de TableAdapters en su propio espacio de nombres.  Por ejemplo, si tiene un conjunto de datos denominado `SalesDataSet`, habrá un espacio de nombres `SalesDataSetTableAdapters` que contiene sus TableAdapters.  
  
2.  Llame a su consulta como llamaría a cualquier otro método del código.  Su consulta es un método de TableAdapter.  Reemplace el código siguiente con los nombres de su TableAdapter y realice la consulta.  También necesita pasar todos los parámetros requeridos por la consulta.  Si no está seguro de si su consulta requiere parámetros, o de qué parámetros requiere, compruebe IntelliSense para averiguar la firma necesaria de la consulta.  Dependiendo de si su consulta toma parámetros o no, el código se parecería al de uno de los ejemplos siguientes:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Las consultas que creemos que no devuelve ningún valor, realmente sí lo devuelven: un entero que contiene el número de filas afectadas por la consulta.  El código completo para declarar una instancia de un TableAdapter y ejecutar una consulta debe lucir similar a lo siguiente:  
  
     [!code-cs[VbRaddataFillingAndExecuting#11](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-no-value_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-no-value_1.vb)]  
  
## Ejecutar instrucciones SQL que no devuelvan valores mediante un objeto de comando  
 El ejemplo siguiente muestra cómo crear un comando y ejecutar una instrucción SQL que no devuelve valores.  Para obtener información sobre cómo configurar y obtener los valores de parámetro para un comando, vea [Cómo: Establecer y obtener parámetros para objetos de comandos](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md).  
  
 Este ejemplo utiliza el objeto <xref:System.Data.SqlClient.SqlCommand> y requiere:  
  
-   Hace referencia a los espacios de nombres <xref:System>, <xref:System.Data> y <xref:System.Xml>.  
  
-   Un conjunto de datos denominado `SqlConnection1`.  
  
-   Una tabla denominada `Customers` en el origen de datos al que se conecta `SqlConnection1`.  \(De lo contrario, necesita una instrucción SQL válida para su origen de datos.\)  
  
#### Para ejecutar una instrucción SQL que no devuelva ningún valor mediante un DataCommand  
  
-   Agregue el código siguiente a un método desde donde desee que se ejecute la instrucción SQL.  Llame al método `ExecuteNonQuery` de un comando para no devolver valores \(por ejemplo, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>\).  
  
     [!code-cs[VbRaddataFillingAndExecuting#12](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-no-value_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#12](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-no-value_2.vb)]  
  
## Seguridad de .NET Framework  
 La aplicación necesita permiso para tener acceso a la base de datos y ejecutar la instrucción SQL.  
  
## Vea también  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 [Cómo: Crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Cómo: Editar consultas de TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Cómo: Llenar un conjunto de datos con datos](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Rellenar los conjuntos de datos con datos](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Cómo: Establecer y obtener parámetros para objetos de comandos](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)