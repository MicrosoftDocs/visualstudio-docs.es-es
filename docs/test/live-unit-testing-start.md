---
title: Más información sobre cómo probar el código con Live Unit Test 2017 | Microsoft Docs
ms.date: 08/31/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: bd4986d88654e584b3c05be2fd2b720b76be423a
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834258"
---
# <a name="get-started-with-live-unit-testing-in-visual-studio"></a>Comenzar a utilizar Live Unit Testing en Visual Studio

Al habilitar Live Unit Testing en una solución de Visual Studio, Live Unit Testing representa visualmente la cobertura y el estado de las pruebas. También ejecuta dinámicamente pruebas cada vez que modifica el código y le notifica inmediatamente cuando sus cambios provocan un error en las pruebas.

Live Unit Testing puede utilizarse para probar soluciones que tienen como destino .NET Framework o .NET Core. En este tutorial, obtendrá información sobre cómo utilizar Live Unit Testing mediante la creación de una biblioteca de clases sencilla que tiene como destino .NET Standard y podrá crear un proyecto de MSTest, cuyo destino es .NET Core, para probarlo.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
La solución completa de C# puede descargarse desde el repositorio [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) en GitHub.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
La solución completa de Visual Basic puede descargarse desde el repositorio [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/visual-basic/UtilityLibraries/) en GitHub.

---

## <a name="prerequisites"></a>Requisitos previos

Para completar este tutorial, debe haber instalado la versión 15.3 de Visual Studio 2017 Enterprise Edition con la carga de trabajo de .NET Core 2.0.

## <a name="create-the-solution-and-the-class-library-project"></a>Creación de la solución y del proyecto de biblioteca de clases

Empiece por crear una solución de Visual Studio denominada `UtilityLibraries`, que consta de un solo proyecto de biblioteca de clases de .NET Standard, `StringLibrary`. Puede escribir `StringLibrary` en C# o Visual Basic.

La solución es simplemente un contenedor para uno o varios proyectos. Para crear la solución, abra Visual Studio 2017 y haga lo siguiente:

1. Seleccione **Archivo** > **Nuevo** > **Proyecto** en el menú de nivel superior de Visual Studio.

1. En el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Otros tipos de proyectos** y seleccione **Soluciones de Visual Studio**. Seleccione la plantilla **Solución en blanco** en el panel derecho y escriba `UtilityLibraries` en el cuadro de texto **Nombre**, como se muestra en la figura siguiente:

   ![Cuadro de diálogo **Nuevo proyecto**](./media/lut-start/new-solution.png)

1. Seleccione **Aceptar** para crear la solución.

Ahora que ha creado la solución, podrá crear una biblioteca de clases denominada `StringLibrary`, que contiene una serie de métodos de extensión para trabajar con cadenas.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. En el **Explorador de soluciones**, haga clic con el botón derecho en la solución `UtilityLibraries` y seleccione **Agregar** > **Nuevo proyecto**.

1. En el cuadro de diálogo **Agregar nuevo proyecto**, seleccione el nodo de C# y, después, **.NET Standard**.

   > [!NOTE]
   > Debido a que nuestra biblioteca tiene como destino .NET Standard en lugar de una implementación concreta de .NET, se puede llamar desde cualquier implementación de .NET que admita esa versión de .NET Standard. Para más información, consulte [.NET Standard](/dotnet/standard/net-standard).

1. Seleccione la plantilla **Biblioteca de clases (.NET Standard)** en el panel derecho y escriba `StringLibrary` en el cuadro de texto **Nombre**, como se muestra en la figura siguiente:

   ![Cuadro de diálogo **Agregar nuevo proyecto**](./media/lut-start/add-project-cs.png)

1. Seleccione **Aceptar** para crear el proyecto.

