---
title: Administrar excepciones con el depurador | Microsoft Docs
ms.custom: seodec18
ms.date: 10/09/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00ad5b41dd0a11661d281f24474b7673ea0a342c
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911505"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Administrar excepciones con el depurador en Visual Studio

Una excepción es una indicación de estado de error que se produce mientras se ejecuta un programa. Puede indicar al depurador las excepciones o conjuntos de excepciones en las que se va a interrumpir y en qué punto desea que el depurador interrumpa (es decir, PAUSE en el depurador). Cuando el depurador se interrumpe, muestra dónde se produjo la excepción. También puede Agregar o eliminar excepciones. Con una solución abierta en Visual Studio, use **Debug > configuración de excepciones de Windows >** para abrir la ventana de **configuración de excepciones** .

Proporcionar controladores que respondan a las excepciones más importantes. Si necesita saber cómo agregar controladores para las excepciones, vea [corregir errores escribiendo mejor C# código](../debugger/write-better-code-with-visual-studio.md). Además, obtenga información sobre cómo configurar el depurador para interrumpir siempre la ejecución de algunas excepciones.

Cuando se produce una excepción, el depurador escribe un mensaje en la ventana **Salida**. Puede interrumpir la ejecución en los casos siguientes cuando:

- Se produce una excepción que no se controla.
- El depurador está configurado para interrumpir la ejecución antes de que se invoque ningún controlador.
- Ha establecido [solo mi código](../debugger/just-my-code.md)y el depurador está configurado para interrumpir en cualquier excepción que no se controle en el código de usuario.

> [!NOTE]
> ASP.NET tiene un controlador de excepciones de nivel superior que muestra las páginas de error en un explorador. No interrumpe la ejecución a menos que se active **solo mi código** . Para obtener un ejemplo, vea [indicar al depurador que continúe en las excepciones no controladas por el usuario](#BKMK_UserUnhandled) a continuación.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> En una aplicación de Visual Basic, el depurador administra todos los errores como excepciones, incluso si se usan controladores de error de tipo On Error.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Indicar al depurador que se interrumpa cuando se produzca una excepción

El depurador puede interrumpir la ejecución en el punto en el que se produce una excepción, por lo que puede examinar la excepción antes de que se invoque un controlador.

En la ventana **configuración de excepciones** (**depurar > configuración de excepciones de Windows >** ), expanda el nodo de una categoría de excepciones, como **excepciones de Common Language Runtime**. A continuación, active la casilla para una excepción concreta dentro de esa categoría, como **System. AccessViolationException**. También puede seleccionar una categoría de excepciones completa.

![AccessViolationException activado](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Puede buscar excepciones específicas mediante la ventana **Buscar** de la barra de herramientas de **configuración de excepciones** , o usar la búsqueda para filtrar espacios de nombres específicos (como **System.IO**).

Si selecciona una excepción en la ventana de **configuración de excepciones** , la ejecución del depurador se interrumpirá siempre que se produzca la excepción, independientemente de si está controlada. Ahora, la excepción se denomina primera excepción. A continuación se muestran un par de escenarios de ejemplo:

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

  Si ha protegido **AccessViolationException** en la **configuración de excepciones**, la ejecución se interrumpirá en la línea de `throw` cuando ejecute este código en el depurador. A continuación puede continuar la ejecución. La consola debería mostrar ambas líneas:

  ```cmd
  caught exception
  goodbye
  ```

  pero no muestra la línea `here`.

- Una C# aplicación de consola hace referencia a una biblioteca de clases con una clase que tiene dos métodos. Un método produce una excepción y la controla, mientras que un segundo método produce la misma excepción pero no la controla.

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

  Si ha protegido **AccessViolationException** en la **configuración de excepciones**, la ejecución se interrumpirá en la línea de `throw` en **dos excepciones throwhandledexception ()** y **ThrowUnhandledException ()** cuando ejecute este código en el depurador.

Para restaurar la configuración de excepciones a los valores predeterminados, elija el botón **restaurar la lista a la configuración predeterminada** :

![Restaurar valores predeterminados en la configuración de excepciones](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="BKMK_UserUnhandled"></a>Indicar al depurador que continúe en las excepciones no controladas por el usuario

Si está depurando código .NET o JavaScript con [solo mi código](../debugger/just-my-code.md), puede indicar al depurador que evite la interrupción en excepciones que no se controlan en el código de usuario, pero que se administran en otro lugar.

1. En la ventana **configuración de excepciones** , abra el menú contextual haciendo clic con el botón secundario en una etiqueta de columna y, a continuación, seleccione **Mostrar columnas > acciones adicionales**. (Si ha desactivado **solo mi código**, no verá este comando). Aparece una tercera columna denominada **acciones adicionales** .

   ![Columna acciones adicionales](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   En el caso de una excepción que muestre **continuar cuando** no se controle en el código de usuario de esta columna, el depurador continúa si esa excepción no se controla en el código de usuario, pero se administra externamente.

2. Para cambiar esta configuración para una excepción determinada, seleccione la excepción, haga clic con el botón derecho para mostrar el menú contextual y seleccione **continuar cuando no se controle en el código de usuario**. También puede cambiar la configuración de una categoría de excepciones completa, como todas las excepciones de Common Language Runtime.

   ![* * Continuar cuando no se controle en el código de usuario * *](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Por ejemplo, las aplicaciones Web de ASP.NET controlan las excepciones convirtiéndose en un código de Estado HTTP 500 ([control de excepciones en ASP.net web API](/aspnet/web-api/overview/error-handling/exception-handling)), lo que puede no ayudarle a determinar el origen de la excepción. En el ejemplo siguiente, el código del usuario realiza una llamada a `String.Format()` que produce una excepción <xref:System.FormatException>. La ejecución se interrumpe del modo siguiente:

![Excepción no controlada&#45;por el usuario se interrumpe](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Agregar y eliminar excepciones

Las excepciones se pueden agregar y eliminar. Para eliminar un tipo de excepción de una categoría, seleccione la excepción y elija el botón **eliminar la excepción seleccionada en la lista** (el signo menos) de la barra de herramientas de **configuración de excepciones** . También puede hacer clic con el botón derecho en la excepción y seleccionar **eliminar** en el menú contextual. La eliminación de una excepción tiene el mismo efecto que tener la excepción desactivada, lo que indica que el depurador no se interrumpirá cuando se produzca.

Para agregar una excepción:

1. En la ventana **configuración de excepciones** , seleccione una de las categorías de excepciones (por ejemplo, **Common Language Runtime**).

2. Elija el botón **Agregar una excepción al categoría seleccionada** (el signo más).

   ![* * Agregar una excepción al botón de categoría * * seleccionado](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Escriba el nombre de la excepción (por ejemplo, **System. UriTemplateMatchException**).

   ![Escriba el nombre de la excepción](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   La excepción se agrega a la lista (en orden alfabético) y se activa automáticamente.

Para agregar una excepción a las categorías excepciones de acceso a la memoria de GPU, excepciones en tiempo de ejecución de JavaScript o excepciones de Win32, incluya el código de error y la descripción.

> [!TIP]
> No olvide revisar la ortografía. La ventana **Configuración de excepciones** no comprueba la existencia de una excepción agregada. Por lo tanto, si escribe **Sytem.UriTemplateMatchException**, se creará una entrada para esa excepción (y no para **System.UriTemplateMatchException**).

La configuración de excepciones se conserva en el archivo .suo de la solución, por lo que se aplican a una solución concreta. Esta configuración de excepciones específica no se puede reutilizar en otras soluciones. Ahora solo se conservan las excepciones agregadas. las excepciones eliminadas no lo son. Puede Agregar una excepción, cerrar la solución y volver a abrirla, y la excepción seguirá estando ahí. Pero si elimina una excepción y cierra y vuelve a abrir la solución, volverá a aparecer la excepción.

La ventana **Configuración de excepciones** admite tipos genéricos de excepciones en C#, pero no en Visual Basic. Para interrumpir la ejecución en excepciones como `MyNamespace.GenericException<T>`, agregue la excepción como **MyNamespace.GenericException`1**. Es decir, si ha creado una excepción como este código:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Puede Agregar la excepción a la **configuración de excepciones** mediante el procedimiento anterior:

![Agregar excepción genérica](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Agregar condiciones a una excepción

Use la ventana **configuración de excepciones** para establecer condiciones en las excepciones. Las condiciones admitidas actualmente incluyen los nombres de módulo que se van a incluir o excluir para la excepción. Al establecer los nombres de módulo como condiciones, puede elegir interrumpir la excepción solo en determinados módulos de código. También puede optar por evitar la interrupción en módulos concretos.

> [!NOTE]
> Se admite la adición de condiciones a una excepción a partir de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Para agregar excepciones condicionales:

1. Elija el botón **Editar condiciones** en la ventana Configuración de excepciones, o haga clic con el botón derecho en la excepción y elija **Editar condiciones**.

   ![Condiciones para una excepción](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Para agregar condiciones adicionales necesarias a la excepción, seleccione **Agregar condición** para cada nueva condición. Aparecen líneas de condiciones adicionales.

   ![Condiciones adicionales para una excepción](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. En cada línea de condición, escriba el nombre del módulo y cambie la lista de operadores de comparación por **es igual** a o **no es igual**a. Puede especificar caracteres comodín ( **\\\*** ) en el nombre para especificar más de un módulo.

4. Si necesita eliminar una condición, elija la **X** al final de la línea de condición.

## <a name="see-also"></a>Vea también

- [Continuación de la ejecución después de una excepción](../debugger/continuing-execution-after-an-exception.md)<br/>
- [Análisis del código del sistema después de una excepción](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [Uso de comprobaciones nativas en tiempo de ejecución](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [Usar comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
