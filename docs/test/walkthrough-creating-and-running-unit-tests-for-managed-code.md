---
title: Crear y ejecutar pruebas unitarias en código administrado
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: d951c6171abd0e8cad42554c49a40cb42542fb62
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976236"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Tutorial: Crear y ejecutar pruebas unitarias en código administrado

En este artículo se recorre paso a paso la creación, ejecución y personalización de una serie de pruebas unitarias mediante el marco de pruebas unitarias para código administrado de Microsoft y el **Explorador de pruebas** de Visual Studio. Se empieza con un proyecto C# que está en desarrollo, se crean pruebas que utilizan el código, se ejecutan las pruebas y se examinan los resultados. Por último, puede cambiar el código del proyecto y volver a ejecutar las pruebas.

> [!NOTE]
> En este tutorial se utiliza el marco de pruebas unitarias de Microsoft para código administrado. El **Explorador de pruebas** también puede ejecutar pruebas de marcos de pruebas unitarias de terceros, que tienen adaptadores para el **Explorador de pruebas**. Para obtener más información, consulte [Instalar marcos de prueba unitaria de terceros](../test/install-third-party-unit-test-frameworks.md)

Para obtener información sobre cómo ejecutar pruebas desde una línea de comandos, vea [Opciones de la línea de comandos para VSTest.Console.exe](vstest-console-options.md).

## <a name="prerequisites"></a>Requisitos previos

- El proyecto del banco. Vea [Proyecto de ejemplo para crear pruebas unitarias](../test/sample-project-for-creating-unit-tests.md).

## <a name="create-a-project-to-test"></a>Crear un proyecto para pruebas

::: moniker range="vs-2017"

1. Abra Visual Studio.

2. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

   Aparecerá el cuadro de diálogo **Nuevo proyecto** .

3. Elija la plantilla de proyecto **Biblioteca de clases** de C#.

4. Asigne al proyecto el nombre **Bank** y haga clic en **Aceptar**.

   Se crea el proyecto Bank y se muestra en el **Explorador de soluciones** con el archivo *Class1.cs* abierto en el editor de código.

   > [!NOTE]
   > Si *Class1.cs* no se abre en el editor de código, haga doble clic en el archivo *Class1.cs* en el **Explorador de soluciones** para abrirlo.

::: moniker-end

::: moniker range=">=vs-2019"

1. Abra Visual Studio.

2. En la ventana de inicio, elija **Crear un proyecto nuevo**.

3. Busque la plantilla de proyecto **Biblioteca de clases** de C#, selecciónela y haga clic en **Siguiente**.

4. Asigne al proyecto el nombre **Bank** y haga clic en **Crear**.

   Se crea el proyecto Bank y se muestra en el **Explorador de soluciones** con el archivo *Class1.cs* abierto en el editor de código.

   > [!NOTE]
   > Si *Class1.cs* no se abre en el editor de código, haga doble clic en el archivo *Class1.cs* en el **Explorador de soluciones** para abrirlo.

::: moniker-end

5. Copie el código fuente del [Proyecto de ejemplo para crear pruebas unitarias](../test/sample-project-for-creating-unit-tests.md) y reemplace el contenido original de *Class1.cs* por el código copiado.

6. Guarde el archivo como *BankAccount.cs*.

7. En el menú **Compilar** , haga clic en **Compilar solución**.

Ahora tiene un proyecto denominado Bank que contiene código fuente para realizar pruebas y las herramientas necesarias para ello. El espacio de nombres de Bank, BankAccountNS, contiene la clase pública BankAccountcuyos métodos probará en los procedimientos siguientes.

En este artículo, las pruebas se centran en el método Debit. Se llama al método Debit cuando se retira dinero de una cuenta. A continuación se muestra una definición del método:

```csharp
// Method to be tested.
public void Debit(double amount)
{
    if(amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    m_balance += amount;
}
```

## <a name="create-a-unit-test-project"></a>Crear un proyecto de prueba unitaria