1. Reemplace el código existente en la ventana de código por el código siguiente:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   `StringLibrary` tiene tres métodos estáticos:

      - `StartsWithUpper` devuelve `true` si una cadena comienza por una letra mayúscula; en caso contrario, devuelve `false`.

      - `StartsWithLower` devuelve `true` si una cadena comienza por una letra minúscula; en caso contrario, devuelve `false`.

      - `HasEmbeddedSpaces` devuelve `true` si una cadena contiene un espacio en blanco insertado; en caso contrario, devuelve `false`.

1.  Seleccione **Compilar** > **Compilar solución** en el menú de nivel superior de Visual Studio. Visual Studio compilará correctamente la biblioteca.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. En el **Explorador de soluciones**, haga clic con el botón derecho en la solución `UtilityLibraries` y seleccione **Agregar** > **Nuevo proyecto**.

1. En el cuadro de diálogo **Agregar nuevo proyecto**, seleccione el nodo de Visual Basic y, después, **.NET Standard**.

   > [!NOTE]
   > Debido a que nuestra biblioteca tiene como destino .NET Standard en lugar de una implementación concreta de .NET, se puede llamar desde cualquier implementación de .NET que admita esa versión de .NET Standard. Para más información, consulte [.NET Standard](/dotnet/standard/net-standard).

1. Seleccione la plantilla **Biblioteca de clases (.NET Standard)** en el panel derecho y escriba `StringLibrary` en el cuadro de texto **Nombre**, como se muestra en la figura siguiente:

   ![Cuadro de diálogo **Agregar nuevo proyecto**](./media/lut-start/add-project-vb.png)

1. Seleccione **Aceptar** para crear el proyecto.

1. Reemplace el código existente en la ventana de código por el código siguiente:

   [!code-vb[StringLibrary source code](samples/visual-basic/utilitylibraries/stringlibrary/class1.vb)]

   `StringLibrary` tiene tres métodos estáticos:

      - `StartsWithUpper` devuelve `true` si una cadena comienza por una letra mayúscula; en caso contrario, devuelve `false`.

      - `StartsWithLower` devuelve `true` si una cadena comienza por una letra minúscula; en caso contrario, devuelve `false`.

      - `HasEmbeddedSpaces` devuelve `true` si una cadena contiene un espacio en blanco insertado; en caso contrario, devuelve `false`.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto StringLibrary y seleccione **Propiedades**. En la pestaña **Aplicación**, elimine el texto del cuadro de texto **Espacio de nombres raíz**, como se muestra en la figura siguiente. El espacio de nombres raíz se define mediante la [instrucción Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement) en el código fuente.

   ![Cuadro de diálogo Propiedades del proyecto para un proyecto de Visual Basic](./media/lut-start/vb-properties.png)

1.  Seleccione **Compilar** > **Compilar solución** en el menú de nivel superior de Visual Studio. Visual Studio compilará correctamente la biblioteca.

---

## <a name="create-the-test-project"></a>Crear el proyecto de prueba

El paso siguiente consiste en crear el proyecto de prueba unitaria para probar la biblioteca de `StringLibrary`. Siga estos pasos para crear las pruebas unitarias:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. En el **Explorador de soluciones**, haga clic con el botón derecho en la solución `UtilityLibraries` y seleccione **Agregar** > **Nuevo proyecto**.

1. En el cuadro de diálogo **Agregar nuevo proyecto**, seleccione el nodo de C# y, después, **.NET Core**.

   > [!NOTE]
   > No es necesario escribir las pruebas unitarias en el mismo lenguaje que el de la biblioteca de clases.

1. Seleccione la plantilla **Proyecto de prueba unitaria (.NET Core)** en el panel derecho y escriba `StringLibraryTests` en el cuadro de texto **Nombre**, como se muestra en la figura siguiente:

   ![Cuadro de diálogo **Agregar nuevo proyecto** para el proyecto de prueba unitaria](./media/lut-start/add-unit-test-cs.png)

