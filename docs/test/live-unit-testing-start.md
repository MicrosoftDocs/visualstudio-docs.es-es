---
title: Más información sobre cómo probar el código con Live Unit Test
description: Obtenga información sobre cómo usar Live Unit Testing mediante la creación de una biblioteca de clases sencilla que tiene como destino .NET Standard y creando un proyecto de MSTest, cuyo destino es .NET Core, para probarlo.
ms.custom: SEO-VS-2020
ms.date: 04/03/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: ea87135b1f60c7ae65a8bc25399604151ab2fcee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887814"
---
# <a name="get-started-with-live-unit-testing"></a>Introducción a Live Unit Testing

Live Unit Testing, cuando se habilita en una solución de Visual Studio, representa visualmente la cobertura y el estado de las pruebas. Live Unit Testing también ejecuta dinámicamente pruebas cada vez que modifica el código y le notifica inmediatamente cuando sus cambios provocan un error en las pruebas.

Live Unit Testing puede utilizarse para probar soluciones que tienen como destino .NET Framework o .NET Core. En este tutorial, obtendrá información sobre cómo utilizar Live Unit Testing mediante la creación de una biblioteca de clases sencilla que tiene como destino .NET Standard y podrá crear un proyecto de MSTest, cuyo destino es .NET Core, para probarlo.

La solución completa de C# puede descargarse desde el repositorio [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) en GitHub.

## <a name="prerequisites"></a>Requisitos previos

Este tutorial exige la instalación previa de Visual Studio Enterprise con la carga de trabajo del **desarrollo multiplataforma de .NET Core**.

## <a name="create-the-solution-and-the-class-library-project"></a>Creación de la solución y del proyecto de biblioteca de clases

Empiece por crear una solución de Visual Studio denominada UtilityLibraries que conste de un solo proyecto de biblioteca de clases de .NET Standard, StringLibrary.

La solución es simplemente un contenedor para uno o varios proyectos. Para crear una solución en blanco, abra Visual Studio y haga lo siguiente:

1. Seleccione **Archivo** > **Nuevo** > **Proyecto** en el menú de nivel superior de Visual Studio.