1. En el menú **Archivo**, seleccione **Agregar** > **Nuevo proyecto**.

   > [!TIP]
   > También puede hacer clic con el botón derecho en la solución en el **Explorador de soluciones** y elegir **Agregar** > **Nuevo proyecto**.

::: moniker range="vs-2017"

2. En el cuadro de diálogo **Nuevo proyecto**, expanda **Instalado**, expanda **Visual C#** y, después, elija **Prueba**.

3. En la lista de plantillas, seleccione **Proyecto de prueba unitaria**.

4. En el cuadro **Nombre**, escriba `BankTests` y seleccione **Aceptar**.

   El proyecto **BankTests** se agrega a la solución **Bank**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Busque la plantilla de proyecto **Proyecto de prueba unitaria** de C#, selecciónela y haga clic en **Siguiente**.

3. Dé un nombre al proyecto `BankTests`.

4. Haga clic en **Crear**.

   El proyecto **BankTests** se agrega a la solución **Bank**.

::: moniker-end

5. En el proyecto **BankTests**, agregue una referencia al proyecto **Bank**.

   En el **Explorador de soluciones**, seleccione **Referencias** en el proyecto **BankTests** y, después, seleccione **Agregar referencia** en el menú contextual.

6. En el cuadro de diálogo del **Administrador de referencia**, expanda **Solución** y active el elemento **Bank**.

## <a name="create-the-test-class"></a>Crear la clase de prueba

Cree una clase de prueba para comprobar la clase `BankAccount`. Puede utilizar el archivo *UnitTest1.cs*, generado por la plantilla de proyecto, pero asigne al archivo y a la clase nombres más descriptivos. Puede hacer esto en un solo paso cambiando el nombre del archivo en el **Explorador de soluciones**.

### <a name="rename-a-class-file"></a>Cambiar el nombre de un archivo de clase

En el **Explorador de soluciones**, seleccione el archivo *UnitTest1.cs* en el proyecto BankTests. En el menú contextual, seleccione **Cambiar nombre** y, después, cambie el nombre del archivo a *BankAccountTests.cs*. Elija **Sí** en el cuadro de diálogo en el que se le pregunta si quiere cambiar el nombre de todas las referencias al elemento de código `UnitTest1` del proyecto.

En este paso se cambia el nombre de la clase a `BankAccountTests`. El archivo *BankAccountTests.cs* contiene ahora el siguiente código:

```csharp
using System;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace BankTests
{
    [TestClass]
    public class BankAccountTests
    {
        [TestMethod]
        public void TestMethod1()
        {
        }
    }
}
```

### <a name="add-a-using-statement-to-the-project-under-test"></a>Agregar una instrucción using al proyecto en pruebas

También puede agregar una instrucción `using` a la clase para poder llamar al proyecto en pruebas, sin utilizar nombres completos. En la parte superior del archivo de clase, agregue:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Requisitos de la clase de prueba

Los requisitos mínimos para una clase de prueba son los siguientes:

- El atributo `[TestClass]` se requiere en el marco de pruebas unitarias para código administrado de Microsoft para cualquier clase que contenga métodos de prueba unitaria que desee ejecutar en el Explorador de pruebas.

- Cada método de prueba que quiera que ejecute el Explorador de pruebas debe tener el atributo `[TestMethod]`.

Puede tener otras clases de un proyecto de prueba unitaria que no tengan el atributo `[TestClass]` y puede tener otros métodos de clases de prueba que no tengan el atributo `[TestMethod]` . Puede utilizar estos otros métodos y clases en sus métodos de prueba.

## <a name="create-the-first-test-method"></a>Crear el primer método de prueba

En este procedimiento, escribirá métodos de prueba unitaria para comprobar el comportamiento del método `Debit` de la clase `BankAccount`. El método `Debit` se muestra anteriormente en este artículo.

Hay al menos tres comportamientos que deben comprobarse:

- El método produce <xref:System.ArgumentOutOfRangeException> si la cantidad de débito es mayor que el saldo.

- El método produce <xref:System.ArgumentOutOfRangeException> si la cantidad de débito es menor que cero.