1. Seleccione **Aceptar** para crear el proyecto.

   > [!NOTE]
   > En este tutorial de introducción, Live Unit Testing se utiliza con el marco de pruebas de MSTest. También puede usar los marcos de pruebas de xUnit y NUnit.

1. El proyecto de prueba unitaria no puede acceder automáticamente a la biblioteca de clases que está probando. Para conceder acceso a la biblioteca de prueba, agregue una referencia al proyecto de biblioteca de clases. Para ello, haga clic con el botón derecho en el proyecto `StringLibraryTests` y seleccione **Agregar** > **Referencia**. En el cuadro de diálogo **Administrador de referencias**, asegúrese de que la pestaña **Solución** esté seleccionada y elija el proyecto `StringLibrary`, como se muestra en la figura siguiente.

   ![Cuadro de diálogo **Administrador de referencias**](./media/lut-start/add-reference.png)

1. Reemplace el código de prueba unitaria reutilizable que proporciona la plantilla por el código siguiente:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

1. Guarde el proyecto seleccionando el icono **Guardar** de la barra de herramientas.

1. Dado que el código de prueba unitaria incluye algunos caracteres no ASCII, Visual Studio muestra el siguiente cuadro de diálogo para advertir de que algunos caracteres se perderán si guardamos el archivo en el formato ASCII predeterminado. Elija el botón **Guardar con otra codificación**.

   ![Elegir una codificación de archivos](media/lut-start/ascii-encoding.png)

1. En la lista desplegable **Codificación** del cuadro de diálogo **Opciones avanzadas para guardar**, elija **Unicode (UTF-8 sin signatura) - Página de códigos 65001**, como se muestra en esta figura:

   ![Elegir la codificación UTF-8](media/lut-start/utf8-encoding.png)

1. Para compilar el proyecto de prueba unitaria, seleccione **Compilar** > **Recompilar solución** en el menú de nivel superior de Visual Studio.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. En el **Explorador de soluciones**, haga clic con el botón derecho en la solución `UtilityLibraries` y seleccione **Agregar** > **Nuevo proyecto**.

1. En el cuadro de diálogo **Agregar nuevo proyecto**, seleccione el nodo de Visual Basic y, después, **.NET Core**.

   > [!NOTE]
   > No es necesario escribir las pruebas unitarias en el mismo lenguaje que el de la biblioteca de clases.

1. Seleccione la plantilla **Proyecto de prueba unitaria (.NET Core)** en el panel derecho y escriba `StringLibraryTests` en el cuadro de texto **Nombre**, como se muestra en la figura siguiente:

   ![Cuadro de diálogo **Agregar nuevo proyecto** para la prueba unitaria](./media/lut-start/add-unit-test-vb.png)

1. Seleccione **Aceptar** para crear el proyecto.

   > [!NOTE]
   > En este tutorial de introducción, Live Unit Testing se utiliza con el marco de pruebas de MSTest. También puede usar los marcos de pruebas de xUnit y NUnit.

1. El proyecto de prueba unitaria no puede acceder automáticamente a la biblioteca de clases que está probando. Para conceder acceso a la biblioteca de prueba, agregue una referencia al proyecto de biblioteca de clases. Para ello, haga clic con el botón derecho en el proyecto `StringLibraryTests` y seleccione **Agregar** > **Referencia**. En el cuadro de diálogo **Administrador de referencias**, asegúrese de que la pestaña **Solución** esté seleccionada y elija el proyecto `StringLibrary`, como se muestra en la figura siguiente.

   ![Cuadro de diálogo **Administrador de referencias**](./media/lut-start/add-reference.png)

1. Reemplace el código de prueba unitaria reutilizable que proporciona la plantilla por el código siguiente:

   [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest1.vb)]

1. Guarde el proyecto seleccionando el icono **Guardar** de la barra de herramientas.

