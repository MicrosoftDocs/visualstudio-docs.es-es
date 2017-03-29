---
title: "Tutorial: Crear y ejecutar pruebas unitarias en código administrado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.assetid: 2b018b18-b412-4e0e-b0ee-b580a2f3ba9c
caps.latest.revision: 83
ms.author: mlearned
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: a00b80092a44190d626b93b0ecc5689bafd1a4e3
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-and-running-unit-tests-for-managed-code"></a>Tutorial: Crear y ejecutar pruebas unitarias en código administrado
Este tutorial recorre paso a paso la creación, ejecución y personalización de una serie de pruebas unitarias mediante el marco de pruebas unitarias para código administrado de Microsoft y el Explorador de pruebas de Visual Studio. Se empieza con un proyecto C# que está en desarrollo, se crean pruebas que utilizan el código, se ejecutan las pruebas y se examinan los resultados. Por último, puede cambiar el código del proyecto y volver a ejecutar las pruebas.  
  
 Este tema contiene las siguientes secciones:  
  
 [Preparar el tutorial](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough)  
  
 [Crear un proyecto de prueba unitaria](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_a_unit_test_project)  
  
 [Crear la clase de prueba](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_test_class)  
  
-   [Requisitos de la clase de prueba](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_class_requirements)  
  
 [Crear el primer método de prueba](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_first_test_method)  
  
-   [Requisitos del método de prueba](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_method_requirements)  
  
 [Compilar y ejecutar la prueba](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Build_and_run_the_test)  
  
 [Corrija el código y vuelva a ejecutar las pruebas](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Fix_your_code_and_rerun_your_tests)  
  
 [Utilizar pruebas unitarias para mejorar el código](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Use_unit_tests_to_improve_your_code)  
  
> [!NOTE]
>  En este tutorial se utiliza el marco de pruebas unitarias de Microsoft para código administrado. El Explorador de pruebas también puede ejecutar pruebas de marcos de pruebas unitarias de terceros, que tienen adaptadores para el Explorador de pruebas. Para obtener más información, consulte [Instalar marcos de prueba unitaria de terceros](../test/install-third-party-unit-test-frameworks.md)  
  
> [!NOTE]
>  Para obtener información sobre cómo ejecutar pruebas desde una línea de comandos, vea [Tutorial: Utilizar la utilidad de prueba de la línea de comandos](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867).  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   El proyecto del banco. Consulte [Proyecto de ejemplo para crear pruebas unitarias](../test/sample-project-for-creating-unit-tests.md).  
  
##  <a name="BKMK_Prepare_the_walkthrough"></a> Preparar el tutorial  
  
1.  Abra Visual Studio.  
  
2.  En el menú **Archivo** , elija **Nuevo** y haga clic en **Proyecto**.  
  
     Aparecerá el cuadro de diálogo **Nuevo proyecto** .  
  
3.  En **Plantillas instaladas**, haga clic en **Visual C#**.  
  
4.  En la lista de tipos de aplicación, haga clic en **Biblioteca de clases**.  
  
5.  En el cuadro **Nombre** , escriba `Bank` y haga clic en **Aceptar**.  
  
    > [!NOTE]
    >  Si el nombre "Bank" ya está en uso, elija otro nombre para el proyecto.  
  
     Se crea el nuevo proyecto Bank y se muestra en el Explorador de soluciones con el archivo Class1.cs abierto en el editor de código.  
  
    > [!NOTE]
    >  Si el archivo Class1.cs no se abre en el editor de código, en el Explorador de soluciones, haga doble clic en el archivo para abrirlo.  
  
6.  Copie el código fuente desde el [proyecto de ejemplo para crear pruebas de unidad](../test/sample-project-for-creating-unit-tests.md).  
  
7.  Reemplace el contenido original de Class1.cs por el código que encontrará en el [proyecto de ejemplo para crear pruebas de unidad](../test/sample-project-for-creating-unit-tests.md).  
  
8.  Guarde el archivo como BankAccount.cs  
  
