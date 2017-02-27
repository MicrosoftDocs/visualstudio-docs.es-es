---
title: "C&#243;mo: Crear una prueba unitaria controlada por datos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.test.testresults.unittest.datadriven"
  - "vs.test.testresults.unittest.datadriven.failure"
helpviewer_keywords: 
  - "pruebas unitarias, ejecución"
  - "pruebas unitarias, orientadas a datos"
  - "pruebas unitarias orientadas a datos"
ms.assetid: a0322bc5-02c8-4f9f-af43-100a60b1bd28
caps.latest.revision: 33
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 33
---
# C&#243;mo: Crear una prueba unitaria controlada por datos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mediante el marco de pruebas unitarias de Microsoft para el código administrado, se puede configurar un método de pruebas unitarias para recuperar los valores utilizados en el método de un origen de datos.  El método se ejecuta consecutivamente para cada fila del origen de datos, que facilita probar una variedad de entradas utilizando un único método.  
  
 Este tema contiene las siguientes secciones:  
  
-   [El método en pruebas](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)  
  
-   [Crear un origen de datos](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)  
  
-   [Agregar un TestContext a la clase de prueba](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)  
  
-   [Escritura del método de prueba](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)  
  
    -   [Especificar el DataSourceAttribute](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)  
  
    -   [Mediante TestContext.DataRow para obtener acceso a los datos](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)  
  
-   [Ejecutar pruebas y ver los resultados](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)  
  
 Crear una prueba unitaria controlada por datos implica los pasos siguientes:  
  
1.  Crear un origen de datos que contiene los valores que se utilizan en el método de prueba.  El origen de datos puede ser cualquier tipo registrado en el equipo que ejecuta la prueba.  
  
2.  Agregue un campo privado <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> y una propiedad pública `TestContext` a la clase de prueba.  
  
3.  Cree un método de prueba unitaria y agregue un atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> a ésta.  
  
4.  Utilice la propiedad de indizador <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> para recuperar los valores que se utilizan en una prueba.  
  
##  <a name="BKMK_The_method_under_test"></a> El método en pruebas  
 Como ejemplo, supongamos que hemos creado:  
  
1.  Una solución denominada `MyBank` que acepta y procesa las transacciones para distintos tipos de cuentas.  
  
2.  Un proyecto en `MyBank` denominado `BankDb` que administra las transacciones de las cuentas.  
  
3.  Una clase denominada `Maths` en el proyecto `DbBank` que realiza las funciones matemáticas para asegurarse de que cualquier transacción es ventajosa para el banco.  
  
4.  Un proyecto de prueba unitaria denominado `BankDbTests` para probar el comportamiento del componente `BankDb`.  
  
5.  Una clase de pruebas unitarias denominada `MathsTests` para comprobar el comportamiento de la clase `Maths`.  
  
 Probaremos un método en `Maths` que agregue dos enteros utilizando un bucle:  
  
```  
public int AddIntegers(int first, int second)  
{  
    int sum = first;  
    for( int i = 0; i < second; i++)  
    {  
        sum += 1;  
    }  
    return sum;  
}  
```  
  
##  <a name="BKMK_Creating_a_data_source"></a> Crear un origen de datos  
 Para probar el método `AddIntegers`, creamos un origen de datos que especifique un intervalo de valores para los parámetros y la suma que espera devolverse.  En nuestro ejemplo, creamos un acuerdo `MathsData` denominado base de datos de SQL y una tabla denominada `AddIntegersData` que contiene los nombres de columna y los valores siguientes  
  
|FirstNumber|SecondNumber|Sum|  
|-----------------|------------------|---------|  
|0|1|1|  
|1|1|2|  
|2|\-3|\-1|  
  
##  <a name="BKMK_Adding_a_TestContext_to_the_test_class"></a> Agregar un TestContext a la clase de prueba  
 El marco de pruebas unitarias crea un objeto `TestContext` para almacenar información de origen de datos para una prueba controlada por datos.  El marco, a continuación, establece este objeto como valor de la propiedad `TestContext` que creamos.  
  
```  
  
private TestContext testContextInstance;  
public TestContext TestContext  
{  
    get { return testContextInstance; }  
    set { testContextInstance = value; }  
}  
  
```  
  
 En el método de prueba, se tiene acceso a los datos a través de la propiedad de indizador `DataRow` de `TestContext`.  
  
##  <a name="BKMK_Writing_the_test_method"></a> Escritura del método de prueba  
 El método de prueba para `AddIntegers` es bastante simple.  Para cada fila del origen de datos, denominamos `AddIntegers` con los valores de columna de **FirstNumber** y de **SecondNumber** como parámetros y comprobamos el valor devuelto con valor de columna de **suma** :  
  
