---
title: Live Unit Testing en Visual Studio
ms.date: 2017-03-07
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 4cc9ec25ab6bc69359649764074a3e908c06c4ae
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089560"
---
# <a name="live-unit-testing-with-visual-studio-2017"></a>Live Unit Testing con Visual Studio 2017

Mientras desarrolla una aplicación, Live Unit Testing ejecuta automáticamente y en segundo plano las pruebas unitarias afectadas y presenta los resultados y la cobertura de código en vivo en el IDE de Visual Studio en tiempo real. Cuando modifica el código, Live Unit Testing proporciona comentarios sobre cómo los cambios afectaron a las pruebas existentes y si el código nuevo que ha agregado está cubierto por una o varias pruebas existentes. Esto le recordará que debe escribir pruebas unitarias cuando realiza correcciones de errores o agrega nuevas características.

> [!NOTE]
> Live Unit Testing está disponible para proyectos de C# y Visual Basic que tienen como destino .NET Core o .NET Framework en la edición Enterprise de Visual Studio 2017.

Cuando se usa Live Unit Testing para las pruebas, Live Unit Testing conserva los datos sobre el estado de las pruebas. Su capacidad de usar datos persistentes permite que Live Unit Testing ofrezca un rendimiento superior mientras se ejecutan las pruebas de forma dinámica en respuesta a los cambios en el código.

## <a name="supported-test-frameworks"></a>Marcos de prueba admitidos
Live Unit Testing funciona con los tres marcos de pruebas unitarias conocidos enumerados en la tabla siguiente. La versión mínima admitida de sus adaptadores y marcos también aparece en la tabla. Los marcos de pruebas unitarias están disponibles en NuGet.org.

<table>
<tr>
   <th>Marco de prueba</th>
   <th>Versión mínima del adaptador de Visual Studio</th>
   <th>Versión mínima del marco</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.runner.visualstudio version 2.2.0-beta3-build1187</td>
   <td>xunit 1.9.2</td>
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter version 3.5.1</td>
   <td>NUnit version 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.4-preview</td>
   <td>MSTest.TestFramework 1.0.5-preview</td>
</tr>
</table>

Si tiene proyectos de prueba basados en versiones anteriores de MSTest que hacen referencia a `Microsoft.VisualStudio.QualityTools.UnitTestFramework` y no quiere utilizar los paquetes de MSTest NuGet más recientes, actualice a la versión 15.4 de Visual Studio 2017.

En algunos casos, es posible que tenga que restaurar explícitamente los paquetes NuGet a los que los proyectos de la solución hacen referencia para que Live Unit Testing funcione. Puede hacerlo compilando explícitamente la solución (seleccione **Compilar**, **Recompilar solución** en el menú de Visual Studio de nivel superior) o restaurando los paquetes en la solución (haga doble clic en la solución y seleccione **Restaurar paquetes de NuGet**) antes de habilitar Live Unit Testing.

## <a name="configuring-live-unit-testing"></a>Configuración de Live Unit Testing

Puede configurar Live Unit Testing seleccionando **Herramientas**, **Opciones** en el menú de Visual Studio de nivel superior y luego seleccionando **Live Unit Testing** en el panel izquierdo del cuadro de diálogo **Opciones**. La figura siguiente muestra las opciones de configuración Live Unit Testing disponibles en el cuadro de diálogo.

  ![Imagen](./media/lut-options.png)

A continuación se indican las opciones que se pueden configurar:

- Si Live Unit Testing se pausa cuando se compila y depura una solución

- Si Live Unit Testing se pausa cuando la energía de la batería del sistema cae por debajo de un umbral especificado.
- Si Live Unit Testing se ejecuta automáticamente cuando se abre una solución.
- El directorio en el que almacenar los datos persistentes.
   El botón **Delete Persisted Data** (Eliminar datos persistentes) permite eliminar todos los datos persistentes. Esto resulta útil cuando Live Unit Testing tiene un comportamiento impredecible o inesperado, lo que sugiere que se dañaron los datos persistentes.
- El intervalo después del cual un caso de prueba expira; el valor predeterminado es 30 segundos.
- El número máximo de procesos de prueba que Live Unit Testing crea.
- La cantidad máxima de memoria que pueden consumir los procesos de Live Unit Testing.
- El nivel de la información que se escribe en la ventana **Salida** de Live Unit Testing.
   Las opciones incluyen no registrar nada (**Ninguno**), solo los mensajes de error (**Error**), mensajes de error e informativos (**Información**, el valor predeterminado) o todos los detalles (**Detallado**).

