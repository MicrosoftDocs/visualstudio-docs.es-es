---
title: Administrar excepciones con el depurador . Microsoft Docs
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301126"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Administrar excepciones con el depurador en Visual Studio

Una excepción es una indicación de estado de error que se produce mientras se ejecuta un programa. Puede indicar al depurador qué excepciones o conjuntos de excepciones interrumpir y en qué momento desea que se interrumpa el depurador (es decir, pausar en el depurador). Cuando se interrumpe el depurador, se muestra dónde se ha producido la excepción. También puede agregar o eliminar excepciones. Con una solución abierta en Visual Studio, use **Depurar > Windows > Configuración de excepciones** para abrir la ventana Configuración de **excepciones.**

Proporcione controladores que respondan a las excepciones más importantes. Si necesita saber cómo agregar controladores para excepciones, vea [Corregir errores escribiendo un mejor código de C.](../debugger/write-better-code-with-visual-studio.md) Además, obtenga información sobre cómo configurar el depurador para interrumpir siempre la ejecución de algunas excepciones.

Cuando se produce una excepción, el depurador escribe un mensaje de excepción **en** la salida ventana. Puede interrumpir la ejecución en los siguientes casos cuando:

- Se produce una excepción que no se controla.
- El depurador está configurado para interrumpir la ejecución antes de invocar cualquier controlador.
- Ha establecido [Solo mi código](../debugger/just-my-code.md)y el depurador está configurado para interrumpir cualquier excepción que no se controle en el código de usuario.

