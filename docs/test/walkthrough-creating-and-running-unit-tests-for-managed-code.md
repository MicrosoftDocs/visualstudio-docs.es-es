---
title: Tutorial de prueba unitaria de C#
description: Aprenda a crear, ejecutar y personalizar una serie de pruebas unitarias mediante el marco de pruebas unitarias de Microsoft para usarlas con el código administrado y el Explorador de pruebas de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/14/2019
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: 264744d7fe39c77da625c778d1bfea51f55e1f2d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948015"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Tutorial: Crear y ejecutar pruebas unitarias en código administrado

En este artículo se recorre paso a paso la creación, ejecución y personalización de una serie de pruebas unitarias mediante el marco de pruebas unitarias para código administrado de Microsoft y el **Explorador de pruebas** de Visual Studio. Se empieza con un proyecto C# que está en desarrollo, se crean pruebas que utilizan el código, se ejecutan las pruebas y se examinan los resultados. Luego se cambia el código del proyecto y se vuelven a ejecutar las pruebas.



## <a name="create-a-project-to-test"></a>Crear un proyecto para pruebas

::: moniker range="vs-2017"

1. Abra Visual Studio.

2. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

   Aparecerá el cuadro de diálogo **Nuevo proyecto** .

3. En la categoría **Visual C#** > **.NET Core**, elija la plantilla de proyecto **Aplicación de consola (.NET Core)** .

4. Asigne al proyecto el nombre **Bank** y haga clic en **Aceptar**.

   Se crea el proyecto Bank y se muestra en el **Explorador de soluciones** con el archivo *Program.cs* abierto en el editor de código.

   > [!NOTE]
   > Si *Program.cs* no se abre en el editor, haga doble clic en el archivo *Program.cs* en el **Explorador de soluciones** para abrirlo.

::: moniker-end

::: moniker range=">=vs-2019"

1. Abra Visual Studio.

2. En la ventana de inicio, elija **Crear un proyecto nuevo**.

3. Busque y seleccione la plantilla de proyecto de C# **Aplicación de consola (.NET Core)** y haga clic en **Siguiente**.

4. Asigne al proyecto el nombre **Bank** y haga clic en **Crear**.

   Se crea el proyecto Bank y se muestra en el **Explorador de soluciones** con el archivo *Program.cs* abierto en el editor de código.

   > [!NOTE]
   > Si *Program.cs* no se abre en el editor, haga doble clic en el archivo *Program.cs* en el **Explorador de soluciones** para abrirlo.

::: moniker-end

5. Reemplace el contenido de *Program.cs* por el siguiente código de C# que define una clase, *BankAccount*:

   ```csharp
   using System;

   namespace BankAccountNS
   {
       /// <summary>
       /// Bank account demo class.
       /// </summary>
       public class BankAccount
       {
           private readonly string m_customerName;
           private double m_balance;

           private BankAccount() { }

           public BankAccount(string customerName, double balance)
           {
               m_customerName = customerName;
               m_balance = balance;
           }

           public string CustomerName
           {
               get { return m_customerName; }
           }

           public double Balance
           {
               get { return m_balance; }
           }

           public void Debit(double amount)
           {
               if (amount > m_balance)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount; // intentionally incorrect code
           }

           public void Credit(double amount)
           {
               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount;
           }

           public static void Main()
           {
               BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);

               ba.Credit(5.77);
               ba.Debit(11.22);
               Console.WriteLine("Current balance is ${0}", ba.Balance);
           }
       }
   }
   ```

6. Cambie el nombre del archivo a *BankAccount.cs* al hacer clic con el botón derecho y elegir **Cambiar nombre** en el **Explorador de soluciones**.

7. En el menú **Compilación**, haga clic en **Compilar solución** (o presione **CTRL** + **Mayús** + **B**).

Ahora tiene un proyecto con métodos que puede probar. En este artículo, las pruebas se centran en el método `Debit`. Se llama al método `Debit` cuando se retira dinero de una cuenta.

## <a name="create-a-unit-test-project"></a>Crear un proyecto de prueba unitaria

