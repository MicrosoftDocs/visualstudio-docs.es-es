---
title: "C&#243;mo: Ejecutar un procedimiento almacenado que devuelve un &#250;nico valor | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CommandType.StoredProcedure"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "ExecuteReader (ejemplo del método) [Visual Basic]"
  - "procedimientos almacenados, ejemplos"
  - "procedimientos almacenados, ejecutar"
ms.assetid: ecf8c262-58ca-4a69-a82c-916c0c061422
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Ejecutar un procedimiento almacenado que devuelve un &#250;nico valor
Para ejecutar un procedimiento almacenado que devuelve un solo valor, puede ejecutar una consulta de TableAdapter configurada para ejecutar un procedimiento almacenado \(por ejemplo, `CustomersTableAdapter.CustomerCount()`\).  
  
 Si su aplicación no utiliza TableAdapters, llame al método `ExecuteScalar` en un objeto de comando, estableciendo su propiedad `CommandType` en <xref:System.Data.CommandType>.  \(El objeto "Command"" hace referencia al comando concreto para el [Proveedor de datos de .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md) que utiliza su aplicación.  Por ejemplo, si su aplicación utiliza el proveedor de datos de .NET Framework para el servidor SQL Server, el objeto de comando sería <xref:System.Data.SqlClient.SqlCommand>.\)  
  
 Los ejemplos siguientes muestran cómo ejecutar procedimientos almacenados que devuelven valores únicos de una base de datos utilizando TableAdapters u objetos de comando.  Para obtener más información sobre cómo realizar consultas con TableAdapters y comandos, vea [Rellenar los conjuntos de datos con datos](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Ejecutar procedimientos almacenados que devuelven valores únicos utilizando un TableAdapter  
 Este ejemplo muestra cómo crear una consulta de TableAdapter mediante [Asistente para la configuración de consultas de TableAdapter](../data-tools/editing-tableadapters.md) y, a continuación, proporciona información acerca de cómo declarar una instancia de TableAdapter y ejecutar la consulta.  
  
#### Para ejecutar un procedimiento almacenado que devuelve un valor único mediante un TableAdapter  
  
1.  Abra un conjunto de datos en el **Diseñador de Dataset**.  Para obtener más información, vea [Cómo: Abrir un objeto Dataset en el Diseñador de Dataset](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Si no tiene uno ya, cree un TableAdapter.  Para obtener más información sobre cómo crear TableAdapters, vea [Cómo: Crear TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Si ya tiene una consulta en su TableAdapter que utiliza un procedimiento almacenado para devolver un valor único, omita el procedimiento siguiente, "Para declarar una instancia de TableAdapter y ejecutar la consulta". De lo contrario, continúe con el paso 4 para crear una nueva consulta que devuelva un valor único.  
  
4.  Haga clic con el botón secundario del mouse en el TableAdapter deseado y utilice el menú contextual para agregar una consulta.  
  
     El **Asistente para la configuración de consultas de TableAdapter** se abre.  
  
5.  Seleccione **Usar el procedimiento almacenado existente** y, a continuación, haga clic en **Siguiente**.  
  
6.  Seleccione un procedimiento almacenado en la lista desplegable y, a continuación, haga clic en **Siguiente**.  
  
7.  Seleccione la opción para que devuelva **Un solo valor** y, a continuación, haga clic en **Siguiente**.  
  
8.  Proporcione un nombre para la consulta.  
  
9. Haga clic en **Siguiente** o en **Finalizar** para finalizar el asistente; la consulta se agrega al TableAdapter.  
  
10. Compilar el proyecto.  
  
#### Para declarar una instancia de TableAdapter y ejecutar la consulta  
  
1.  Declare una instancia de TableAdapter que contenga la consulta que desea ejecutar.  
  
    -   Para crear una instancia mediante las herramientas en tiempo de diseño, arrastre el TableAdapter que desee desde el **Cuadro de herramientas**.  \(Los componentes del proyecto aparecen ahora en el **Cuadro de herramientas** debajo de un encabezado que coincide con el nombre del proyecto.\) Si el TableAdapter no aparece en el **Cuadro de herramientas**, quizá deba compilar el proyecto.  
  
         O bien  
  
    -   Para crear una instancia de código, reemplace el código siguiente con los nombres de <xref:System.Data.DataSet> y TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  La búsqueda de TableAdapters no se realiza realmente dentro de sus clases de conjunto de datos asociadas.  Cada conjunto de datos tiene una colección correspondiente de TableAdapters en su propio espacio de nombres.  Por ejemplo, si tiene un conjunto de datos denominado `SalesDataSet`, habrá un espacio de nombres `SalesDataSetTableAdapters` que contiene sus TableAdapters.  
  
2.  Llame a su consulta como llamaría a cualquier otro método del código.  Su consulta es un método de TableAdapter.  Reemplace el código siguiente con los nombres de su TableAdapter y realice la consulta.  También necesitará pasar cualquier parámetro requerido por su consulta.  Si no está seguro de si su consulta requiere parámetros, o de qué parámetros requiere, compruebe IntelliSense para averiguar la firma necesaria de la consulta.  Dependiendo de si su consulta toma parámetros o no, el código se parecería al de uno de los ejemplos siguientes:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     El código completo para declarar una instancia de TableAdapter y ejecutar la consulta debe parecerse al siguiente:  
  
     [!code-cs[VbRaddataFillingAndExecuting#9](../data-tools/codesnippet/CSharp/how-to-execute-a-stored-procedure-that-returns-a-single-value_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../data-tools/codesnippet/VisualBasic/how-to-execute-a-stored-procedure-that-returns-a-single-value_1.vb)]  
  
## Ejecutar procedimientos almacenados que devuelven valores únicos utilizando un objeto de comando  
 El ejemplo siguiente muestra cómo crear un comando y ejecutar un procedimiento almacenado que devuelve un solo valor.  Para obtener información sobre cómo configurar y obtener los valores de parámetro para un comando, vea [Cómo: Establecer y obtener parámetros para objetos de comandos](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md).  
  
 Este ejemplo utiliza el objeto <xref:System.Data.SqlClient.SqlCommand> y requiere:  
  
-   Hace referencia a los espacios de nombres <xref:System>, <xref:System.Data> y <xref:System.Xml>.  
  
-   Un conjunto de datos denominado `SqlConnection1`.  
  
-   Una tabla denominada `Customers` en el origen de datos al que se conecta `SqlConnection1`.  \(De lo contrario, necesita una instrucción SQL válida para su origen de datos.\)  
  
#### Para ejecutar un procedimiento almacenado que devuelve un valor único mediante un DataCommand  
  
-   Agregue el código siguiente a un método desde el que desee ejecutar el código.  Puede devolver valores únicos si llama al método `ExecuteScalar` de un comando \(por ejemplo, <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>\).  Los datos se devuelven en un `object`.  
  
     [!code-cs[VbRaddataFillingAndExecuting#14](../data-tools/codesnippet/CSharp/how-to-execute-a-stored-procedure-that-returns-a-single-value_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#14](../data-tools/codesnippet/VisualBasic/how-to-execute-a-stored-procedure-that-returns-a-single-value_2.vb)]  
  
## Vea también  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteScalar%2A?displayProperty=fullName>   
 [Cómo: Crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Cómo: Editar consultas de TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Cómo: Llenar un conjunto de datos con datos](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Rellenar los conjuntos de datos con datos](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Cómo: Establecer y obtener parámetros para objetos de comandos](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)