> [!NOTE]
> ASP.NET tiene un controlador de excepciones de nivel superior que muestra las páginas de error en un explorador. No interrumpe la ejecución a menos que **Just My Code** esté activado. Para obtener un ejemplo, vea [Indicar al depurador que continúe en las excepciones no controladas](#BKMK_UserUnhandled) por el usuario a continuación.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> En una aplicación de Visual Basic, el depurador administra todos los errores como excepciones, incluso si se usan controladores de error de tipo On Error.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Indique al depurador que se interrumpa cuando se produzca una excepción

El depurador puede interrumpir la ejecución en el punto donde se produce una excepción, por lo que puede examinar la excepción antes de invocar un controlador.

En la ventana **Configuración** de excepciones ( Depurar > Windows > Configuración de**excepciones**), expanda el nodo de una categoría de excepciones, como **Excepciones**de Common Language Runtime . A continuación, active la casilla de verificación de una excepción específica dentro de esa categoría, como **System.AccessViolationException**. También puede seleccionar una categoría de excepciones completa.

![AccessViolationException comprobado](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Puede encontrar excepciones específicas mediante la ventana **Buscar** de la barra de herramientas Configuración de **excepciones** o usar la búsqueda para filtrar espacios de nombres específicos (como **System.IO**).

Si selecciona una excepción en la ventana **Configuración** de excepción, la ejecución del depurador se interrumpirá dondequiera que se produzca la excepción, independientemente de si se controla. Ahora la excepción se denomina una excepción de primera oportunidad. A continuación se muestran un par de escenarios de ejemplo:

- En la siguiente aplicación de consola de C, el `try/catch` método Main produce una **excepción AccessViolationException** dentro de un bloque.

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

  Si tiene **AccessViolationException** activado en Configuración de `throw` **excepciones**, la ejecución se interrumpirá en la línea cuando ejecute este código en el depurador. A continuación puede continuar la ejecución. La consola debería mostrar ambas líneas:

  ```cmd
  caught exception
  goodbye
  ```

  pero no muestra la `here` línea.

- Una aplicación de consola de C- hace referencia a una biblioteca de clases con una clase que tiene dos métodos. Un método produce una excepción y la controla, mientras que un segundo método produce la misma excepción, pero no la controla.

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

  Si tiene **AccessViolationException** activado en Configuración de `throw` **excepciones**, la ejecución se interrumpirá en la línea en **ThrowHandledException()** y **ThrowUnhandledException()** al ejecutar este código en el depurador.

Para restaurar la configuración de excepción a los valores predeterminados, elija el botón **Restaurar la lista a la configuración predeterminada:**

![Restaurar valores predeterminados en Configuración de excepciones](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>Indique al depurador que continúe con las excepciones no controladas por el usuario

Si está depurando código .NET o JavaScript con [Just My Code](../debugger/just-my-code.md), puede indicar al depurador que evite interrumpir las excepciones que no se controlan en el código de usuario pero que se controlan en otro lugar.

1. En la ventana Configuración de **excepciones,** abra el menú contextual haciendo clic con el botón derecho en una etiqueta de columna y, a continuación, seleccione **Mostrar columnas > Acciones adicionales**. (Si ha desactivado **Solo mi código**, no verá este comando.) Aparece una tercera columna denominada **Acciones adicionales.**

   ![Columna Acciones adicionales](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   Para una excepción que muestra **Continuar cuando no se controla en el código** de usuario de esta columna, el depurador continúa si esa excepción no se controla en el código de usuario, pero se controla externamente.

2. Para cambiar esta configuración para una excepción determinada, seleccione la excepción, haga clic con el botón derecho para mostrar el menú contextual y seleccione **Continuar cuando no se controla en código**de usuario . También puede cambiar la configuración de toda una categoría de excepciones, como todas las excepciones de Common Language Runtime).

   ![**Continúe cuando no se manipule en el código de usuario** configuración](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Por ejemplo, ASP.NET aplicaciones web controlan las excepciones convirtiéndolas en un código de estado HTTP 500 (control de[excepciones en ASP.NET API web),](/aspnet/web-api/overview/error-handling/exception-handling)lo que puede no ayudarle a determinar el origen de la excepción. En el ejemplo siguiente, el código del usuario realiza una llamada a `String.Format()` que produce una excepción <xref:System.FormatException>. La ejecución se interrumpe del modo siguiente:

![Interrupciones en el usuario&#45;excepción no controlada](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Agregar y eliminar excepciones

Las excepciones se pueden agregar y eliminar. Para eliminar un tipo de excepción de una categoría, seleccione la excepción y elija **Eliminar la excepción seleccionada en el** botón de lista (el signo menos) de la barra de herramientas Configuración de **excepciones.** O puede hacer clic con el botón derecho en la excepción y seleccionar **Eliminar** en el menú contextual. La eliminación de una excepción tiene el mismo efecto que tener la excepción desactivada, que es que el depurador no se interrumpirá cuando se produzca.

Para agregar una excepción:

1. En la ventana Configuración de **excepción,** seleccione una de las categorías de excepción (por ejemplo, **Common Language Runtime**).

2. Elija el botón **Agregar una excepción a la categoría seleccionada** (el signo más).

   ![**Añadir una excepción al botón de categoría seleccionada**](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Escriba el nombre de la excepción (por ejemplo, **System.UriTemplateMatchException**).

   ![Escriba el nombre de la excepción](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   La excepción se agrega a la lista (en orden alfabético) y se comprueba automáticamente.

Para agregar una excepción a las categorías Excepciones de acceso a memoria de GPU, Excepciones de tiempo de ejecución de JavaScript o Excepciones de Win32, incluya el código de error y la descripción.

> [!TIP]
> No olvide revisar la ortografía. La ventana Configuración de **excepción** no comprueba la existencia de una excepción agregada. Por lo tanto, si escribe **Sytem.UriTemplateMatchException**, obtendrá una entrada para esa excepción (y no para **System.UriTemplateMatchException**).

La configuración de excepciones se conserva en el archivo .suo de la solución, por lo que se aplican a una solución concreta. Esta configuración de excepciones específica no se puede reutilizar en otras soluciones. Ahora solo se conservan las excepciones añadidas; excepciones eliminadas no lo son. Puede agregar una excepción, cerrar y volver a abrir la solución, y la excepción seguirá estando allí. Pero si elimina una excepción y cierra y vuelve a abrir la solución, volverá a aparecer la excepción.

La ventana **Configuración de excepciones** admite tipos genéricos de excepciones en C#, pero no en Visual Basic. Para interrumpir la ejecución en excepciones como `MyNamespace.GenericException<T>`, agregue la excepción como **MyNamespace.GenericException`1**. Es decir, si ha creado una excepción como este código:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Puede agregar la excepción a La configuración de **excepciones** mediante el procedimiento anterior:

![Agregar excepción genérica](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Añadir condiciones a una excepción

Utilice la ventana Configuración de **excepciones** para establecer condiciones en las excepciones. Las condiciones admitidas actualmente incluyen los nombres de módulo que se incluirán o excluirán para la excepción. Al establecer los nombres de módulo como condiciones, puede optar por interrumpir la excepción solo en determinados módulos de código. También puede evitar romper en módulos particulares.

> [!NOTE]
> Se admite la adición [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]de condiciones a una excepción a partir de .

Para agregar excepciones condicionales:

1. Elija el botón **Editar condiciones** en la ventana Configuración de excepción o haga clic con el botón derecho en la excepción y elija **Editar condiciones**.

   ![Condiciones para una excepción](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Para agregar condiciones necesarias adicionales a la excepción, seleccione **Agregar condición** para cada nueva condición. Aparecen líneas de condición adicionales.

   ![Condiciones adicionales para una excepción](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Para cada línea de condición, escriba el nombre del módulo y cambie la lista de operadores de comparación a **Equals** o **Not Equals**. Puede especificar comodines (**\\**) en el nombre para especificar más de un módulo.

4. Si necesita eliminar una condición, elija la **X** al final de la línea de condición.

## <a name="see-also"></a>Consulte también

- [Continuación de la ejecución después de una excepción](../debugger/continuing-execution-after-an-exception.md)<br/>
- [Análisis del código del sistema después de una excepción](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [Uso de comprobaciones nativas en tiempo de ejecución](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [Utilice comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
- [Primero mire el depurador](../debugger/debugger-feature-tour.md)