1. En el menú **Archivo**, seleccione **Agregar** > **Nuevo proyecto**.

   > [!TIP]
   > También puede hacer clic con el botón derecho en la solución en el **Explorador de soluciones** y elegir **Agregar** > **Nuevo proyecto**.

::: moniker range="vs-2017"

2. En el cuadro de diálogo **Nuevo proyecto**, expanda **Instalado**, expanda **Visual C#** y, después, elija **Prueba**.

3. En la lista de plantillas, seleccione **Proyecto de prueba de MSTest (.NET Core)** .

4. En el cuadro **Nombre**, escriba `BankTests` y seleccione **Aceptar**.

   El proyecto **BankTests** se agrega a la solución **Bank**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Busque y seleccione la plantilla de proyecto **Proyecto de prueba de MSTest (.NET Core)** de C# y haga clic en **Siguiente**.

3. Ponga al proyecto el nombre **BankTests**.

4. Haga clic en **Crear**.

   El proyecto **BankTests** se agrega a la solución **Bank**.

::: moniker-end

5. En el proyecto **BankTests**, agregue una referencia al proyecto **Bank**.

   En el **Explorador de soluciones**, seleccione **Dependencias** en el proyecto **BankTests** y luego seleccione **Agregar referencia** en el menú contextual.

6. En el cuadro de diálogo **Administrador de referencias**, expanda **Proyectos**, seleccione **Solución** y active el elemento **Bank**.

7. Elija **Aceptar**.

## <a name="create-the-test-class"></a>Crear la clase de prueba

Cree una clase de prueba para comprobar la clase `BankAccount`. Puede utilizar el archivo *UnitTest1.cs*, generado por la plantilla de proyecto, pero asigne al archivo y a la clase nombres más descriptivos.

### <a name="rename-a-file-and-class"></a>Cambio de nombre de un archivo y una clase

1. Para cambiar el nombre del archivo, en el **Explorador de soluciones**, seleccione el archivo *UnitTest1.cs* del proyecto BankTests. En el menú contextual, seleccione **Cambiar nombre** (o presione **F2**) y cambie el nombre del archivo a *BankAccountTests.cs*.

::: moniker range="vs-2017"

2. Para cambiar el nombre de la clase, seleccione **Sí** en el cuadro de diálogo que aparece y le pregunta si quiere cambiar también el nombre de las referencias al elemento de código.

::: moniker-end

::: moniker range=">=vs-2019"

2. Para cambiar el nombre de la clase, sitúe el cursor sobre `UnitTest1` en el editor de código, haga clic con el botón derecho y seleccione **Cambiar nombre** (o presione **F2**). Escriba **BankAccountTests** y presione **Entrar**.

::: moniker-end

El archivo *BankAccountTests.cs* contiene ahora el siguiente código:

