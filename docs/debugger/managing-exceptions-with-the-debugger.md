---
title: Administración de excepciones con el depurador | Microsoft Docs
ms.custom: seodec18
ms.date: 10/09/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02c7fbfca9a63ac736972ebea01a854e24f90188
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057923"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Administración de excepciones con el depurador de Visual Studio

Una excepción es una indicación de estado de error que se produce mientras se ejecuta un programa. Puede indicar al depurador qué excepciones o conjuntos de excepciones para interrumpir y en qué punto desea que el depurador se interrumpa. Cuando el depurador se interrumpe, se muestra donde se produjo la excepción. También puede agregar o eliminar las excepciones. Con una solución abierta en Visual Studio, utilice **Depurar > Windows > configuración de excepciones** para abrir el **configuración de excepciones** ventana.

Proporcione controladores que respondan a las excepciones más importantes. También aprenderá a configurar el depurador para interrumpir siempre la ejecución de algunas excepciones.

Cuando se produce una excepción, el depurador escribe un mensaje en la ventana **Salida**. Puede interrumpir la ejecución en los siguientes casos cuando:

- Se produce una excepción no controlada.
- El depurador está configurado para interrumpir la ejecución antes de que se invoque ningún controlador.
- Ha establecido [solo mi código](../debugger/just-my-code.md), y el depurador está configurado para que se interrumpa en cualquier excepción que no se controla en código de usuario.

