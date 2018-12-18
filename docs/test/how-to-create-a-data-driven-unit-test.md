---
title: 'Cómo: Crear una prueba unitaria controlada por datos en Visual Studio'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a05729efcc475fa99026d99abc24d09c2511a2b7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939259"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Cómo: Crear una prueba unitaria controlada por datos

Mediante el marco de pruebas unitarias de Microsoft para código administrado, puede configurar un método de prueba unitaria para recuperar los valores utilizados en el método de prueba de un origen de datos. El método se ejecuta correctamente para cada fila del origen de datos, lo que facilita probar una variedad de entrada mediante el uso de un único método.

Crear una prueba unitaria controlada por datos implica los siguientes pasos:

1.  Crear un origen de datos que contiene los valores que se utilizan en el método de prueba. El origen de datos puede ser cualquier tipo que está registrado en el equipo que ejecuta la prueba.

2.  Agregue un campo privado <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> y una propiedad pública `TestContext` a la clase de prueba.

3.  Cree un método de prueba unitaria y agréguele un atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>.

4.  Use la propiedad de indexador <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> para recuperar los valores que se usan en una prueba.

##  <a name="BKMK_The_method_under_test"></a> El método sometido a prueba

Por ejemplo, supongamos que ha creado:

1.  Una solución denominada `MyBank` que acepta y procesa las transacciones para diferentes tipos de cuentas.

2.  Un proyecto en `MyBank` llamado `BankDb` que administra las transacciones para las cuentas.

3.  Una clase denominada `Maths` en el `DbBank` proyecto que realiza las funciones matemáticas para asegurarse de que cualquier transacción es una ventaja para el banco.

4.  Un proyecto de prueba unitaria denominado `BankDbTests` para probar el comportamiento del componente `BankDb`.

5.  Una clase unitaria de denominada `MathsTests` para probar el comportamiento de la clase `Maths`.

Probaremos un método en `Maths` que agrega dos enteros mediante un bucle:

```csharp
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

##  <a name="create-a-data-source"></a>Crear un origen de datos
 Para probar el método `AddIntegers`, cree un origen de datos que especifica un intervalo de valores para los parámetros y la suma que se espera que se devuelva. En este ejemplo, crearemos una base de datos de SQL Compact denominada `MathsData` y una tabla denominada `AddIntegersData` que contiene los siguientes nombres de columna y valores:

|FirstNumber|SecondNumber|Sum|
|-|------------------|-|
|0|1|1|
|1|1|2|
|2|-3|-1|

##  <a name="add-a-testcontext-to-the-test-class"></a>Agregar un TestContext para la clase de prueba
 El marco de pruebas unitarias crea un objeto `TestContext` para almacenar la información de origen de datos para una prueba controlada por datos. Después, el marco de trabajo establece este objeto como el valor de la propiedad `TestContext` que crea.

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

 En el método de prueba, accede a los datos a través de la propiedad de indizador `DataRow` del `TestContext`.

##  <a name="write-the-test-method"></a>Escribir el método de prueba
 El método de prueba para `AddIntegers` es bastante sencillo. Para cada fila del origen de datos, llame a `AddIntegers` con los valores de columna **FirstNumber** y **SecondNumber** como parámetros y compruebe el valor devuelto con el valor de columna **Sum**:

```csharp
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

El método `Assert` incluye un mensaje que muestra los valores `x` y `y` de una iteración con error. De forma predeterminada, los valores de aserción, `expected` y `actual`, ya están incluidos en los detalles de una prueba no superada.

###  <a name="BKMK_Specifying_the_DataSourceAttribute"></a> Especificar el DataSourceAttribute
 El atributo `DataSource` especifica la cadena de conexión para el origen de datos y el nombre de la tabla que se utiliza en el método de prueba. La información exacta de la cadena de conexión es diferente, dependiendo de qué tipo de origen de datos está utilizando. En este ejemplo, se utiliza una base de datos de SqlServerCe.

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

El atributo de origen de datos tiene tres constructores.

```csharp
[DataSource(dataSourceSettingName)]
```

 Un constructor con un parámetro usa la información de conexión que se almacena en el archivo *app.config* para la solución. El *dataSourceSettingsName* es el nombre del elemento Xml en el archivo de configuración que especifica la información de conexión.

 Un archivo *app.config* permite cambiar la ubicación del origen de datos sin realizar cambios en la propia prueba unitaria. Para obtener información sobre cómo crear y utilizar un archivo *app.config*, vea [Tutorial: Usar un archivo de configuración para definir un origen de datos](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

```csharp
[DataSource(connectionString, tableName)]
```

 El constructor `DataSource` con dos parámetros especifica la cadena de conexión para el origen de datos y el nombre de la tabla que contiene los datos para el método de prueba.

 Las cadenas de conexión dependen del tipo de origen de datos, pero debe contener un elemento de proveedor que especifique el nombre invariable del proveedor de datos.

```csharp
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

###  <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> Usar TestContext.DataRow para tener acceso a los datos
 Para obtener acceso a los datos de la tabla `AddIntegersData`, utilice el indizador `TestContext.DataRow`. `DataRow` es un objeto <xref:System.Data.DataRow>, por lo que se recuperan valores de columna mediante los nombres de columna o índice. Dado que los valores se devuelven como objetos, es necesario convertirlos al tipo adecuado:

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

##  <a name="run-the-test-and-view-results"></a>Ejecutar la prueba y ver los resultados
 Cuando haya terminado de escribir un método de prueba, compile el proyecto de prueba. El método de prueba aparece en la ventana **Explorador de pruebas** en el grupo **Pruebas no ejecutadas**. Al ejecutar, escribir y volver a ejecutar las pruebas, el **Explorador de pruebas** muestra los resultados en los grupos de **Pruebas no superadas**, **Pruebas superadas** y **Pruebas no ejecutadas**. Se puede elegir **Ejecutar todas** para ejecutar todas las pruebas o bien **Ejecutar** para elegir un subconjunto de pruebas que se desea ejecutar.

 Se anima la barra de resultados de pruebas en la parte superior del explorador cuando se ejecuta la prueba. Al final de la serie de pruebas, la barra será verde si todas las pruebas se completaron correctamente o roja si no alguna de las pruebas no lo hace. Un resumen de la ejecución de la prueba aparece en el panel de detalles de la parte inferior de la ventana **Explorador de pruebas**. Seleccione una prueba para ver los detalles de esa prueba en el panel inferior.

 Si ha ejecutado el método `AddIntegers_FromDataSourceTest` del ejemplo, la barra de resultados se vuelve roja y el método de prueba se mueve al grupo **Pruebas no superadas**. Se produce un error en una prueba controlada por datos si se produce un error en cualquiera de los métodos iterados del origen de datos. Al elegir una prueba controlada por datos con errores en la ventana **Explorador de pruebas**, en el panel de detalles se muestran los resultados de cada iteración que se identifica mediante el índice de fila de datos. En nuestro ejemplo, parece que el algoritmo `AddIntegers` no controla correctamente los valores negativos.

 Cuando el método de prueba se ha corregido y la prueba se ejecuta de nuevo, la barra de resultados se vuelve verde y el método de prueba se mueve al grupo **Pasa la prueba**.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)
- [Ejecutar pruebas unitarias con el Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md)
- [Escribir pruebas unitarias para .NET Framework con el Framework de pruebas unitarias de Microsoft para código administrado](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)