```csharp
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

### <a name="add-a-using-statement"></a>Agregar una instrucción using

Agregue una [instrucción `using`](/dotnet/csharp/language-reference/keywords/using-statement) a la clase de prueba para poder llamar al proyecto que se está probando sin usar nombres completos. En la parte superior del archivo de clase, agregue:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Requisitos de la clase de prueba

Los requisitos mínimos para una clase de prueba son los siguientes:

- Se requiere el atributo `[TestClass]` en cualquier clase que contenga métodos de prueba unitaria que quiera ejecutar en el Explorador de pruebas.

- Cada método de prueba que quiera que el Explorador de pruebas reconozca debe tener el atributo `[TestMethod]`.

Puede tener otras clases de un proyecto de prueba unitaria que no tengan el atributo `[TestClass]` y puede tener otros métodos de clases de prueba que no tengan el atributo `[TestMethod]` . Puede llamar a estos otros métodos y clases desde los métodos de prueba.

## <a name="create-the-first-test-method"></a>Crear el primer método de prueba

En este procedimiento, escribirá métodos de prueba unitaria para comprobar el comportamiento del método `Debit` de la clase `BankAccount`.

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

El método es sencillo: configura un nuevo objeto `BankAccount` con un saldo inicial y luego retira una cantidad válida. Usa el método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType> para comprobar que el saldo de cierre es el esperado.

### <a name="test-method-requirements"></a>Requisitos del método de prueba

Un método de prueba debe cumplir los siguientes requisitos:

- Es representativo del atributo `[TestMethod]`.

- Devuelve `void`.

- No puede tener parámetros.

## <a name="build-and-run-the-test"></a>Compilar y ejecutar la prueba

1. En el menú **Compilación**, elija **Compilar solución** (o presione **CTRL** + **Mayús** + **B**).

2. Si el **Explorador de pruebas** no está abierto, seleccione **Prueba** > **Windows** > **Explorador de pruebas** en la barra de menús superior para abrirlo (o presione **CTRL** + **E**, **T**).

3. Elija **Ejecutar todas** para ejecutar la prueba (o presione **CTRL** + **R**, **V**).

   Mientras se ejecuta la prueba, la barra de estado de la parte superior de la ventana **Explorador de pruebas** está animada. Al final de la serie de pruebas, la barra se vuelve verde si todos los métodos de prueba se completan correctamente o roja si no alguna de las prueba no lo hace.

   En este caso, la prueba no se completa correctamente.

4. Seleccione el método en el **Explorador de pruebas** para ver los detalles en la parte inferior de la ventana.

## <a name="fix-your-code-and-rerun-your-tests"></a>Corrija el código y vuelva a ejecutar las pruebas

El resultado de la prueba contiene un mensaje que describe el error. En el caso del método `AreEqual`, el mensaje muestra lo que se esperaba y lo que se ha recibido realmente. Esperaba que se redujera el saldo pero, en su lugar, aumentó en la cantidad retirada.

La prueba unitaria puso al descubierto un error: la cantidad retirada se *agrega* al saldo de cuenta en lugar de ser *restada*.

### <a name="correct-the-bug"></a>Corregir el error

Para corregir el error, en el archivo *BankAccount.cs*, reemplace la línea:

```csharp
m_balance += amount;
```

Por:

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Vuelva a ejecutar la prueba

En el **Explorador de pruebas**, elija **Ejecutar todas** para volver a ejecutar la prueba (o presione **CTRL** + **R**, **V**). La barra de color rojo o verde se vuelve verde para indicar que se ha superado la prueba.

![Explorador de pruebas de Visual Studio 2019 que muestra una prueba superada](media/test-explorer-banktests-passed.png)

## <a name="use-unit-tests-to-improve-your-code"></a>Utilice pruebas unitarias para mejorar el código

En esta sección se describe cómo un proceso iterativo de análisis, el desarrollo de pruebas unitarias y la refactorización pueden servirle de ayuda para que el código de producción sea más compacto y eficaz.

### <a name="analyze-the-issues"></a>Analizar los problemas

Ha creado un método de prueba para confirmar que se resta correctamente una cantidad válida en el método `Debit`. Ahora, compruebe que el método produce <xref:System.ArgumentOutOfRangeException> si la cantidad de débito es:

- mayor que el saldo, o
- menor que cero.

### <a name="create-and-run-new-test-methods"></a>Creación y ejecución de nuevos métodos de prueba

Cree un método de prueba para comprobar que el comportamiento es el correcto cuando la cantidad de débito es menor que cero:

```csharp
[TestMethod]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act and assert
    Assert.ThrowsException<System.ArgumentOutOfRangeException>(() => account.Debit(debitAmount));
}
```

Use el método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> para declarar que se ha producido la excepción correcta. Este método provoca un error en la prueba, a menos que se produzca <xref:System.ArgumentOutOfRangeException>. Si modifica temporalmente el método en pruebas para que produzca una excepción <xref:System.ApplicationException> más genérica cuando la cantidad de débito es menor que cero, la prueba se comporta correctamente&mdash;es decir, se produce un error.

Para probar el caso en el que la cantidad retirada es mayor que el saldo, siga los siguientes pasos:

1. Crear un nuevo método de prueba denominado `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.

2. Copiar el cuerpo del método de `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` en el nuevo método.

