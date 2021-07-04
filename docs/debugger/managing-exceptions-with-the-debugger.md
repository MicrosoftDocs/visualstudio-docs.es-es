---
title: Administración de excepciones con el depurador | Microsoft Docs
description: Obtenga información sobre cómo especificar en qué excepciones se interrumpe el depurador, en qué punto quiere que se interrumpa y cómo se controlan las interrupciones.
ms.custom: SEO-VS-2020
ms.date: 10/09/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 89795df3a4c6b87c6a878cd07a072027f880e660
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390429"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Administración de excepciones con el depurador en Visual Studio

Una excepción es una indicación de estado de error que se produce mientras se ejecuta un programa. Puede indicar al depurador las excepciones o los conjuntos de excepciones donde se va a interrumpir y en qué punto quiere que el depurador lo haga (es decir, que el depurador se pause). Cuando el depurador se interrumpe, muestra dónde se produjo la excepción. También puede agregar o eliminar excepciones. Con una solución abierta en Visual Studio, use **Depurar > Windows > Configuración de excepciones** para abrir la ventana **Configuración de excepciones**.

Proporcione controladores que respondan a las excepciones más importantes. Si necesita saber cómo agregar controladores para las excepciones, consulte [Herramientas y técnicas de depuración para ayudarle a escribir código mejor](../debugger/write-better-code-with-visual-studio.md). Además, obtenga información sobre cómo configurar el depurador para interrumpir siempre la ejecución de algunas excepciones.

Cuando se produce una excepción, el depurador escribe un mensaje en la ventana **Salida**. La ejecución se puede interrumpir en los casos siguientes:

- Se produce una excepción que no está controlada.
- El depurador está configurado para interrumpir la ejecución antes de invocar cualquier controlador.
- Se ha establecido [Solo mi código](../debugger/just-my-code.md) y el depurador está configurado para interrumpir la ejecución en cualquier excepción que no esté controlada en el código del usuario.