> [!NOTE]
> ASP.NET tiene un controlador de excepciones de nivel superior que muestra las páginas de error en un explorador. No interrumpir la ejecución a menos que **solo mi código** está activado. Para obtener un ejemplo, vea [indicar al depurador para continuar en las excepciones no controladas de usuario](#BKMK_UserUnhandled) a continuación.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> En una aplicación de Visual Basic, el depurador administra todos los errores como excepciones, incluso si se usan controladores de error de tipo On Error.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Indicar al depurador para interrumpir cuando se produce una excepción

El depurador puede interrumpir la ejecución en el punto donde se produce una excepción, por lo que puede examinar la excepción antes de que se invoca un controlador.

En el **configuración de excepciones** ventana (**Depurar > Windows > configuración de excepciones**), expanda el nodo de una categoría de excepciones, como **excepciones Common Language Runtime**. A continuación, seleccione la casilla de verificación para una excepción concreta dentro de esa categoría, como **System.AccessViolationException**. También puede seleccionar una categoría de excepciones completa.

![Comprobar AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Puede encontrar excepciones específicas mediante la **búsqueda** ventana en la **configuración de excepciones** barra de herramientas, o usar la búsqueda para filtrar espacios de nombres específicos (como **System.IO**).

Si selecciona una excepción en el **configuración de excepciones** ventana, la ejecución del depurador se interrumpirá siempre que se produce la excepción, independientemente de si se trata. Ahora, la excepción se denomina primera excepción. A continuación se muestran un par de escenarios de ejemplo:

- En la siguiente aplicación de consola de C#, el método Main produce una excepción **AccessViolationException** dentro de un bloque `try/catch`.

  ```csharp
  static void Main(string[] args)
  {
      try
      {
          throw new AccessViolationException();
          Console.WriteLine("here");
      }
      catch (Exception e)
      {
          Console.WriteLine("caught exception");
      }
      Console.WriteLine("goodbye");
  }
  ```

  Si tiene **AccessViolationException** protegido **configuración de excepciones**, se interrumpirá la ejecución en el `throw` cuando ejecuta este código en el depurador de línea. A continuación puede continuar la ejecución. La consola debería mostrar ambas líneas:

  ```cmd
  caught exception
  goodbye
  ```

  pero no muestra la `here` línea.

- Un C# aplicación de consola hace referencia a una biblioteca de clases con una clase que tiene dos métodos. Un método produce una excepción y controla, mientras que un segundo método produce la misma excepción pero no la controla.

  ```csharp
  public class Class1
  {
      public void ThrowHandledException()
      {
          try
          {
              throw new AccessViolationException();
          }
          catch (AccessViolationException ave)
          {
              Console.WriteLine("caught exception" + ave.Message);
          }
      }

      public void ThrowUnhandledException()
      {
          throw new AccessViolationException();
      }
  }
  ```

  Este es el método Main() de la aplicación de consola:

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  Si tiene **AccessViolationException** protegido **configuración de excepciones**, se interrumpirá la ejecución en el `throw` línea tanto en **ThrowHandledException()** y **ThrowUnhandledException()** al ejecutar este código en el depurador.

Para restaurar la configuración de excepciones a los valores predeterminados, elija el **restaurar la lista a la configuración predeterminada** botón:

![Restaurar valores predeterminados en la configuración de excepciones](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="BKMK_UserUnhandled"></a>Indicar al depurador para continuar en las excepciones no controladas de usuario

Si está depurando código .NET o JavaScript con [solo mi código](../debugger/just-my-code.md), puede indicar al depurador para evitar interrupciones en las excepciones que no se controla en código de usuario, pero sí se controlan en otro lugar.

1. En el **configuración de excepciones** , abra el menú contextual haciendo una etiqueta de columna y, a continuación, seleccione **mostrar columnas > acciones adicionales**. (Si ha desactivado **solo mi código**, no verá este comando.) Una tercera columna denominada **acciones adicionales** aparece.

   ![Columna de acciones adicional](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   Para una excepción que se muestra **continuar cuando no está controlada en código de usuario** en esta columna, el depurador continúa si esa excepción no controlada en el código de usuario, pero se controla de forma externa.

2. Para cambiar esta configuración para una excepción concreta, seleccione la excepción, haga doble clic para mostrar el menú contextual y seleccione **continuar cuando no se controle en el código de usuario**. También puede cambiar la configuración para toda una categoría de excepciones, como las excepciones de Common Language Runtime todas).

   ![** Continuar cuando no está controlada en código ** configuración de usuario](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Por ejemplo, las aplicaciones web ASP.NET controlan excepciones mediante su conversión a un código de estado HTTP 500 ([control de excepciones en ASP.NET Web API](http://www.asp.net/web-api/overview/error-handling/exception-handling)), que es posible que no ayudarle a determinar el origen de la excepción. En el ejemplo siguiente, el código del usuario realiza una llamada a `String.Format()` que produce una excepción <xref:System.FormatException>. La ejecución se interrumpe del modo siguiente:

![Se interrumpe en usuario&#45;excepción no controlada](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Agregar y eliminar excepciones

Las excepciones se pueden agregar y eliminar. Para eliminar un tipo de excepción de una categoría, seleccione la excepción y elija el **eliminar la excepción seleccionada en la lista** botón (el signo menos) en el **configuración de excepciones** barra de herramientas. O bien haga clic en la excepción y seleccione **eliminar** en el menú contextual. Eliminar una excepción tiene el mismo efecto que la excepción no está activada, que es que el depurador no se interrumpa cuando se produzca la excepción.

Para agregar una excepción:

1. En el **configuración de excepciones** ventana, seleccione una de las categorías de excepciones (por ejemplo, **Common Language Runtime**).

2. Elija la **agregar una excepción a la categoría seleccionada** botón (el signo más).

   ![** Agregar una excepción al botón seleccionado categoría **](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Escriba el nombre de la excepción (por ejemplo, **System.UriTemplateMatchException**).

   ![Escriba el nombre de la excepción](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   La excepción se agrega a la lista (en orden alfabético) y se activa automáticamente.

Para agregar una excepción a las excepciones de acceso de memoria de GPU, las excepciones de tiempo de ejecución de JavaScript o categorías de excepciones de Win32, incluyen el código de error y la descripción.

> [!TIP]
> No olvide revisar la ortografía. La ventana **Configuración de excepciones** no comprueba la existencia de una excepción agregada. Por lo tanto, si escribe **Sytem.UriTemplateMatchException**, se creará una entrada para esa excepción (y no para **System.UriTemplateMatchException**).

La configuración de excepciones se conserva en el archivo .suo de la solución, por lo que se aplican a una solución concreta. Esta configuración de excepciones específica no se puede reutilizar en otras soluciones. Ahora se conservan solo excepciones agregadas; no las eliminadas. Puede agregar una excepción, cerrar y volver a abrir la solución, y la excepción seguirá estando ahí. Pero si elimina una excepción y cierra y vuelve a abrir la solución, volverá a aparecer la excepción.

La ventana **Configuración de excepciones** admite tipos genéricos de excepciones en C#, pero no en Visual Basic. Para interrumpir la ejecución en excepciones como `MyNamespace.GenericException<T>`, agregue la excepción como **MyNamespace.GenericException`1**. Es decir, si ha creado una excepción similar a este código:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Puede agregar la excepción a **configuración de excepciones** mediante el procedimiento anterior:

![Agregar excepción genérica](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Agregar condiciones a una excepción

Use la **configuración de excepciones** ventana para establecer condiciones en las excepciones. Las condiciones admitidas actualmente incluyen los nombres de módulo para incluir o excluir de la excepción. Al establecer los nombres de módulo como condiciones, puede interrumpir para la excepción solo en determinados módulos de código. También puede evitar interrupciones en módulos concretos.

> [!NOTE]
> Agregar condiciones a una excepción es nueva en [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Para agregar excepciones condicionales:

1. Elija la **editar condiciones** situado en la ventana de configuración de excepciones, o haga clic en la excepción y elija **editar condiciones**.

   ![Condiciones para una excepción](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Para agregar condiciones adicionales necesarias para la excepción, seleccione **Agregar condición** para cada una de ellas. Aparecen líneas de la condición adicional.

   ![Condiciones adicionales para una excepción](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Para cada línea de la condición, escriba el nombre del módulo y cambie la lista de operadores de comparación a **es igual a** o **no es igual a**. Puede especificar caracteres comodín (**\\***) en el nombre para especificar más de un módulo.

4. Si necesita eliminar una condición, elija el **X** al final de la línea de la condición.

## <a name="see-also"></a>Vea también

[Continuación de la ejecución después de una excepción](../debugger/continuing-execution-after-an-exception.md)<br/>
[Cómo: examinar el código del sistema después de una excepción](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
[Cómo: usar comprobaciones nativas en tiempo de ejecución](../debugger/how-to-use-native-run-time-checks.md)<br/>
[Usar comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
[Tutorial: información sobre cómo depurar con Visual Studio](../debugger/getting-started-with-the-debugger.md)