```  
  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0; Data Source=C:\Data\MathsData.sdf;", "Numbers")]  
[TestMethod()]  
public void AddIntegers_FromDataSourceTest()  
{  
    var target = new Maths();  
  
    // Access the data  
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);   
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);  
    int actual = target.IntegerMethod(x, y);  
    Assert.AreEqual(expected, actual,  
        "x:<{0}> y:<{1}>",  
        new object[] {x, y});  
  
}  
  
```  
  
 Observe que el método `Assert` incluye un mensaje que muestra los valores `x` e `y` de una iteración errónea.  De forma predeterminada, los valores afirmados, `expected` y `actual`, están ya incluidos en los detalles de una prueba no superada.  
  
###  <a name="BKMK_Specifying_the_DataSourceAttribute"></a> Especificar el DataSourceAttribute  
 El atributo `DataSource` especifica la cadena de conexión para el origen de datos y el nombre de la tabla que se utiliza en el método de prueba.  La información exacta de la cadena de conexión varía, dependiendo de qué tipo de origen de datos se utilice.  En este ejemplo, utilizamos una base de datos SqlServerCe.  
  
```  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]  
```  
  
 El atributo DataSource tiene tres constructores.  
  
```  
[DataSource(dataSourceSettingName)]  
```  
  
 Un constructor con un parámetro utiliza la información de conexión que se almacena en el archivo app.config para la solución.  *dataSourceSettingsName* es el nombre del elemento XML en el archivo de configuración que especifica la información de conexión.  
  
 Mediante un archivo app.config se permite cambiar la ubicación del origen de datos sin realizar cambios en la propia prueba unitaria.  Para obtener información sobre cómo crear y utilizar un archivo app.config, consulte [Tutorial: Utilizar un archivo de configuración para definir un origen de datos](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).  
  
```  
[DataSource(connectionString, tableName)]  
```  
  
 El constructor `DataSource` con dos parámetros especifica la cadena de conexión para el origen de datos y el nombre de la tabla que contiene los datos para el método de prueba.  
  
 Las cadenas de conexión dependen del tipo de origen de datos, pero debe contener un elemento del proveedor que especifique el nombre invariable del proveedor de datos.  
  
```  
[DataSource(  
    dataProvider,   
    connectionString,   
    tableName,  
    dataAccessMethod  
    )]  
```  
  
###  <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> Mediante TestContext.DataRow para obtener acceso a los datos  
 Para obtener acceso a los datos en `AddIntegersData`, utilice el indizador de `TestContext.DataRow` .  `DataRow` es un objeto <xref:System.Data.DataRow>, por lo que recuperamos valores de columnas por índice o nombres de columna.  Dado que los valores se devuelven como objetos, necesitamos convertirlos al tipo adecuado:  
  
```  
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
  
```  
  
##  <a name="BKMK_Running_the_test_and_viewing_results"></a> Ejecutar pruebas y ver los resultados  
 Cuando termine de escribir un método de prueba, compile el proyecto de prueba.  El método de prueba aparece en la ventana del Explorador de pruebas en el grupo de **Pruebas no ejecutadas** .  A medida que ejecuta, escribe y vuelve a ejecutar las pruebas, el Explorador de pruebas muestra los resultados en los grupos **Pruebas no superadas**, **Pruebas superadas** y **Pruebas no ejecutadas**.  Puede elegir **Ejecutar todas** para ejecutar todas las pruebas o elija **Ejecutar...** para elegir un subconjunto de prueba se vaya a ejecutar.  
  
 La barra de resultados de pruebas en la parte superior del Explorador se anima a medida que se ejecutan las pruebas.  Al final de la serie de pruebas, la barra se vuelve verde si todas las pruebas se han superado o roja si no se ha superado cualquiera de las pruebas.  Un resumen de la serie de pruebas aparece en el panel de detalles en la parte inferior de la ventana del Explorador de pruebas.  Seleccione una prueba para ver los detalles de esa prueba en el panel inferior.  
  
 Si ejecutó el método `AddIntegers_FromDataSourceTest` en nuestro ejemplo, la barra de resultados cambia a color rojo y el método de prueba se mueve a los errores dirigidos por datos a la prueba de **Pruebas no superadas** si hay métodos iterados cualquiera de los del origen de datos.  Cuando se elige una prueba controlada por datos incorrectos en la ventana del Explorador de pruebas, el panel de detalles muestra los resultados de cada iteración que se identifica mediante el índice de la fila de datos.  En nuestro ejemplo, aparecerá que el algoritmo `AddIntegers` no controla los valores negativos correctamente.  
  
 Cuando el método en pruebas es corregido y se vuelven a ejecutar las pruebas, la barra de resultados se vuelve verde y el método de pruebas se mueve al grupo **Pruebas superadas** .  
  
## Vea también  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>   
 [Cómo: Crear y ejecutar una prueba unitaria](http://msdn.microsoft.com/es-es/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48)   
 [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)   
 [Ejecutar pruebas unitarias con el Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md)   
 [Escribir pruebas unitarias para .NET Framework con el Framework de pruebas unitarias de Microsoft código administrado](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)