9. En el menú **Compilar** , haga clic en **Compilar solución**.  
  
 Ahora tiene un proyecto denominado Bank que contiene código fuente para realizar pruebas y las herramientas necesarias para ello. El espacio de nombres de Bank, **BankAccountNS**, contiene la clase pública **BankAccount**cuyos métodos probará en los procedimientos siguientes.  
  
 Este tutorial se centra en el método `Debit` . Se llama al método Debit cuando se retira dinero de una cuenta y contiene el siguiente código:  
  
```c#  
// method under test  
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
  
##  <a name="BKMK_Create_a_unit_test_project"></a> Crear un proyecto de prueba unitaria  
 **Requisito previo**: siga los pasos del procedimiento [Preparar el tutorial](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough).  
  
#### <a name="to-create-a-unit-test-project"></a>Para crear un proyecto de prueba unitaria  
  
1.  En el menú **Archivo** , elija **Agregar**y, a continuación, elija **Nuevo proyecto...**.  
  
2.  En el cuadro de diálogo Nuevo proyecto, expanda **Instalado**, expanda **Visual C#**y, a continuación, elija **Prueba**.  
  
3.  En la lista de plantillas, seleccione **Proyecto de prueba unitaria**.  
  
4.  En el cuadro **Nombre** , escriba BankTest y elija **Aceptar**.  
  
     El proyecto **BankTests** se agrega a la solución **Bank** .  
  
5.  En el proyecto **BankTests** , agregue una referencia a la solución **Bank** .  
  
     En el Explorador de soluciones, seleccione **Referencias** en el proyecto **BankTests** y, después, elija **Agregar referencia...** desde el menú contextual.  
  
6.  En el cuadro de diálogo del Administrador de referencia, expanda **Solución** y active el elemento **Bank** .  
  
##  <a name="BKMK_Create_the_test_class"></a> Crear la clase de prueba  
 Se necesita una clase de prueba para comprobar la clase `BankAccount` . Se puede utilizar UnitTest1.cs, generado por la plantilla de proyecto, pero se debe asignar al archivo y a la clase nombres más descriptivos. Podemos hacer esto en un solo paso cambiando el nombre del archivo en el Explorador de soluciones.  
  
 **Cambiar el nombre de un archivo de clase**  
  
 En el Explorador de soluciones, seleccione el archivo UnitTest1.cs en el proyecto BankTests. Desde el menú contextual, elija **Cambiar nombre**y, a continuación, cambie el nombre del archivo a BankAccountTests.cs. Elija **Sí** en el cuadro de diálogo que pregunta si desea cambiar el nombre de todas las referencias del proyecto al elemento de código “UnitTest1”. En este paso se cambia el nombre de la clase a `BankAccountTest`.  
  
 El archivo BankAccountTests.cs contiene ahora el siguiente código:  
  
```c#  
// unit test code  
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
  
 **Agregar una instrucción using al proyecto en pruebas**  
  
 También podemos agregar una instrucción using a la clase para poder llamar al proyecto en pruebas, sin utilizar nombres completos. En la parte superior del archivo de clase, agregue:  
  
```c#  
using BankAccountNS;  
```  
  
###  <a name="BKMK_Test_class_requirements"></a> Requisitos de la clase de prueba  
 Los requisitos mínimos para una clase de prueba son los siguientes:  
  
-   El atributo `[TestClass]` se requiere en el marco de pruebas unitarias para código administrado de Microsoft para cualquier clase que contenga métodos de prueba unitaria que desee ejecutar en el Explorador de pruebas.  
  
-   Cada método de prueba que desee que ejecute el Explorador de pruebas debe tener el atributo `[TestMethod]`.  
  
 Puede tener otras clases de un proyecto de prueba unitaria que no tengan el atributo `[TestClass]` y puede tener otros métodos de clases de prueba que no tengan el atributo `[TestMethod]` . Puede utilizar estos otros métodos y clases en sus métodos de prueba.  
  
##  <a name="BKMK_Create_the_first_test_method"></a> Crear el primer método de prueba  
 En este procedimiento, se escribirán métodos de prueba unitaria para comprobar el comportamiento del método `Debit` de la clase `BankAccount` . El método se muestra más arriba.  
  
 Al analizar el método en pruebas, se determina que hay al menos tres comportamientos que deben comprobarse:  
  