1. Dado que el código de prueba unitaria incluye algunos caracteres no ASCII, Visual Studio muestra el siguiente cuadro de diálogo para advertir de que algunos caracteres se perderán si guardamos el archivo en el formato ASCII predeterminado. Elija el botón **Guardar con otra codificación**.

   ![Elegir una codificación de archivos](media/lut-start/ascii-encoding.png)

1. En la lista desplegable **Codificación** del cuadro de diálogo **Opciones avanzadas para guardar**, elija **Unicode (UTF-8 sin signatura) - Página de códigos 65001**, como se muestra en esta figura:

   ![Elegir la codificación UTF-8](media/lut-start/utf8-encoding.png)

1. Para compilar el proyecto de prueba unitaria, seleccione **Compilar** > **Recompilar solución** en el menú de nivel superior de Visual Studio.

---

Ha creado una biblioteca de clases, así como algunas pruebas unitarias la misma. Ya ha completado los pasos preliminares necesarios para utilizar Live Unit Testing.

## <a name="enable-live-unit-testing"></a>Habilitar Live Unit Testing

Hasta ahora, aunque ha escrito las pruebas para la biblioteca de clases `StringLibrary`, no las ha ejecutado. Live Unit Testing las ejecuta automáticamente una vez que lo habilite. Para ello, haga lo siguiente:

1. Si quiere, seleccione la ventana de código que contiene el código para `StringLibrary`. Se trata de *Class1.cs* para un proyecto de C# o de *Class1.vb* para un proyecto de Visual Basic. Este paso le permite inspeccionar visualmente el resultado de las pruebas y el alcance de la cobertura de código una vez que habilite Live Unit Testing.

1. Seleccione **Prueba** > **Live Unit Testing** > **Iniciar** en el menú de nivel superior de Visual Studio.

1. Visual Studio inicia Live Unit Testing, que ejecuta automáticamente todas las pruebas.