> [!NOTE]
> ASP.NET tiene un controlador de excepciones de nivel superior que muestra las páginas de error en un explorador. No interrumpe la ejecución a menos que **Solo mi código** esté activado. Para obtener un ejemplo, consulte [Indicar al depurador que continúe en las excepciones no controladas por el usuario](#BKMK_UserUnhandled) a continuación.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> En una aplicación de Visual Basic, el depurador administra todos los errores como excepciones, incluso si se usan controladores de error de tipo On Error.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Indicar al depurador que se interrumpa en las excepciones no controladas por el usuario

El depurador puede interrumpir la ejecución en el momento en el que se produce una excepción para que, así, pueda examinarla antes de que se invoque un controlador.

En la ventana **Configuración de excepciones** (**Depurar > Windows > Configuración de excepciones**), expanda el nodo para obtener una categoría de excepciones, como **Excepciones de Common Language Runtime**. Después, active la casilla para buscar una excepción determinada dentro de esa categoría, como **System.AccessViolationException**. También puede seleccionar una categoría de excepciones completa.

![AccessViolationException comprobado](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Si quiere buscar una determinada excepción, use la ventana **Buscar** de la barra de herramientas **Configuración de excepciones**. También puede usar la búsqueda para filtrar espacios de nombres específicos (como **System.IO**).

Si selecciona una excepción en la ventana **Configuración de excepciones**, la ejecución del depurador se interrumpirá siempre que se produzca la excepción, independientemente de si está controlada. Ahora la excepción se denomina primera excepción. A continuación se muestran un par de escenarios de ejemplo:

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

  Si activó **AccessViolationException** en **Configuración de excepciones**, la ejecución se interrumpirá en la línea `throw` al ejecutar este código en el depurador. A continuación puede continuar la ejecución. La consola debería mostrar ambas líneas:

  ```cmd
  caught exception
  goodbye
  ```

  pero no muestra la línea `here`.

- Una aplicación de consola de C# hace referencia a una biblioteca de clases con una clase que tiene dos métodos. Un método produce una excepción y la controla, mientras que un segundo método produce la misma excepción, pero no la controla.

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

  Si activó **AccessViolationException** en **Configuración de excepciones**, la ejecución se interrumpirá en la línea `throw` en las dos excepciones **ThrowHandledException()** y **ThrowUnhandledException()** cuando ejecute este código en el depurador.

Para restaurar la configuración de excepciones a los valores predeterminados, haga clic en el botón **Restaurar la lista a la configuración predeterminada**:

![Restaurar valores predeterminados en Configuración de excepciones](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>Indicar al depurador que continúe en las excepciones no controladas por el usuario

Si está depurando código .NET o JavaScript con [Solo mi código](../debugger/just-my-code.md), puede indicar al depurador que impida la interrupción de la ejecución en excepciones que no se controlan en el código de usuario, sino que se controlan en otro lugar.

1. En la ventana **Configuración de excepciones**, abra el menú contextual haciendo clic con el botón derecho en una etiqueta de columna y, después, seleccione **Mostrar columnas > Acciones adicionales**. (Si ha desactivado **Solo mi código**, no verá este comando). Aparecerá una tercera columna denominada **Acciones adicionales**.

   ![Columna Acciones adicionales](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   En el caso de una excepción que muestre **Continuar cuando no se controle en el código de usuario** en esta columna, el depurador continuará si dicha excepción no se controla en el código de usuario, sino que se administrará externamente.

2. Para cambiar esta configuración para una excepción determinada, seleccione la excepción, haga clic con el botón derecho para mostrar el menú contextual y seleccione **Continuar cuando no se controle en el código de usuario**. También puede cambiar la configuración de una categoría de excepciones completa, como todas las excepciones de Common Language Runtime.

   ![Opción **Continuar cuando no se controle en el código de usuario**](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Por ejemplo, para controlar las excepciones, las aplicaciones web ASP.NET las convierten en un código de estado HTTP 500 ([Control de excepciones en ASP.NET Web API](/aspnet/web-api/overview/error-handling/exception-handling)), lo cual podría no ser una ayuda a la hora de determinar el origen de la excepción. En el ejemplo siguiente, el código del usuario realiza una llamada a `String.Format()` que produce una excepción <xref:System.FormatException>. La ejecución se interrumpe del modo siguiente:

![Excepción no controlada interrumpida en el usuario](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Agregar y eliminar excepciones

Las excepciones se pueden agregar y eliminar. Para eliminar un tipo de excepción de una categoría, seleccione la excepción y haga clic en el botón **Eliminar la excepción seleccionada de la lista** (el signo menos) de la barra de herramientas **Configuración de excepciones**. O bien, puede hacer clic con el botón derecho en la excepción y seleccionar **Eliminar** en el menú contextual. Eliminar una excepción tiene el mismo efecto que no activar la excepción: el depurador no se interrumpirá cuando se produzca la excepción.

Para agregar una excepción:

1. En la ventana **Configuración de excepciones**, seleccione una de las categorías de excepciones (por ejemplo, **Common Language Runtime**).

2. Haga clic en el botón **Agregar una excepción a la categoría seleccionada** (el signo más).

   ![Botón **Agregar una excepción a la categoría seleccionada**](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Escriba el nombre de la excepción (por ejemplo, **System.UriTemplateMatchException**).

   ![Escriba el tipo de excepción.](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   La excepción se agrega a la lista (en orden alfabético) y se activa automáticamente.

Para agregar una excepción a las excepciones de acceso a la memoria de GPU, a las excepciones de JavaScript en tiempo de ejecución o a las excepciones de Win32, incluya el código de error y la descripción.

> [!TIP]
> No olvide revisar la ortografía. La ventana **Configuración de excepciones** no comprueba la existencia de una excepción agregada. Por lo tanto, si escribe **Sytem.UriTemplateMatchException**, se creará una entrada para esa excepción (y no para **System.UriTemplateMatchException**).

La configuración de excepciones se conserva en el archivo .suo de la solución, por lo que se aplican a una solución concreta. Esta configuración de excepciones específica no se puede reutilizar en otras soluciones. Actualmente solo se conservan las excepciones agregadas, no las eliminadas. Puede agregar una excepción, cerrar la solución y volver a abrirla, y la excepción seguirá estando ahí. Pero si elimina una excepción y cierra y vuelve a abrir la solución, volverá a aparecer la excepción.

La ventana **Configuración de excepciones** admite tipos genéricos de excepciones en C#, pero no en Visual Basic. Para interrumpir la ejecución en excepciones como `MyNamespace.GenericException<T>`, agregue la excepción como **MyNamespace.GenericException`1**. Es decir, si creó una excepción como este código:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Puede agregar la excepción a **Configuración de excepciones** con el procedimiento anterior:

![Adición de excepción genérica](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Adición de condiciones a una excepción

Use la ventana **Configuración de excepciones** para establecer condiciones en las excepciones. Las condiciones admitidas actualmente incluyen los nombres de los módulos que se van a incluir o excluir para la excepción. Al establecer los nombres de los módulos como condiciones, puede elegir interrumpir la excepción solo en determinados módulos de código. También puede optar por evitar la interrupción en módulos concretos.

> [!NOTE]
> Se admite la adición de condiciones a una excepción a partir de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Para agregar excepciones condicionales:

1. Haga clic en el botón **Editar condiciones** de la ventana Configuración de excepciones, o haga clic con el botón derecho en la excepción y seleccione **Editar condiciones**.

   ![Condiciones para una excepción](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Para agregar condiciones adicionales necesarias a la excepción, seleccione **Agregar condición** para cada nueva condición. Aparecen líneas de condiciones adicionales.

   ![Condiciones adicionales para una excepción](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Para cada línea de condición, escriba el nombre del módulo y cambie la lista de operadores de comparación a **Es igual a** o **No es igual a**. Puede especificar caracteres comodín ( **\\\*** ) en el nombre para especificar más de un módulo.

4. Si necesita eliminar una condición, elija la **X** al final de la línea de condición.

## <a name="see-also"></a>Vea también

- [Continuación de la ejecución después de una excepción](../debugger/continuing-execution-after-an-exception.md)<br/>
- [Cómo: examinar el código del sistema después de una excepción](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [Cómo: usar comprobaciones nativas en tiempo de ejecución](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