1.  El método produce [ArgumentOutOfRangeException](assetId:///ArgumentOutOfRangeException?qualifyHint=False&autoUpgrade=True) si la cantidad de débito es mayor que el saldo.  
  
2.  También produce `ArgumentOutOfRangeException` si la cantidad de débito es menor que cero.  
  
3.  Si se cumplen las comprobaciones 1.) y 2.), el método resta la cantidad del saldo de cuenta.  
  
 En la primera prueba, se comprueba que una cantidad válida (una menor que el saldo de cuenta y mayor que cero) retire la cantidad correcta de la cuenta.  
  
#### <a name="to-create-a-test-method"></a>Para crear un método de prueba  
  
1.  Agregue una instrucción using `BankAccountNS;` al archivo BankAccountTests.cs.  
  
2.  Agregue el siguiente método a esa clase `BankAccountTests` :  
  
    ```c#  
    // unit test code  
    [TestMethod]  
    public void Debit_WithValidAmount_UpdatesBalance()  
    {  
        // arrange  
        double beginningBalance = 11.99;  
        double debitAmount = 4.55;  
        double expected = 7.44;  
        BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
        // act  
        account.Debit(debitAmount);  
  
        // assert  
        double actual = account.Balance;  
        Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");  
    }  
    ```  
  
 El método es bastante sencillo. Se configura un nuevo objeto `BankAccount` con un saldo inicial y después se retira una cantidad válida. Se utiliza el marco de pruebas unitarias de Microsoft para el método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> de código administrado, para comprobar que el saldo de cierre es el esperado.  
  
###  <a name="BKMK_Test_method_requirements"></a> Requisitos del método de prueba  
 Un método de prueba debe cumplir los siguientes requisitos:  
  
-   El método se debe señalar con el atributo `[TestMethod]` .  
  
-   El método debe devolver `void`.  
  
-   El método no puede tener parámetros.  
  
##  <a name="BKMK_Build_and_run_the_test"></a> Compilar y ejecutar la prueba  
  
#### <a name="to-build-and-run-the-test"></a>Para compilar y ejecutar la prueba  
  
1.  En el menú **Compilar** , elija **Compilar solución**.  
  
     Si no hay ningún error, aparece la ventana UnitTestExplorer con **Debit_WithValidAmount_UpdatesBalance** incluido en el grupo **Pruebas no ejecutadas** . Si no el Explorador de pruebas aparece tras realizar una compilación correcta, elija **Prueba** en el menú, **Ventanas**y, a continuación,  **Explorador de pruebas**.  
  
2.  Elija **Ejecutar todas** para ejecutar la prueba. Mientras se ejecuta la prueba, la barra de estado en la parte superior de la ventana se anima. Al final de la serie de pruebas, la barra se vuelve verde si todos los métodos de prueba se completan correctamente o roja si no alguna de las prueba no lo hace.  
  
3.  En este caso, la prueba no se completa correctamente. El método de prueba se mueve al grupo **Pruebas no superadas** . Seleccione el método en el Explorador de pruebas para ver los detalles en la parte inferior de la ventana.  
  
##  <a name="BKMK_Fix_your_code_and_rerun_your_tests"></a> Corregir el código y volver a ejecutar las pruebas  
 **Analizar los resultados de pruebas**  
  
 El resultado de la prueba contiene un mensaje que describe el error. Para el método `AreEquals`, el mensaje muestra lo que se esperaba (el parámetro **Expected\<*XXX*>**) y lo que se recibió realmente (el parámetro**Actual\<*YYY*>**). Se esperaba una disminución en el saldo en comparación con el inicial pero, en cambio, ha aumentado en la cantidad retirada.  
  
 Un nuevo examen del código Debit muestra que la prueba unitaria ha logrado encontrar un error. La cantidad retirada se agrega al saldo de cuenta en lugar de ser restarse.  
  
 **Corregir el error**  
  
 Para corregir el error, reemplace simplemente la línea  
  