Cuando acaba de ejecutar las pruebas, el **Explorador de pruebas** muestra los resultados globales y el resultado de las pruebas individuales. Además, la ventana de código muestra gráficamente la cobertura de código de prueba y el resultado de las pruebas. Como se muestra en la figura siguiente, las tres pruebas se han ejecutado correctamente. También muestra que nuestras pruebas han cubierto todas las rutas de acceso de código en el método `StartsWithUpper` y que esas pruebas se han ejecutado correctamente (lo que se indica mediante la marca de verificación de color verde, "✓"). Por último, muestra que ninguno de los otros métodos de `StringLibrary` tiene cobertura de código (lo que se indica mediante una línea azul, "➖").

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![Explorador de pruebas y ventana de código después de iniciar Live Unit Testing](media/lut-start/lut-results-cs.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
![Explorador de pruebas y ventana de código después de iniciar Live Unit Testing](media/lut-start/lut-results-vb.png)

---

También puede obtener información más detallada sobre la cobertura y los resultados de las pruebas seleccionando un icono de cobertura de código determinado en la ventana de código. Para examinar este detalle, haga lo siguiente:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Haga clic en la marca de verificación verde situada en la línea `if (String.IsNullOrWhiteSpace(s))` del método `StartsWithUpper`. Como se muestra en la figura siguiente, Live Unit Testing indica que las tres pruebas cubren esa línea de código y que todas se han ejecutado correctamente.

   ![Cobertura de código para la instrucción condicional "if"](media/lut-start/code-coverage-cs1.png)

1. Haga clic en la marca de verificación verde situada en la línea `return Char.IsUpper(s[0])` del método `StartsWithUpper`. Como se muestra en la figura siguiente, Live Unit Testing indica que solo dos pruebas cubren esa línea de código y que todas se han ejecutado correctamente.

   ![Cobertura de código para la instrucción Return](media/lut-start/code-coverage-cs2.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Haga clic en la marca de verificación verde situada en la línea `If (String.IsNullOrWhiteSpace(s)) Then` del método `StartsWithUpper`. Como se muestra en la figura siguiente, Live Unit Testing indica que las tres pruebas cubren esa línea de código y que todas se han ejecutado correctamente.

   ![Cobertura de código para la instrucción condicional "If"](media/lut-start/code-coverage-vb1.png)

1. Haga clic en la marca de verificación verde situada en la línea `Return Char.IsUpper(s(0))` del método `StartsWithUpper`. Como se muestra en la figura siguiente, Live Unit Testing indica que solo dos pruebas cubren esa línea de código y que todas se han ejecutado correctamente.

   ![Cobertura de código para la instrucción Return](media/lut-start/code-coverage-vb2.png)

---

El problema principal que Live Unit Testing identifica es la cobertura de código incompleta. Este tema se tratará en la sección siguiente.

## <a name="expand-test-coverage"></a>Expandir la cobertura de pruebas

En esta sección, podrá ampliar las pruebas unitarias al método `StartsWithLower`. Al hacerlo, Live Unit Testing continuará dinámicamente para probar el código.

Para ampliar la cobertura de código al método `StartsWithLower`, haga lo siguiente:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Agregue los métodos `TestStartsWithLower` y `TestDoesNotStartWithLower` al archivo de código fuente de prueba del proyecto:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Modifique el método `DirectCallWithNullOrEmpty` agregando el código siguiente inmediatamente después de la llamada al método [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse).

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Cuando se modifica el código fuente, Live Unit Testing ejecuta automáticamente las pruebas nuevas y modificadas. Como se muestra en la figura siguiente del **Explorador de pruebas**, todas las pruebas, incluidas las dos que se han agregado y la que se ha modificado, se han realizado correctamente.

   ![Explorador de pruebas después de expandir la cobertura de las pruebas.](media/lut-start/test-dynamic.png)

1. Cambie a la ventana que contiene el código fuente de la clase `StringLibrary`. Ahora, Live Unit Testing muestra que nuestra cobertura de código se ha extendido al método `StartsWithLower`.

    ![Cobertura de código para el método StartsWithLower](media/lut-start/lut-extended-cs.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Agregue los métodos `TestStartsWithLower` y `TestDoesNotStartWithLower` al archivo de código fuente de prueba del proyecto:

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#1)]

1. Modifique el método `DirectCallWithNullOrEmpty` agregando el código siguiente inmediatamente después de la llamada al método [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse).

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#2)]

1. Cuando se modifica el código fuente, Live Unit Testing ejecuta automáticamente las pruebas nuevas y modificadas. Como se muestra en la figura siguiente del **Explorador de pruebas**, todas las pruebas, incluidas las dos que se han agregado y la que se ha modificado, se han realizado correctamente.

   ![Explorador de pruebas después de expandir la cobertura de las pruebas.](media/lut-start/test-dynamic.png)

1. Cambie a la ventana que contiene el código fuente de la clase `StringLibrary`. Ahora, Live Unit Testing muestra que nuestra cobertura de código se ha extendido al método `StartsWithLower`.

    ![Cobertura de código para StartsWithLower](media/lut-start/lut-extended-vb.png)

---

En algunos casos, las pruebas correctas pueden mostrarse deshabilitadas en el **Explorador de pruebas**. Eso indica que una prueba se está ejecutando actualmente, o que la prueba no se ha vuelto a ejecutar porque no ha habido ningún cambio en el código que pudiera afectar a la prueba desde que se ejecutó por última vez.

Hasta ahora, todas nuestras pruebas se han realizado correctamente. En la siguiente sección, examinaremos cómo puede controlar los errores de pruebas.

## <a name="handle-a-test-failure"></a>Controlar errores de pruebas

En esta sección, explorará cómo puede usar Live Unit Testing para identificar, solucionar y abordar los errores de pruebas. Para ello, debe expandir la cobertura de las pruebas al método `HasEmbeddedSpaces`.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Agregue el método siguiente al archivo de prueba:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Cuando se ejecuta la prueba, Live Unit Testing indica que se ha producido un error en el método `TestHasEmbeddedSpaces`, tal como se muestra en la figura siguiente:

   ![El Explorador de pruebas informa de una prueba errónea.](media/lut-start/test-failure.png)

1. Seleccione la ventana en la que se muestra el código de biblioteca. Tenga en cuenta que Live Unit Testing ha ampliado la cobertura de código al método `HasEmbeddedSpaces`. También informa de los errores de pruebas agregando un símbolo "🞩" rojo a las líneas cubiertas por pruebas erróneas.

1. Mantenga el mouse sobre la línea que contiene la signatura del método `HasEmbeddedSpaces`. Live Unit Testing muestra información que indica que una prueba cubre el método, tal como se muestra en la figura siguiente:

   ![Información de Live Unit Testing sobre una prueba errónea.](media/lut-start/test-failure-info-cs.png)

1. Seleccione la prueba errónea **TestHasEmbeddedSpaces**. Tenga en cuenta que Live Unit Testing proporciona una serie de opciones, como ejecutar todas las pruebas, ejecutar las pruebas de selección, depurar todas las pruebas y depurar las pruebas seleccionadas, como se muestra en la figura siguiente:

   ![Opciones de Live Unit Testing para una prueba errónea.](media/lut-start/test-failure-options.png)

1. Seleccione **Depurar seleccionada** para depurar la prueba errónea.

1. Visual Studio ejecuta la prueba en modo de depuración. Nuestra prueba asigna cada cadena de una matriz a una variable denominada `phrase` y la pasa al método `HasEmbeddedSpaces`. La ejecución del programa se pone en pausa e invoca al depurador la primera vez que la expresión de aserción es `false`. En la figura siguiente se muestra el cuadro de diálogo de excepción que resulta del valor inesperado en la llamada al método [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue).

   ![Cuadro de diálogo de excepción de Live Unit Testing.](media/lut-start/exception-dialog-cs.png)

   Además, todas las herramientas de depuración que Visual Studio proporciona están disponibles para ayudarnos a solucionar problemas de nuestra prueba errónea, tal como se muestra en la figura siguiente:

   ![Herramientas de depuración de Visual Studio.](media/lut-start/debugging-tools-cs.png)

   Tenga en cuenta que, en la ventana **Automático**, el valor de la variable `phrase` es "Name\tDescription", que es el segundo elemento de la matriz. El método de prueba espera que `HasEmbeddedSpaces` devuelva `true` cuando se le pasa esta cadena; en su lugar, devuelve `false`. Evidentemente, no reconoce "\t", el carácter de tabulación, como un espacio insertado.

1. Seleccione **Depurar** > **Continuar**, presione **F5** o haga clic en el botón **Continuar** de la barra de herramientas para continuar ejecutando el programa de prueba. La prueba ha finalizado porque se ha producido una excepción no controlada.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Agregue el método siguiente al archivo de prueba:

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/unittest2.vb#3)]

1. Cuando se ejecuta la prueba, Live Unit Testing indica que se ha producido un error en el método `TestHasEmbeddedSpaces`, tal como se muestra en la figura siguiente:

   ![El Explorador de pruebas informa de una prueba errónea.](media/lut-start/test-failure.png)

1. Seleccione la ventana en la que se muestra el código de biblioteca. Tenga en cuenta que Live Unit Testing ha ampliado la cobertura de código al método `HasEmbeddedSpaces`. También informa de los errores de pruebas agregando un símbolo "🞩" rojo a las líneas cubiertas por pruebas erróneas.

1. Mantenga el mouse sobre la línea que contiene la signatura del método `HasEmbeddedSpaces`. Live Unit Testing muestra información que indica que una prueba cubre el método, tal como se muestra en la figura siguiente:

   ![Información de Live Unit Testing sobre una prueba errónea.](media/lut-start/test-failure-info-vb.png)

1. Seleccione la prueba errónea **TestHasEmbeddedSpaces**. Tenga en cuenta que Live Unit Testing proporciona una serie de opciones, como ejecutar todas las pruebas, ejecutar las pruebas de selección, depurar todas las pruebas y depurar las pruebas seleccionadas, como se muestra en la figura siguiente:

   ![Opciones de Live Unit Testing para una prueba errónea.](media/lut-start/test-failure-options.png)

1. Seleccione **Depurar seleccionada** para depurar la prueba errónea.

1. Visual Studio ejecuta la prueba en modo de depuración. Nuestra prueba asigna cada cadena de una matriz a una variable denominada `phrase` y la pasa al método `HasEmbeddedSpaces`. La ejecución del programa se pone en pausa e invoca al depurador la primera vez que la expresión de aserción es `false`. En la figura siguiente se muestra el cuadro de diálogo de excepción que resulta del valor inesperado en la llamada al método [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue).

   ![Cuadro de diálogo de excepción de Live Unit Testing.](media/lut-start/exception-dialog-vb.png)

   Además, todas las herramientas de depuración que Visual Studio proporciona están disponibles para ayudarnos a solucionar problemas de nuestra prueba errónea, tal como se muestra en la figura siguiente:

   ![Herramientas de depuración de Visual Studio.](media/lut-start/debugging-tools-vb.png)

   Tenga en cuenta que, en la ventana **Automático**, el valor de la variable `phrase` es "Name" + vbTab + "Description", que es el segundo elemento de la matriz. El método de prueba espera que `HasEmbeddedSpaces` devuelva `true` cuando se le pasa esta cadena; en su lugar, devuelve `false`. Evidentemente, no reconoce el carácter de tabulación como un espacio insertado.

1. Seleccione **Depurar** > **Continuar**, presione **F5** o haga clic en el botón **Continuar** de la barra de herramientas para continuar ejecutando el programa de prueba. La prueba ha finalizado porque se ha producido una excepción no controlada.

---

Esto proporciona información suficiente para una investigación preliminar del error. `TestHasEmbeddedSpaces`, la rutina de prueba, ha realizado una suposición incorrecta, o bien `HasEmbeddedSpaces` no reconoce correctamente todos los espacios insertados. Para diagnosticar y corregir el problema, comience por el método `StringLibrary.HasEmbeddedSpaces`:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Mire la comparación en el método `HasEmbeddedSpaces`. Considera que U+0020 es un espacio insertado. Sin embargo, el estándar Unicode incluye otros caracteres de espacio. Esto sugiere que el código de biblioteca ha probado incorrectamente la presencia de un carácter de espacio en blanco.

1. Reemplace la comparación de igualdad por una llamada al método <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName>:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing vuelve a ejecutar automáticamente el método de prueba errónea y actualiza los resultados en la ventana de código y en el **Explorador de pruebas**, como se muestra en la figura siguiente:

    ![Prueba HasEmbeddedSpaces correcta.](media/lut-start/test-success-cs.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Mire la comparación en el método `HasEmbeddedSpaces`. Considera que U+0020 es un espacio insertado. Sin embargo, el estándar Unicode incluye otros caracteres de espacio. Esto sugiere que el código de biblioteca ha probado incorrectamente la presencia de un carácter de espacio en blanco.

1. Reemplace la comparación de igualdad por una llamada al método <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName>:

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/class2.vb#1)]

1. Live Unit Testing vuelve a ejecutar automáticamente el método de prueba errónea y actualiza los resultados en la ventana de código y en el **Explorador de pruebas**, como se muestra en la figura siguiente:

    ![Prueba HasEmbeddedSpaces correcta.](media/lut-start/test-success-vb.png)

---

## <a name="see-also"></a>Vea también
- [Live Unit Testing en Visual Studio](live-unit-testing.md)
- [Preguntas más frecuentes sobre Live Unit Testing](live-unit-testing-faq.md)
