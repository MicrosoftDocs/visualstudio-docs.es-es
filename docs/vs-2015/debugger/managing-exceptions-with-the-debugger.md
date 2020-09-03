---
title: Administrar excepciones con el depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 45b681b8d146fcc4ca8b056cd94bb0ef65cae826
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918954"
---
# <a name="managing-exceptions-with-the-debugger"></a>Administración de excepciones con el depurador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una excepción es una indicación de estado de error que se produce mientras se ejecuta un programa. Se puede y es recomendable proporcionar controladores que respondan a las excepciones principales, pero es importante saber cómo configurar el depurador para que interrumpa la ejecución en las excepciones que desee ver.  
  
 Cuando se produce una excepción, el depurador escribe un mensaje en la ventana Salida. La ejecución se puede interrumpir en los casos siguientes:  
  
- Cuando se produce una excepción y no se controla.  
  
- Cuando el depurador está configurado para interrumpir de inmediato la ejecución cuando se produce una excepción, antes de que se invoque ningún controlador.  
  
- Si se ha establecido [Just My Code](../debugger/just-my-code.md)y el depurador está configurado para interrumpir la ejecución en cualquier excepción que no esté controlada en el código del usuario.  
  
> [!NOTE]
> ASP.NET tiene un controlador de excepciones de nivel superior que muestra las páginas de error en un explorador. No interrumpe la ejecución a menos que **Solo mi código** esté activado. Para obtener un ejemplo, consulta [Setting the debugger to continue on user-unhandled exceptions](../debugger/managing-exceptions-with-the-debugger.md#BKMK_UserUnhandled) a continuación.  
  
> [!NOTE]
> En una aplicación de Visual Basic, el depurador administra todos los errores como excepciones, incluso si se usan controladores de error del tipo “Al ocurrir un error”.  
  
## <a name="managing-exceptions-with-the-exception-settings-window"></a>Administrar excepciones con la ventana Configuración de excepciones  
 Mediante la ventana **Configuración de excepciones** se pueden especificar las excepciones (o los conjuntos de excepciones) que provocarán la interrupción del depurador y el momento en que se produce la interrupción. Las excepciones se pueden agregar o eliminar, y también es posible especificar aquellas en las que tendrá lugar la interrupción. Para abrir esta ventana cuando haya abierta una solución, haga clic en **Depurar/Ventanas/Configuración de excepciones**.  
  
 Si quiere buscar una determinada excepción, use la ventana **Buscar** de la barra de herramientas de **Configuración de excepciones** . También puede usar la búsqueda para filtrar espacios de nombres específicos (por ejemplo **System.IO**).  
  
### <a name="setting-the-debugger-to-break-when-an-exception-is-thrown"></a>Configurar el depurador para interrumpir la ejecución cuando se produce una excepción  
 El depurador puede interrumpir la ejecución en el momento en que se produce una excepción, permitiendo así depurarla antes de que se invoque un controlador.  
  
 En la ventana **Configuración de excepciones** , expanda el nodo de una categoría de excepciones (por ejemplo, **Excepciones de Common Language Runtime**, es decir, las excepciones. NET) y active la casilla de una excepción concreta dentro de esa categoría (por ejemplo **System.AccessViolationException**). También puede seleccionar una categoría de excepciones completa.  
  
 ![AccessViolationException comprobado](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")  
  
 Si activa una determinada excepción, la ejecución del depurador se interrumpirá siempre que se produzca la excepción, independientemente de si está controlada o no. En este punto, la excepción se denomina primera excepción. A continuación se muestran un par de escenarios de ejemplo:  
  
1. En la siguiente aplicación de consola de C#, el método Main produce **AccessViolationException** dentro de un `try/catch` bloque:  
  
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
  
    Si activó **AccessViolationException** en la **Configuración de excepciones**y ejecuta este código en el depurador, la ejecución se interrumpirá en la línea `throw` . A continuación puede continuar la ejecución. La consola debería mostrar ambas líneas:  
  
   ```  
   caught exception  
   goodbye  
   ```  
  
    Sin embargo, no muestra la línea `here` .  
  
2. Una aplicación de consola de C# hace referencia a una biblioteca de clases con una clase que tiene dos métodos, uno que produce una excepción y la controla, y otro que produce la misma excepción y no la controla:  
  
   ```vb  
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
  
    Si activó **AccessViolationException** en la **Configuración de excepciones**y ejecuta este código en el depurador, la ejecución se interrumpirá en la línea `throw` en las dos excepciones **ThrowHandledException()** y **ThrowUnhandledException()**.  
  
   Si desea restaurar la configuración de excepciones a los valores predeterminados, haga clic en el botón **Restaurar** de la barra de herramientas:  
  
   ![Restaurar valores predeterminados en Configuración de excepciones](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")  
  
### <a name="setting-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a> Establecer el depurador para continuar en las excepciones no controladas por el usuario  
 Si está depurando código .NET o JavaScript con [Just My Code](../debugger/just-my-code.md), puede indicar al depurador que no interrumpa la ejecución en excepciones que no se controlan en el código de usuario, pero que sí se controlan en otro lugar.  
  
1. En la ventana **Configuración de excepciones** , abra el menú contextual de una ventana con el botón derecho y, a continuación, seleccione **Mostrar columnas**. (Si ha desactivado **Solo mi código**, no verá este comando).  
  
2. Debería ver una segunda columna denominada **Acciones adicionales**. Esta columna muestra **Continuar si no está controlada en el código de usuario** en excepciones específicas, lo que significa que el depurador no se interrumpe si esa excepción no se controla en el código del usuario, pero sí se controla en código externo.  
  
3. Esta configuración se puede cambiar para excepciones concretas (seleccione la excepción, haga clic con el botón derecho y active o desactive **Continuar si no está controlada en el código de usuario**) o para toda una categoría de excepciones (por ejemplo, todas las excepciones de Common Language Runtime).  
  
   Por ejemplo, para controlar las excepciones, las aplicaciones web ASP.NET las convierten en un código de estado HTTP 500 ([Exception Handling in ASP.NET API](/aspnet/web-api/overview/error-handling/exception-handling)[Control de excepciones en la API de ASP.NET]), lo cual podría no ser una ayuda a la hora de determinar el origen de la excepción. En el ejemplo siguiente, el código del usuario realiza una llamada a `String.Format()` que produce una excepción <xref:System.FormatException>. La ejecución se interrumpe del modo siguiente:  
  
   ![interrupción en el usuario&#45;excepción unhanlded](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")  
  
### <a name="adding-and-deleting-exceptions"></a>Agregar y eliminar excepciones  
 Las excepciones se pueden agregar y eliminar. Puede eliminar cualquier tipo de excepción de cualquier categoría; para ello, seleccione la excepción y haga clic en el botón **Eliminar** (el signo menos) de la barra de herramientas de **Configuración de excepciones** , o haga clic con el botón derecho en la excepción y seleccione **Eliminar** en el menú contextual. Eliminar una excepción tiene el mismo efecto que no activar la excepción: el depurador no se interrumpirá cuando se produzca la excepción.  
  
 Para agregar una excepción: en la ventana **Configuración de excepciones** , seleccione una de las categorías de excepciones (por ejemplo, **Common Language Runtime**) y haga clic en el botón **Agregar** . Escriba el nombre de la excepción (por ejemplo, **System.UriTemplateMatchException**). La excepción se agrega a la lista (en orden alfabético) y se activa automáticamente.  
  
 Si desea agregar una excepción a las excepciones de acceso a la memoria de GPU, a las excepciones de JavaScript en tiempo de ejecución o a las excepciones de Win32, deberá incluir el código de error y la descripción.  
  
> [!TIP]
> No olvide revisar la ortografía. La ventana **configuración de excepciones** no comprueba la existencia de una excepción agregada. Por lo tanto, si escribe System **. UriTemplateMatchException**, obtendrá una entrada para esa excepción (y no para **System. UriTemplateMatchException**).  
  
 La configuración de excepciones se conserva en el archivo .suo de la solución, por lo que se aplican a una solución concreta. Esta configuración no se puede reutilizar en otras soluciones. Actualmente solo se conservan las excepciones agregadas, no las eliminadas. En otras palabras, puede agregar una excepción, cerrar la solución y volver a abrirla, y la excepción seguirá estando ahí. Pero si elimina una excepción y cierra y vuelve a abrir la solución, volverá a aparecer la excepción.  
  
 La ventana **Configuración de excepciones** admite tipos genéricos de excepciones en C#, pero no en Visual Basic. Para interrumpir la ejecución en excepciones como `MyNamespace.GenericException<T>`, agregue la excepción como **MyNamespace.GenericException`1**. Es decir, si creó una excepción como esta:  
  
```csharp  
public class GenericException<T> : Exception  
{  
    public GenericException() : base("This is a generic exception.")  
    {  
    }  
}  
```  
  
 Puede agregar la excepción a **Configuración de excepciones** del modo siguiente:  
  
 ![Adición de excepción genérica](../debugger/media/addgenericexception.png "AddGenericException")  
  
## <a name="see-also"></a>Consulte también  
 [Continuar la ejecución después de una excepción](../debugger/continuing-execution-after-an-exception.md)   
 [Cómo: examinar el código del sistema después de una excepción](../debugger/how-to-examine-system-code-after-an-exception.md)   
 [Cómo: utilizar comprobaciones nativas en tiempo de ejecución](../debugger/how-to-use-native-run-time-checks.md)   
 [Usar comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)   
 [Asistente de excepciones](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)