```c#  
m_balance += amount;  
```  
  
 with  
  
```c#  
m_balance -= amount;  
```  
  
 **Volver a ejecutar la prueba**  
  
 En el Explorador de pruebas, elija **Ejecutar todas** para volver a ejecutar la prueba. La barra de color rojo o verde se vuelve verde y la prueba se mueve al grupo de **Pruebas superadas** .  
  
##  <a name="BKMK_Use_unit_tests_to_improve_your_code"></a> Utilizar pruebas unitarias para mejorar el código  
 En esta sección se describe cómo un proceso iterativo de análisis, el desarrollo de pruebas unitarias y la refactorización pueden servirle de ayuda para que el código de producción sea más compacto y eficaz.  
  
 **Analizar los problemas**  
  
 Después de crear un método de prueba para confirmar que se reste correctamente una cantidad válida en el método `Debit` , podemos volver a los casos restantes del análisis original:  
  
1.  El método produce `ArgumentOutOfRangeException` si la cantidad de débito es mayor que el saldo.  
  
2.  También produce `ArgumentOutOfRangeException` si la cantidad de débito es menor que cero.  
  
 **Crear los métodos de prueba**  
  
 El primer intento de crear un método de prueba para resolver estos problemas es prometedor:  
  
```c#  
//unit test method  
[TestMethod]  
[ExpectedException(typeof(ArgumentOutOfRangeException))]  
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = -100.00;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    account.Debit(debitAmount);  
  
    // assert is handled by ExpectedException  
}  
  
```  
  
 Se usa el atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> para confirmar que se ha producido la excepción correcta. El atributo hace que la prueba dé un error a menos que se produzca `ArgumentOutOfRangeException` . Ejecutar las pruebas con valores positivos y negativos de `debitAmount` y después modificar temporalmente el método probado para producir una <xref:System.ApplicationException> genérica cuando la cantidad es menor que cero muestra que la prueba se comporta correctamente. Para probar el caso en el que la cantidad retirada es mayor que el saldo, lo que debemos hacer es:  
  
1.  Crear un nuevo método de prueba denominado `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.  
  
2.  Copiar el cuerpo del método de `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` en el nuevo método.  
  
3.  Establecer `debitAmount` en un número mayor que el del saldo.  
  
 **Ejecutar las pruebas**  
  
 Ejecutar los dos métodos con valores diferentes para `debitAmount` muestra que las pruebas controlan los casos restantes de manera adecuada. Ejecutar las tres pruebas confirma que todos casos del análisis original están cubiertos correctamente.  
  
 **Continuar el análisis**  
  
 Sin embargo, los dos últimos métodos de prueba también son algo problemáticos. No podemos estar seguros de qué condición del código en pruebas se inicia cuando se realiza cada serie de pruebas. Sería útil tener alguna manera de diferenciar las dos condiciones. Cuanto más se piensa en el problema, más evidente resulta que sabiendo qué condición se ha infringido aumentaría la confianza en las pruebas. Esta información también sería útil, muy probablemente, al mecanismo de producción que controla la excepción cuando la inicia el método en pruebas. Generar más información cuando el método inicie una excepción ayudaría a todos los componentes relacionados, pero el atributo `ExpectedException` no puede proporcionar esta información.  
  
 Al examinar de nuevo el método en pruebas, se puede ver que ambas instrucciones condicionales utilizan un constructor `ArgumentOutOfRangeException` , que toma su nombre del argumento como parámetro:  
  
```c#  
throw new ArgumentOutOfRangeException("amount");  
```  
  
 En una búsqueda por MSDN Library detectamos que existe un constructor que proporciona información mucho más completa. <xref:System.ArgumentOutOfRangeException.%23ctor%2A>`(String, Object, String)` incluye el nombre del argumento, su valor y un mensaje definido por el usuario. Se puede refactorizar el método en pruebas para utilizar este constructor. Incluso mejor, podemos utilizar miembros de tipo que se encuentran disponibles públicamente para especificar los errores.  
  
 **Refactorizar el código en pruebas**  
  
 Primero se definen dos constantes para los mensajes de error en el ámbito de la clase:  
  
```c#  
// class under test  
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";  
public const string DebitAmountLessThanZeroMessage = "Debit amount less than zero";  
```  
  
 A continuación, se modifican las dos instrucciones condicionales en el método `Debit` :  
  
```c#  
// method under test  
// ...  
    if (amount > m_balance)  
    {  
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);  
    }  
  
    if (amount < 0)  
    {  
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);  
    }  