1. Escriba **solución** en el cuadro de búsqueda de la plantilla y luego seleccione la plantilla **Solución en blanco**. Asigne el nombre **UtilityLibraries** al proyecto.

   ::: moniker range="vs-2017"

   ![Cuadro de diálogo **Nuevo proyecto**](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Termine de crear la solución.

Ahora que ha creado la solución, podrá crear una biblioteca de clases denominada StringLibrary que contenga una serie de métodos de extensión para trabajar con cadenas.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en la solución UtilityLibraries y seleccione **Agregar** > **Nuevo proyecto**.

::: moniker range="vs-2017"

2. En el cuadro de diálogo **Agregar nuevo proyecto**, seleccione el nodo de C# y, después, **.NET Standard**.

   > [!NOTE]
   > Debido a que nuestra biblioteca tiene como destino .NET Standard en lugar de una implementación concreta de .NET, se puede llamar desde cualquier implementación de .NET que admita esa versión de .NET Standard. Para más información, consulte [.NET Standard](/dotnet/standard/net-standard).

3. Seleccione la plantilla **Biblioteca de clases (.NET Standard)** en el panel derecho y escriba **StringLibrary** en el cuadro de texto **Nombre**, como se muestra en la ilustración siguiente:

   ![Cuadro de diálogo **Agregar nuevo proyecto**](./media/lut-start/add-project-cs.png)

4. Seleccione **Aceptar** para crear el proyecto.

::: moniker-end

::: moniker range=">=vs-2019"

2. Escriba **biblioteca de clases** en el cuadro de búsqueda de la plantilla y seleccione la plantilla **Biblioteca de clases (.NET Standard)** . Haga clic en **Siguiente**.

   > [!NOTE]
   > Debido a que nuestra biblioteca tiene como destino .NET Standard en lugar de una implementación concreta de .NET, se puede llamar desde cualquier implementación de .NET que admita esa versión de .NET Standard. Para más información, consulte [.NET Standard](/dotnet/standard/net-standard).

3. Asigne al proyecto el nombre **StringLibrary**.

4. Haga clic en **Crear** para crear el proyecto.

::: moniker-end

5. Reemplace todo el código existente en el editor de código por el siguiente:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   StringLibrary tiene tres métodos estáticos:

   - `StartsWithUpper` devuelve `true` si una cadena comienza por una letra mayúscula; en caso contrario, devuelve `false`.

   - `StartsWithLower` devuelve `true` si una cadena comienza por una letra minúscula; en caso contrario, devuelve `false`.

   - `HasEmbeddedSpaces` devuelve `true` si una cadena contiene un espacio en blanco insertado; en caso contrario, devuelve `false`.

6. Seleccione **Compilar** > **Compilar solución** en el menú de nivel superior de Visual Studio. La compilar debería ser correcta.

## <a name="create-the-test-project"></a>Crear el proyecto de prueba

El paso siguiente consiste en crear el proyecto de prueba unitaria para probar la biblioteca StringLibrary. Siga estos pasos para crear las pruebas unitarias:

1. En el **Explorador de soluciones**, haga clic con el botón derecho en la solución UtilityLibraries y seleccione **Agregar** > **Nuevo proyecto**.

::: moniker range="vs-2017"

2. En el cuadro de diálogo **Agregar nuevo proyecto**, seleccione el nodo de C# y, después, **.NET Core**.

   > [!NOTE]
   > No es necesario escribir las pruebas unitarias en el mismo lenguaje que el de la biblioteca de clases.

3. Seleccione la plantilla **Proyecto de prueba unitaria (.NET Core)** en el panel derecho y escriba **StringLibraryTests** en el cuadro de texto **Nombre**, como se muestra en la ilustración siguiente:

   ![Cuadro de diálogo **Agregar nuevo proyecto** para el proyecto de prueba unitaria](./media/lut-start/add-unit-test-cs.png)

4. Seleccione **Aceptar** para crear el proyecto.

::: moniker-end

::: moniker range=">=vs-2019"

2. Escriba **prueba unitaria** en el cuadro de búsqueda de plantillas y seleccione la plantilla **Proyecto de prueba de MSTest (.NET Core)** . Haga clic en **Siguiente**.

3. Asigne al proyecto el nombre **StringLibraryTests**.

4. Haga clic en **Crear** para crear el proyecto.

::: moniker-end

   > [!NOTE]
   > En este tutorial de introducción, Live Unit Testing se utiliza con el marco de pruebas de MSTest. También puede usar los marcos de pruebas de xUnit y NUnit.

5. El proyecto de prueba unitaria no puede acceder automáticamente a la biblioteca de clases que está probando. Para conceder acceso a la biblioteca de prueba, agregue una referencia al proyecto de biblioteca de clases. Para ello, haga clic con el botón derecho en el proyecto `StringLibraryTests` y seleccione **Agregar** > **Referencia**. En el cuadro de diálogo **Administrador de referencias**, asegúrese de que la pestaña **Solución** esté seleccionada y elija el proyecto StringLibrary, como se muestra en la ilustración siguiente.

   ![Cuadro de diálogo **Administrador de referencias**](./media/lut-start/add-reference.png)

6. Reemplace el código de prueba unitaria reutilizable que proporciona la plantilla por el código siguiente:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. Guarde el proyecto seleccionando el icono **Guardar** de la barra de herramientas.

   Como el código de prueba unitaria incluye algunos caracteres que no son ASCII, verá el cuadro de diálogo siguiente en el que se advierte de que algunos caracteres se perderán si el archivo se guarda en el formato ASCII predeterminado.

8. Elija el botón **Guardar con otra codificación**.

   ![Elegir una codificación de archivos](media/lut-start/ascii-encoding.png)

9. En la lista desplegable **Codificación** del cuadro de diálogo **Opciones avanzadas para guardar**, elija **Unicode (UTF-8 sin signatura) - Página de códigos 65001**, como se muestra en la ilustración siguiente:

   ![Elegir la codificación UTF-8](media/lut-start/utf8-encoding.png)

10. Para compilar el proyecto de prueba unitaria, seleccione **Compilar** > **Recompilar solución** en el menú de nivel superior de Visual Studio.

Ha creado una biblioteca de clases, así como algunas pruebas unitarias la misma. Ya ha completado los pasos preliminares necesarios para utilizar Live Unit Testing.

## <a name="enable-live-unit-testing"></a>Habilitar Live Unit Testing

Hasta ahora, aunque ha escrito las pruebas para la biblioteca de clases StringLibrary, no las ha ejecutado. Live Unit Testing las ejecuta automáticamente una vez que lo habilite. Para ello, haga lo siguiente:

1. Si quiere, seleccione la ventana del editor de código que contiene el código para StringLibrary. Se trata de *Class1.cs* para un proyecto de C# o de *Class1.vb* para un proyecto de Visual Basic. Este paso le permite inspeccionar visualmente el resultado de las pruebas y el alcance de la cobertura de código una vez que habilite Live Unit Testing.

1. Seleccione **Prueba** > **Live Unit Testing** > **Iniciar** en el menú de nivel superior de Visual Studio.

1. Visual Studio inicia Live Unit Testing, que ejecuta automáticamente todas las pruebas.

::: moniker range="vs-2017"
Cuando acaba de ejecutar las pruebas, el **Explorador de pruebas** muestra los resultados globales y el resultado de las pruebas individuales. Además, en la ventana del editor de código se muestra gráficamente la cobertura del código de prueba y el resultado de las pruebas. Como se muestra en la ilustración siguiente, las tres pruebas se han ejecutado correctamente. También muestra que nuestras pruebas han cubierto todas las rutas de acceso de código en el método `StartsWithUpper` y que esas pruebas se han ejecutado correctamente (lo que se indica mediante la marca de verificación de color verde, "✓"). Por último, muestra que ninguno de los otros métodos de StringLibrary tiene cobertura de código (lo que se indica mediante una línea azul, "➖").

![Explorador de pruebas y ventana del editor de código después de iniciar Live Unit Testing](media/lut-start/lut-results-cs.png)
::: moniker-end
::: moniker range=">=vs-2019"
Cuando se termina de ejecutar las pruebas, en **Live Unit Testing** se muestran los resultados globales y el resultado de las pruebas individuales. Además, en la ventana del editor de código se muestra gráficamente la cobertura del código de prueba y el resultado de las pruebas. Como se muestra en la ilustración siguiente, las tres pruebas se han ejecutado correctamente. También muestra que nuestras pruebas han cubierto todas las rutas de acceso de código en el método `StartsWithUpper` y que esas pruebas se han ejecutado correctamente (lo que se indica mediante la marca de verificación de color verde, "✓"). Por último, muestra que ninguno de los otros métodos de StringLibrary tiene cobertura de código (lo que se indica mediante una línea azul, "➖").

![Explorador de pruebas en directo y ventana del editor de código después de iniciar Live Unit Testing](media/lut-start/vs-2019/lut-results-cs.png)
::: moniker-end

También puede obtener información más detallada sobre la cobertura y los resultados de las pruebas si selecciona un icono de cobertura de código determinado en la ventana del editor de código. Para examinar este detalle, haga lo siguiente:

1. Haga clic en la marca de verificación verde situada en la línea `if (String.IsNullOrWhiteSpace(s))` del método `StartsWithUpper`. Como se muestra en la ilustración siguiente, Live Unit Testing indica que las tres pruebas cubren esa línea de código y que todas se han ejecutado correctamente.

   ![Cobertura de código para la instrucción condicional "if"](media/lut-start/code-coverage-cs1.png)

1. Haga clic en la marca de verificación verde situada en la línea `return Char.IsUpper(s[0])` del método `StartsWithUpper`. Como se muestra en la ilustración siguiente, Live Unit Testing indica que solo dos pruebas cubren esa línea de código y que todas se han ejecutado correctamente.

   ![Cobertura de código para la instrucción Return](media/lut-start/code-coverage-cs2.png)

El problema principal que Live Unit Testing identifica es la cobertura de código incompleta. Este tema se tratará en la sección siguiente.

## <a name="expand-test-coverage"></a>Expandir la cobertura de pruebas

En esta sección, podrá ampliar las pruebas unitarias al método `StartsWithLower`. Al hacerlo, Live Unit Testing continuará dinámicamente para probar el código.

Para ampliar la cobertura de código al método `StartsWithLower`, haga lo siguiente:

1. Agregue los métodos `TestStartsWithLower` y `TestDoesNotStartWithLower` al archivo de código fuente de prueba del proyecto:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Modifique el método `DirectCallWithNullOrEmpty` agregando el código siguiente inmediatamente después de la llamada al método [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse).

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Cuando se modifica el código fuente, Live Unit Testing ejecuta automáticamente las pruebas nuevas y modificadas. Como se muestra en la ilustración siguiente, todas las pruebas, incluidas las dos que se han agregado y la que se ha modificado, se han realizado correctamente.

   ::: moniker range="vs-2017"
   ![Explorador de pruebas después de expandir la cobertura de las pruebas](media/lut-start/test-dynamic.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![El explorador de pruebas en directo después de expandir la cobertura de las pruebas](media/lut-start/vs-2019/test-dynamic.png)
   ::: moniker-end

1. Cambie a la ventana que contiene el código fuente de la clase StringLibrary. Ahora, Live Unit Testing muestra que nuestra cobertura de código se ha extendido al método `StartsWithLower`.

    ![Cobertura de código para el método StartsWithLower](media/lut-start/lut-extended-cs.png)

En algunos casos, las pruebas correctas pueden mostrarse deshabilitadas en el **Explorador de pruebas**. Eso indica que una prueba se está ejecutando actualmente, o que la prueba no se ha vuelto a ejecutar porque no ha habido ningún cambio en el código que pudiera afectar a la prueba desde que se ejecutó por última vez.

Hasta ahora, todas nuestras pruebas se han realizado correctamente. En la siguiente sección, examinaremos cómo puede controlar los errores de pruebas.

## <a name="handle-a-test-failure"></a>Controlar errores de pruebas

En esta sección, explorará cómo puede usar Live Unit Testing para identificar, solucionar y abordar los errores de pruebas. Para ello, debe expandir la cobertura de las pruebas al método `HasEmbeddedSpaces`.

1. Agregue el método siguiente al archivo de prueba:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Cuando se ejecuta la prueba, en Live Unit Testing se indica que se ha producido un error en el método `TestHasEmbeddedSpaces`, como se muestra en la ilustración siguiente:

   ::: moniker range="vs-2017"
   ![Explorador de pruebas informando de una prueba errónea](media/lut-start/test-failure.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![El explorador de pruebas en directo con la notificación de una prueba con errores](media/lut-start/vs-2019/test-failure.png)
   ::: moniker-end

1. Seleccione la ventana en la que se muestra el código de biblioteca. Live Unit Testing ha ampliado la cobertura de código al método `HasEmbeddedSpaces`. También informa de los errores de pruebas agregando un símbolo "🞩" rojo a las líneas cubiertas por pruebas erróneas.

1. Mantenga el mouse sobre la línea que contiene la signatura del método `HasEmbeddedSpaces`. En Live Unit Testing se muestra información que indica que una prueba cubre el método, como se muestra en la ilustración siguiente:

   ![Información de Live Unit Testing sobre una prueba errónea](media/lut-start/test-failure-info-cs.png)

1. Seleccione la prueba errónea **TestHasEmbeddedSpaces**. En Live Unit Testing se proporcionan algunas opciones, como la ejecución y la depuración de todas las pruebas, como se muestra en la ilustración siguiente:

   ::: moniker range="vs-2017"
   ![Opciones de Live Unit Testing para una prueba errónea](media/lut-start/test-failure-options.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Opciones de Live Unit Testing para una prueba errónea](media/lut-start/vs-2019/test-failure-options.png)
   ::: moniker-end

1. Seleccione **Depurar todo** para depurar la prueba con error.

1. Visual Studio ejecuta la prueba en modo de depuración.

   La prueba asigna cada cadena de una matriz a una variable denominada `phrase` y la pasa al método `HasEmbeddedSpaces`. La ejecución del programa se pone en pausa e invoca al depurador la primera vez que la expresión de aserción es `false`. En la ilustración siguiente se muestra el cuadro de diálogo de excepción que resulta del valor inesperado en la llamada al método [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue).

   ![Cuadro de diálogo de excepción de Live Unit Testing](media/lut-start/exception-dialog-cs.png)

   Además, todas las herramientas de depuración que proporciona Visual Studio están disponibles para facilitar la solución de problemas en la prueba con error, como se muestra en la ilustración siguiente:

   ![Herramientas de depuración de Visual Studio](media/lut-start/debugging-tools-cs.png)

   Tenga en cuenta que, en la ventana **Automático**, el valor de la variable `phrase` es "Name\tDescription", que es el segundo elemento de la matriz. El método de prueba espera que `HasEmbeddedSpaces` devuelva `true` cuando se le pasa esta cadena; en su lugar, devuelve `false`. Evidentemente, no reconoce "\t", el carácter de tabulación, como un espacio insertado.

1. Seleccione **Depurar** > **Continuar**, presione **F5** o haga clic en el botón **Continuar** de la barra de herramientas para continuar ejecutando el programa de prueba. La prueba ha finalizado porque se ha producido una excepción no controlada.
Esto proporciona información suficiente para una investigación preliminar del error. `TestHasEmbeddedSpaces`, la rutina de prueba, ha realizado una suposición incorrecta, o bien `HasEmbeddedSpaces` no reconoce correctamente todos los espacios insertados.

1. Para diagnosticar y corregir el problema, comience por el método `StringLibrary.HasEmbeddedSpaces`. Mire la comparación en el método `HasEmbeddedSpaces`. Considera que U+0020 es un espacio insertado. Sin embargo, el estándar Unicode incluye otros caracteres de espacio. Esto sugiere que el código de biblioteca ha probado incorrectamente la presencia de un carácter de espacio en blanco.

1. Reemplace la comparación de igualdad por una llamada al método <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName>:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing vuelve a ejecutar de forma automática el método de prueba con errores.

   En Live Unit Testing se muestran los resultados actualizados, que también aparecen en la ventana del editor de código.

## <a name="see-also"></a>Vea también

- [Live Unit Testing en Visual Studio](live-unit-testing.md)
- [Preguntas más frecuentes sobre Live Unit Testing](live-unit-testing-faq.md)