- Si la cantidad de débito es válida, el método resta la cantidad de débito del saldo de cuenta.

> [!TIP]
> Puede eliminar el método `TestMethod1` predeterminado, ya que no lo usará en este tutorial.

### <a name="to-create-a-test-method"></a>Para crear un método de prueba

En la primera prueba, se comprueba que una cantidad válida (es decir, una menor que el saldo de cuenta y mayor que cero) retire la cantidad correcta de la cuenta. Agregue el siguiente método a esa clase `BankAccountTests` :

```csharp
[TestMethod]
public void Debit_WithValidAmount_UpdatesBalance()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 4.55;
    double expected = 7.44;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert
    double actual = account.Balance;
    Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
}
```

El método es sencillo: configura un nuevo objeto `BankAccount` con un saldo inicial y después se retira una cantidad válida. Usa el método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> para comprobar que el saldo de cierre es el esperado.

### <a name="test-method-requirements"></a>Requisitos del método de prueba

Un método de prueba debe cumplir los siguientes requisitos:

- Es representativo del atributo `[TestMethod]`.

- Devuelve `void`.

- No puede tener parámetros.

## <a name="build-and-run-the-test"></a>Compilar y ejecutar la prueba

1. En el menú **Compilar** , elija **Compilar solución**.

   Si no hay ningún error, aparece el **Explorador de pruebas** con **Debit_WithValidAmount_UpdatesBalance** incluido en el grupo **Pruebas no ejecutadas**.

   > [!TIP]
   > Si el **Explorador de pruebas** no aparece tras realizar una compilación correcta, elija **Prueba** en el menú, luego **Ventanas** y, después, **Explorador de pruebas**.

2. Elija **Ejecutar todas** para ejecutar la prueba. Mientras se ejecuta la prueba, la barra de estado en la parte superior de la ventana se anima. Al final de la serie de pruebas, la barra se vuelve verde si todos los métodos de prueba se completan correctamente o roja si no alguna de las prueba no lo hace.

3. En este caso, la prueba no se completa correctamente. El método de prueba se mueve al grupo **Pruebas no superadas**. Seleccione el método en el **Explorador de pruebas** para ver los detalles en la parte inferior de la ventana.

## <a name="fix-your-code-and-rerun-your-tests"></a>Corrija el código y vuelva a ejecutar las pruebas

### <a name="analyze-the-test-results"></a>Analizar los resultados de pruebas

El resultado de la prueba contiene un mensaje que describe el error. Para el método `AreEqual`, el mensaje muestra lo que se esperaba (el parámetro **Expected\<*value*>**) y lo que se recibió realmente (el parámetro **Actual\<*value*>**). Esperaba que se redujera el saldo pero, en su lugar, aumentó en la cantidad retirada.

La prueba unitaria puso al descubierto un error: la cantidad retirada se *agrega* al saldo de cuenta en lugar de ser *restada*.

### <a name="correct-the-bug"></a>Corregir el error

Para corregir el error, reemplace la línea:

```csharp
m_balance += amount;
```

Por:

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Vuelva a ejecutar la prueba

En el **Explorador de pruebas**, elija **Ejecutar todas** para volver a ejecutar la prueba. La barra de color rojo o verde se vuelve verde para indicar que se ha superado la prueba, y la prueba se mueve al grupo de **Pruebas superadas**.

## <a name="use-unit-tests-to-improve-your-code"></a>Utilice pruebas unitarias para mejorar el código

En esta sección se describe cómo un proceso iterativo de análisis, el desarrollo de pruebas unitarias y la refactorización pueden servirle de ayuda para que el código de producción sea más compacto y eficaz.

### <a name="analyze-the-issues"></a>Analizar los problemas

Ha creado un método de prueba para confirmar que se resta correctamente una cantidad válida en el método `Debit`. Ahora, compruebe que el método produce <xref:System.ArgumentOutOfRangeException> si la cantidad de débito es:

- mayor que el saldo, o
- menor que cero.

### <a name="create-the-test-methods"></a>Crear los métodos de prueba