// ...  
```  
  
 **Refactorizar los métodos de prueba**  
  
 En el método de prueba, primero quitamos el atributo `ExpectedException` . En su lugar, se captura la excepción y se comprueba que se haya iniciado en la instrucción condicional correcta. Sin embargo, ahora debemos decidir entre dos opciones para comprobar las condiciones restantes. Por ejemplo, en el método `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` , podemos realizar una de las siguientes acciones:  
  
-   Asegurar que la propiedad `ActualValue` de la excepción (el segundo parámetro del constructor de `ArgumentOutOfRangeException` ) es mayor que el saldo inicial. Esta opción requiere probar la propiedad `ActualValue` de la excepción con la variable `beginningBalance` del método de prueba y, también, requiere que se compruebe que `ActualValue` es mayor que cero.  
  
-   Asegurar que el mensaje (el tercer parámetro del constructor) incluye el `DebitAmountExceedsBalanceMessage` definido en la clase `BankAccount` .  
  
 El método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> en el marco de pruebas unitarias de Microsoft permite comprobar la segunda opción sin los cálculos necesarios de la primera.  
  
 Un segundo intento de revisar `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` podría ser similar a:  
  
```c#  
[TestMethod]  
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = 20.0;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    try  
    {  
        account.Debit(debitAmount);  
    }  
    catch (ArgumentOutOfRangeException e)  
    {  
        // assert  
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);  
    }  
}  
```  
  
 **Volver a probar, reescribir y volver a analizar**  
  
 Cuando se vuelven a probar los métodos de prueba con valores diferentes, descubrimos lo siguiente:  
  
1.  Si se captura el error correcto usando una aserción `debitAmount` mayor que el saldo, la comprobación `Contains` se supera, la excepción se omite y el método de prueba se completa correctamente. Este es el comportamiento que deseamos.  
  
2.  Si se usa `debitAmount` menor que 0, la comprobación no se puede realizar porque se devuelve un mensaje de error incorrecto. La comprobación tampoco se puede realizar si se introduce una excepción temporal `ArgumentOutOfRange` en otro punto del método bajo la ruta de acceso del código de prueba. Esto también es correcto.  
  
3.  Si el valor de `debitAmount` es válido (es decir, menor que el saldo pero mayor que cero), no se detecta ninguna excepción, por lo que la comprobación nunca se detecta. El método de prueba se completa correctamente. Esto no es bueno, porque se desea que el método de prueba no se supere si no se produce ninguna excepción.  
  
 El tercer hecho es un error en el método de prueba. Para intentar resolver el problema, se agrega una aserción <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> al final del método de prueba para controlar el caso donde no se produce ninguna excepción.  
  
 Pero, al volver a examinar, se muestra que se produce un error en la prueba si se detecta la excepción correcta. La instrucción catch restaura la excepción, el método continúa ejecutándose y produce errores en la nueva validación. Para resolver este nuevo problema, se agrega una instrucción `return` después de `StringAssert`. Al volver a examinar se confirma que hemos corregido los problemas. La versión final de `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` tiene el siguiente aspecto:  
  
```c#  
[TestMethod]  
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = 20.0;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    try  
    {  
        account.Debit(debitAmount);  
    }  
    catch (ArgumentOutOfRangeException e)  
    {  
        // assert  
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);  
        return;  
    }  
    Assert.Fail("No exception was thrown.");  
}  
  
```  
  
 En esta sección final, el trabajo que se hizo al mejorar el código de prueba condujo a métodos de prueba más eficaces e informativos. Pero, lo que es más importante, el análisis adicional también condujo a mejoras en el código del proyecto en pruebas.