3. Establecer `debitAmount` en un número mayor que el del saldo.

Ejecutar las dos pruebas y comprobar que se superan.

### <a name="continue-the-analysis"></a>Continuar el análisis

Puede mejorar aún más el método que se está probando. Con la implementación actual, no hay ninguna manera de saber qué condición (`amount > m_balance` o `amount < 0`) ha provocado la excepción producida durante la prueba. Sabemos solo que se ha producido un `ArgumentOutOfRangeException` en algún lugar del método. Sería mejor si pudiéramos decir qué condición en `BankAccount.Debit` produjo la excepción (`amount > m_balance` o `amount < 0`) para que pudiéramos estar seguros de que el método está comprobando correctamente el estado de sus argumentos.

Examine de nuevo el método en pruebas (`ArgumentOutOfRangeException`) y compruebe que ambas instrucciones condicionales utilizan un constructor `BankAccount.Debit` que tan solo toma el nombre del argumento como parámetro:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

Puede usar un constructor que proporcione información mucho más completa: <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> incluye el nombre y el valor del argumento, y un mensaje definido por el usuario. Puede refactorizar el método en pruebas para utilizar este constructor. Incluso mejor, puede utilizar miembros de tipo que se encuentran disponibles públicamente para especificar los errores.

### <a name="refactor-the-code-under-test"></a>Refactorizar el código en pruebas

Primero, defina dos constantes para los mensajes de error en el ámbito de la clase. Colóquelas en la clase sometida a prueba, `BankAccount`:

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

A continuación, modifique las dos instrucciones condicionales en el método `Debit`:

```csharp
if (amount > m_balance)
{
    throw new System.ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
}

if (amount < 0)
{
    throw new System.ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
}
```

### <a name="refactor-the-test-methods"></a>Refactorizar los métodos de prueba

Refactorice los métodos de prueba mediante la eliminación de la llamada a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>. Encapsule la llamada a `Debit()` en un bloque `try/catch`, detecte la excepción concreta que se espera y compruebe su mensaje asociado. El método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> ofrece la posibilidad de comparar dos cadenas.

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
    catch (System.ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>Vuelva a probar, reescriba y vuelva a analizar

Actualmente, el método de prueba no controla todos los casos que debería. Si el método sometido a prueba (`Debit`) no ha podido iniciar una excepción <xref:System.ArgumentOutOfRangeException> cuando `debitAmount` era mayor que el saldo (o menor que cero), el método de prueba pasaría. Esto no es bueno, porque quiere que el método de prueba no se supere si no se produce ninguna excepción.

Se trata de un error en el método de prueba. Para resolver el problema, agregue una validación <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> al final del método de prueba para controlar el caso donde no se produce ninguna excepción.

Al volver a ejecutar la prueba, se muestra que se *produce un error* en ella si se detecta la excepción correcta. El bloque `catch` detecta la excepción, pero el método sigue ejecutándose y se produce un error en el nueva comprobación de <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A>. Para resolver este problema, agregue una instrucción `return` después de `StringAssert` en el bloque `catch`. Al volver a ejecutar la prueba, se confirma que ha resuelto este problema. La versión final de `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` tiene el siguiente aspecto:

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
    catch (System.ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

### <a name="conclusion"></a>Conclusión

Las mejoras en el código de prueba condujeron a métodos de prueba más eficaces e informativos. Pero lo que es más importante, también mejoraron el código sometido a prueba.

> [!TIP]
> En este tutorial se utiliza el marco de pruebas unitarias de Microsoft para código administrado. El **Explorador de pruebas** también puede ejecutar pruebas desde marcos de pruebas unitarias de terceros que tengan adaptadores para el **Explorador de pruebas**. Para más información, vea [Instalar marcos de prueba unitaria de terceros](../test/install-third-party-unit-test-frameworks.md).

## <a name="see-also"></a>Vea también

Para obtener información sobre cómo ejecutar pruebas desde una línea de comandos, vea [Opciones de la línea de comandos para VSTest.Console.exe](vstest-console-options.md).