Cree un método de prueba para comprobar que el comportamiento es el correcto cuando la cantidad de débito es menor que cero:

```csharp
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert is handled by the ExpectedException attribute on the test method.
}
```

Use el atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> para validar que se ha producido la excepción correcta. El atributo hace que la prueba dé un error a menos que se produzca <xref:System.ArgumentOutOfRangeException> . Si modifica temporalmente el método en pruebas para que produzca una excepción <xref:System.ApplicationException> más genérica cuando la cantidad de débito es menor que cero, la prueba se comporta correctamente&mdash;es decir, se produce un error.

Para probar el caso en el que la cantidad retirada es mayor que el saldo, siga los siguientes pasos:

1. Crear un nuevo método de prueba denominado `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.

2. Copiar el cuerpo del método de `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` en el nuevo método.

3. Establecer `debitAmount` en un número mayor que el del saldo.

### <a name="run-the-tests"></a>Ejecutar las pruebas

Al ejecutar los dos métodos de prueba se muestra que las pruebas funcionan correctamente.

### <a name="continue-the-analysis"></a>Continuar el análisis

Pero los dos últimos métodos de prueba también son problemáticos. No puede saber qué condición del método en pruebas inicia la excepción cuando se ejecuta cualquier prueba. Alguna forma de diferenciar las dos condiciones, que es una cantidad de débito negativo o una cantidad mayor que el saldo, aumentaría la confianza en las pruebas.

Examine de nuevo el método en pruebas y compruebe que ambas instrucciones condicionales utilizan un constructor `ArgumentOutOfRangeException` que tan solo toma el nombre del argumento como parámetro:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

Puede usar un constructor que proporcione información mucho más completa: <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> incluye el nombre y el valor del argumento, y un mensaje definido por el usuario. Puede refactorizar el método en pruebas para utilizar este constructor. Incluso mejor, puede utilizar miembros de tipo que se encuentran disponibles públicamente para especificar los errores.

### <a name="refactor-the-code-under-test"></a>Refactorizar el código en pruebas

Primero, defina dos constantes para los mensajes de error en el ámbito de la clase. Colóquelas en la clase sometida a prueba, BankAccount:

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

A continuación, modifique las dos instrucciones condicionales en el método `Debit`:

```csharp
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
```

### <a name="refactor-the-test-methods"></a>Refactorizar los métodos de prueba

Quite el atributo`ExpectedException` del método de prueba y, en su lugar, capture la excepción y compruebe el mensaje asociado. El método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> ofrece la posibilidad de comparar dos cadenas.

Por tanto, `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` quedaría de la siguiente manera:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>Vuelva a probar, reescriba y vuelva a analizar

Suponga que hay un error en el método en pruebas y el método `Debit` ni siquiera inicia una excepción <xref:System.ArgumentOutOfRangeException>, ni tampoco muestra el mensaje correcto con la excepción. Actualmente, el método de prueba no trata este caso. Si el valor de `debitAmount` es válido (es decir, menor que el saldo pero mayor que cero), no se detecta ninguna excepción, por lo que la comprobación nunca se desencadena. Sí, el método de prueba se completa correctamente. Esto no es bueno, porque quiere que el método de prueba no se supere si no se produce ninguna excepción.

Se trata de un error en el método de prueba. Para resolver el problema, agregue una validación <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> al final del método de prueba para controlar el caso donde no se produce ninguna excepción.

Pero, al volver a ejecutar la prueba, se muestra que se *produce un error* en la prueba si se detecta la excepción correcta. El bloque `catch` detecta la excepción, pero el método sigue ejecutándose y se produce un error en el nueva comprobación de <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A>. Para resolver este problema, agregue una instrucción `return` después de `StringAssert` en el bloque `catch`. Al volver a ejecutar la prueba, se confirma que ha resuelto este problema. La versión final de `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` tiene el siguiente aspecto:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

Las mejoras en el código de prueba condujeron a métodos de prueba más eficaces e informativos. Pero lo que es más importante, también mejoraron el código sometido a prueba.