También puede mostrar la salida detallada en la ventana **Salida** de Live Unit Testing asignando un valor de "1" a una variable de entorno de usuario denominada `VS_UTE_DIAGNOSTICS` y reiniciando Visual Studio.

Para capturar mensajes de registro de MSBuild detallados desde Live Unit Testing en un archivo, establezca la variable de entorno de usuario `LiveUnitTesting_BuildLog` en el nombre del archivo que va a contener el registro.

Cuando Live Unit Testing se habilita (consulte la sección siguiente, [Inicio, pausa y detención de Live Unit Testing](#starting-pausing-and-stopping-live-unit-testing)), también puede abrir el cuadro de diálogo **Opciones** si selecciona **Prueba**, **Live Unit Testing**, **Opciones**.

## <a name="starting-pausing-and-stopping-live-unit-testing"></a>Inicio, pausa y detención de Live Unit Testing

Puede habilitar Live Unit Testing seleccionando **Prueba**, **Live Unit Testing**, **Iniciar** en el menú de Visual Studio de nivel superior. Cuando Live Unit Testing se habilita, las opciones disponibles en el menú **Live Unit Testing** pasan de un elemento único, **Iniciar**, a **Pausar**, **Detener** y **Reiniciar**.

> [!NOTE]
> Si inicia Live Unit Testing en una solución que no incluye ningún proyecto de prueba unitaria, las opciones **Pausar**, **Detener** y **Reiniciar** aparecen en el menú **Live Unit Testing**, pero Live Unit Testing no se inicia. En la ventana **Salida** se muestra un mensaje que comienza por "No supported test adapters are referenced by this solution..." ("Esta solución no hace referencia a ningún adaptador de prueba compatible...").

Live Unit Testing puede pausarse temporalmente o detenerse por completo en cualquier momento. Puede hacerlo, por ejemplo, si está en curso una refactorización y sabe que las pruebas se interrumpirán durante un tiempo. Las tres opciones de menú son:

- **Pausar**, que suspende temporalmente Live Unit Testing.

    Cuando Live Unit Testing se pausa, la visualización de la cobertura no aparece en el editor, pero se conservan todos los datos recopilados. Para reanudar Live Unit Testing, seleccione **Continuar** en el menú Live Unit Testing. Live Unit Testing hace el trabajo necesario para ponerse al día con todas las ediciones realizadas mientras estaba en pausa y actualiza los glifos apropiadamente.

- **Detener**, para parar completamente Live Unit Testing. Live Unit Testing descarta todos los datos que ha recopilado.

- **Reiniciar**, que detiene Live Unit Testing, elimina los datos persistentes y reinicia Live Unit Testing.

- **Opciones**, que abre el cuadro de diálogo **Opciones** que se describe en la sección [Configuración de Live Unit Testing](#configuring-live-unit-testing).

##  <a name="viewing-coverage-visualization-in-the-editor-as-you-type"></a>Presentación de la visualización de la cobertura en el editor a medida que escribe

Cuando ya se ha habilitado, Live Unit Testing actualiza cada línea de código en el editor de Visual Studio para mostrar si el código que está escribiendo está cubierto por las pruebas unitarias y si las pruebas que cubre se superan.  La siguiente figura muestra líneas de código tanto con pruebas que se superan como con pruebas con error, así como líneas de código que no están cubiertas por las pruebas. Las líneas representadas con un símbolo "✓" de color verde solo están cubiertas por pruebas superadas, las líneas representadas con una "x" de color rojo están cubiertas por una o varias pruebas con error y las líneas representadas con un símbolo "" de color azul no están cubiertas por ninguna prueba.

  ![Imagen](./media/lut-codewindow.png)

La visualización de cobertura de Live Unit Testing se actualiza inmediatamente a medida que modifica el editor de código. Al procesar las ediciones, la visualización cambia para indicar que los datos no están actualizados agregando una imagen de cronómetro redondo debajo de los símbolos de superación, error y sin cubrir, como se muestra en la figura siguiente.

  ![Imagen](./media/lut-codeupdating.png)

## <a name="getting-information-on-successful-or-failed-tests"></a>Obtención de información sobre las pruebas superadas o con error

Al mantener el puntero sobre el símbolo de operación correcta o con error en la ventana de código, puede ver cuántas pruebas alcanzan esa línea. Si hace clic en el símbolo, puede ver el estado de las pruebas individuales, como se muestra en la figura siguiente:

  ![Imagen](./media/lut-failedinfo.png)

Además de proporcionar los nombres y el resultado de las pruebas, la información sobre herramientas permite volver a ejecutar el conjunto de pruebas, así como ejecutar el conjunto de pruebas mediante el depurador. Si selecciona una o más de las pruebas en la información sobre herramientas, también puede ejecutar o depurar solo esas pruebas. Esto le permite depurar las pruebas sin tener que salir de la ventana de código. Durante la depuración, además de observar cualquier punto de interrupción que ya pueda estar establecido, la ejecución del programa se pausa cuando el depurador ejecuta un método [`Assert`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert) que devuelve un resultado inesperado.

Cuando mantiene el puntero sobre una prueba con error en la información sobre herramientas, se expande para proporcionar información adicional sobre el error, como se muestra en la imagen siguiente. Si hace doble clic en la prueba con error en la información sobre herramientas, puede navegar directamente a ella.

  ![Imagen](./media/lut-failedmsg.png)

Cuando se navega a la prueba con error, Live Unit Testing también indica de manera visual en la signatura de método las pruebas que se aprobaron (lo que se indica con una probeta a medio llenar junto con un símbolo "✓" de color verde), las que no se aprobaron (una probeta a medio llenar junto con un símbolo "🞩" de color rojo) o que no participaron en Live Unit Testing (una probeta a medio llenar junto con un símbolo "" de color azul). Los métodos que no son de prueba no se muestran con ningún símbolo. En la figura siguiente se muestran los cuatro tipos de métodos.

  ![Imagen](media/lut-testsource.png)

## <a name="diagnosing-and-correcting-test-failures"></a>Diagnóstico y corrección de pruebas con error

A partir de la prueba con error, puede depurar fácilmente el código del producto, realizar ediciones y continuar desarrollando la aplicación. Dado que Live Unit Testing se ejecuta en segundo plano, no es necesario detener y reiniciar Live Unit Testing durante el ciclo de depuración, edición y continuación.

Por ejemplo, el error de la prueba que se muestra en la figura anterior fue causado por una asunción incorrecta en el método de prueba de que caracteres no alfabéticos devolverían `true` cuando se pasaran al método <xref:System.Char.IsLower%2A?displayProperty=fullName>. Una vez corregido el método de prueba, todas las pruebas se superan. Mientras estamos haciendo esto, no tenemos que pausar o detener Live Unit Testing.

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing y el Explorador de pruebas

Normalmente, el **Explorador de pruebas** proporciona la interfaz que permite ejecutar, depurar y analizar los resultados de las pruebas. Live Unit Testing se integra con el **Explorador de pruebas**. Cuando la característica Live Unit Testing no está habilitada o está detenida, el **Explorador de pruebas** muestra el estado de las pruebas unitarias la última vez que se ejecutó una prueba. Los cambios de código fuente requieren que se vuelvan a ejecutar las pruebas. En cambio, cuando Live Unit Testing se ha habilitado, el estado de las pruebas unitarias en el **Explorador de pruebas** se actualiza inmediatamente. Ya no necesitará ejecutar las pruebas unitarias de forma explícita.

> [!NOTE]
> Puede abrir el **Explorador de pruebas** seleccionando **Prueba**, **Windows**, **Explorador de pruebas** en el menú de Visual Studio de nivel superior.

Puede observar en la ventana del **Explorador de pruebas** que algunas de las pruebas aparecen atenuadas. Por ejemplo, cuando se habilita Live Unit Testing después de abrir un proyecto guardado anteriormente, la ventana del **Explorador de pruebas** atenuó todas las pruebas, excepto la prueba con error, tal como se muestra en la figura siguiente. En este caso, Live Unit Testing volvió a ejecutar la prueba con error, pero no las pruebas que se realizaron correctamente, porque los datos persistentes de Live Unit Testing indican que no hubo cambios desde la última vez que las pruebas se ejecutaron correctamente.

  ![Imagen](media/lut-test-explorer.png)

Para volver a ejecutar cualquier prueba que aparezca atenuada, seleccione las opciones **Ejecutar todo** o **Ejecutar** en el menú del **Explorador de pruebas**, o bien seleccione una o más pruebas en el menú del **Explorador de pruebas**, haga clic con el botón derecho y seleccione **Ejecutar pruebas seleccionadas** o **Depurar pruebas seleccionadas** en el menú emergente. Cuando las pruebas se ejecutan, se propagan a la parte superior.

Hay algunas diferencias entre la ejecución y actualización automáticas de resultados de pruebas en Live Unit Testing y la ejecución explícita de pruebas desde el **Explorador de pruebas**. Estas diferencias incluyen:

- La ejecución o depuración de pruebas desde la ventana Explorador de pruebas ejecuta binarios normales, mientras que Live Unit Testing ejecuta binarios instrumentados.
- Live Unit Testing no crea un nuevo dominio de aplicación para ejecutar las pruebas, sino que ejecuta pruebas del dominio predeterminado. Las pruebas que se ejecutan desde la ventana **Explorador de pruebas** crean un nuevo dominio de aplicación.
- Live Unit Testing ejecuta pruebas secuencialmente en cada ensamblado de prueba. Si ejecuta varias pruebas desde la ventana **Explorador de pruebas** y selecciona el botón **Ejecutar pruebas en paralelo**, las pruebas se ejecutan en paralelo.

## <a name="live-unit-testing-and-large-solutions"></a>Live Unit Testing y soluciones de gran tamaño

Si la solución tiene diez proyectos o más, cuando se inicia Live Unit Testing y no hay datos persistentes o cuando se selecciona la opción **Prueba**, **Live Unit Testing**, **Restablecer limpieza** en el menú de Visual Studio de nivel superior, Visual Studio muestra el siguiente cuadro de diálogo para advertirle de que la ejecución dinámica de un gran número de pruebas en proyectos de gran tamaño puede afectar gravemente al rendimiento. Si hace clic en **Aceptar**, Live Unit Testing ejecuta todas las pruebas de la solución. Si selecciona **Cancelar**, puede seleccionar las pruebas que desea ejecutar. Para información sobre cómo hacerlo, vea la sección siguiente, [Inclusión y exclusión de proyectos de prueba y métodos de prueba](#including-and-excluding-test-projects-and-test-methods).

 ![Cuadro de diálogo de Live Unit Testing para proyectos de gran tamaño](media/lut-large-project.png)

## <a name="including-and-excluding-test-projects-and-test-methods"></a>Inclusión y exclusión de proyectos de prueba y métodos de prueba

Para soluciones con muchos proyectos de prueba, puede controlar qué proyectos y qué métodos individuales de un proyecto participan en Live Unit Testing. Por ejemplo, si tiene una solución con cientos de proyectos de prueba, puede seleccionar un conjunto de proyectos de prueba de destino para participar en Live Unit Testing. Existen varias maneras de llevar esto a cabo, en función de si desea excluir todas las pruebas en el proyecto o la solución, si desea incluir o excluir la mayoría de las pruebas o si desea excluir pruebas de forma individual. Live Unit Testing guarda el estado de inclusión o exclusión como una configuración de usuario y lo recuerda cuando una solución se cierra y se vuelve a abrir.

**Exclusión de todas las pruebas en un proyecto o solución**

Para seleccionar proyectos individuales en pruebas unitarias, haga lo siguiente después de iniciar Live Unit Testing:

1.  Haga clic con el botón derecho en la solución en el Explorador de soluciones y elija **Live Tests** (Pruebas en vivo), **Excluir** para excluir toda la solución.
1.  Haga clic con el botón derecho en cada proyecto de prueba que desearía incluir en las pruebas y elija **Live Tests** (Pruebas en vivo), **Incluir**.

**Exclusión de pruebas individuales de la ventana del editor de código**

Puede usar la ventana del editor de código para incluir o excluir métodos de prueba individuales. Haga clic con el botón derecho en la firma del método de prueba en la ventana del editor de código y seleccione **Pruebas en vivo**, **Incluir [el método seleccionado]**, **Pruebas en vivo**, **Excluir [el método seleccionado]** o **Pruebas en vivo**, **Excluir todo excepto [el método seleccionado]**, donde "el método seleccionado" es el nombre del método que seleccionó en la ventana de código.

**Exclusión de pruebas mediante programación**

Puede aplicar el atributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> para, mediante programación, excluir los métodos, las clases o las estructuras y evitar que informen de su cobertura en Live Unit Testing.

También puede usar los atributos siguientes para excluir los métodos individuales de Live Unit Testing:

- Para xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Para NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- Para MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Vea también

[Herramientas de pruebas de código](https://visualstudio.microsoft.com/vs/testing-tools/)
[Blog Live Unit Testing](https://go.microsoft.com/fwlink/?linkid=842514)
[Preguntas más frecuentes de Live Unit Testing](live-unit-testing-faq.md)
[Vídeo de Channel 9: Live Unit Testing en Visual Studio 2017](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)

