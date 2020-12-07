---
title: Live Unit Testing
description: Obtenga información sobre el uso de Live Unit Testing durante el desarrollo de aplicaciones, incluidos los marcos admitidos y cómo configurar esta característica.
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: 82ed41514109887d32f38faf4f965c923864ae32
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329359"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Configuración y uso de Live Unit Testing

Mientras desarrolla una aplicación, Live Unit Testing ejecuta automáticamente y en segundo plano las pruebas unitarias afectadas y presenta los resultados y la cobertura de código en tiempo real. Cuando modifica el código, Live Unit Testing proporciona comentarios sobre cómo los cambios afectaron a las pruebas existentes y si el código nuevo que ha agregado está cubierto por una o varias pruebas existentes. Esto le recuerda que debe escribir pruebas unitarias cuando realiza correcciones de errores o agrega nuevas características.

> [!NOTE]
> Live Unit Testing está disponible para proyectos de C# y Visual Basic que tienen como destino .NET Core o .NET Framework en la edición Enterprise de Visual Studio.

Cuando se usa Live Unit Testing para las pruebas, conserva los datos sobre el estado de las pruebas. El uso de datos persistentes permite que Live Unit Testing ofrezca un rendimiento superior mientras se ejecutan las pruebas de forma dinámica en respuesta a los cambios en el código.

## <a name="supported-test-frameworks"></a>Marcos de prueba admitidos

Live Unit Testing funciona con los tres marcos de pruebas unitarias conocidos enumerados en la tabla siguiente. También se muestra la versión mínima admitida de sus adaptadores y marcos. Los marcos de pruebas unitarias están disponibles en NuGet.org.

|Marco de prueba  |Versión mínima del adaptador de Visual Studio  |Versión mínima del marco  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio version 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter version 3.5.1 |NUnit version 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Si tiene proyectos de prueba basados en versiones anteriores de MSTest que hacen referencia a Microsoft.VisualStudio.QualityTools.UnitTestFramework y no quiere migrar a los paquetes NuGet de MSTest más recientes, actualice a Visual Studio 2019 o Visual Studio 2017.

En algunos casos, es posible que tenga que restaurar explícitamente los paquetes NuGet a los que un proyecto hace referencia para que Live Unit Testing funcione. Puede hacerlo compilando explícitamente la solución (seleccione **Compilar** > **Recompilar solución** en el menú de Visual Studio de nivel superior) o restaurando los paquetes en la solución (haga clic con el botón derecho en la solución y seleccione **Restaurar paquetes NuGet**).

## <a name="configure"></a>Configurar

Configure Live Unit Testing seleccionando **Herramientas** > **Opciones** en la barra de menús de Visual Studio de nivel superior y luego seleccionando **Live Unit Testing** en el panel izquierdo del cuadro de diálogo **Opciones**.

> [!TIP]
> Una vez que Live Unit Testing se habilita (vea la sección siguiente, [Iniciar, pausar y detener Live Unit Testing](#start-pause-and-stop)), también puede abrir el cuadro de diálogo **Opciones** si selecciona **Prueba** > **Live Unit Testing** > **Opciones**.

La imagen siguiente muestra las opciones de configuración Live Unit Testing disponibles en el cuadro de diálogo:

![Opciones de configuración de Live Unit Testing](./media/lut-options.png)

A continuación se indican las opciones que se pueden configurar:

- Si Live Unit Testing se pausa cuando se compila y depura una solución.

- Si Live Unit Testing se pausa cuando la energía de la batería del sistema cae por debajo de un umbral especificado.

- Si Live Unit Testing se ejecuta automáticamente cuando se abre una solución.

- Si quiere habilitar el símbolo de depuración y la generación de comentarios de documentación XML.

- El directorio en el que almacenar los datos persistentes.

- La capacidad de eliminar todos los datos persistentes. Esto resulta útil cuando Live Unit Testing tiene un comportamiento impredecible o inesperado, lo que sugiere que se dañaron los datos persistentes.

- El intervalo después del cual un caso de prueba expira. El valor predeterminado es 30 segundos.

- El número máximo de procesos de prueba que Live Unit Testing crea.

- La cantidad máxima de memoria que pueden consumir los procesos de Live Unit Testing.

- El nivel de la información que se escribe en la ventana **Salida** de Live Unit Testing.

   Las opciones incluyen no registrar nada (**Ninguno**), solo los mensajes de error (**Error**), mensajes de error e informativos (**Información**, el valor predeterminado) o todos los detalles (**Detallado**).

   También puede mostrar la salida detallada en la ventana **Salida** de Live Unit Testing asignando un valor de "1" a una variable de entorno de usuario denominada `VS_UTE_DIAGNOSTICS` y, después, reiniciando Visual Studio.

   Para capturar mensajes de registro de MSBuild detallados desde Live Unit Testing en un archivo, establezca la variable de entorno de usuario `LiveUnitTesting_BuildLog` en el nombre del archivo que va a contener el registro.

## <a name="start-pause-and-stop"></a>Iniciar, pausar y detener

Para habilitar Live Unit Testing, seleccione **Prueba** > **Live Unit Testing** > **Iniciar** en el menú de Visual Studio de nivel superior. Cuando Live Unit Testing se habilita, las opciones disponibles en el menú **Live Unit Testing** pasan de un elemento único (**Iniciar**) a **Pausar** y **Detener**:

- **Pausar** suspende temporalmente Live Unit Testing.

  Cuando Live Unit Testing se pausa, la visualización de la cobertura no aparece en el editor, pero se conservan todos los datos recopilados. Para reanudar Live Unit Testing, seleccione **Continuar** en el menú Live Unit Testing. Live Unit Testing hace el trabajo necesario para ponerse al día con todas las ediciones realizadas mientras estaba en pausa y actualiza los glifos apropiadamente.

- **Detener** para completamente Live Unit Testing. Live Unit Testing descarta todos los datos que ha recopilado.

> [!NOTE]
> Si inicia Live Unit Testing en una solución que no incluye ningún proyecto de prueba unitaria, las opciones **Pausar** y **Detener** aparecen en el menú **Live Unit Testing**, pero Live Unit Testing no se inicia. En la ventana **Salida** se muestra un mensaje que comienza por "No supported test adapters are referenced by this solution..." ("Esta solución no hace referencia a ningún adaptador de prueba compatible...").

Live Unit Testing puede pausarse temporalmente o detenerse por completo en cualquier momento. Puede hacerlo, por ejemplo, si está en curso una refactorización y sabe que las pruebas se interrumpirán durante un tiempo.

## <a name="view-coverage-visualization"></a>Ver visualización de cobertura

Cuando ya se ha habilitado, Live Unit Testing actualiza cada línea de código en el editor de Visual Studio para mostrar si el código que está escribiendo está cubierto por las pruebas unitarias y si las pruebas que cubre se superan. La siguiente imagen muestra líneas de código tanto con pruebas que se superan como con pruebas con error, así como líneas de código que no están cubiertas por las pruebas. Las líneas representadas con un símbolo "✓" de color verde solo están cubiertas por pruebas superadas, las líneas representadas con una "x" de color rojo están cubiertas por una o varias pruebas con error y las líneas representadas con un símbolo "➖" de color azul no están cubiertas por ninguna prueba.

![Cobertura de código en Visual Studio](./media/lut-codewindow.png)

La visualización de cobertura de Live Unit Testing se actualiza inmediatamente cuando modifica el editor de código. Al procesar las ediciones, la visualización cambia para indicar que los datos no están actualizados agregando una imagen de cronómetro redondo debajo de los símbolos de superación, error y sin cubrir, como se muestra en la imagen siguiente.

![Cobertura de código en Visual Studio con icono de temporizador](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Obtener información acerca del estado de una prueba

Al mantener el puntero sobre el símbolo de operación correcta o con error en la ventana de código, puede ver cuántas pruebas alcanzan esa línea. Para ver el estado de las pruebas individuales, seleccione el símbolo:

![Estado de la prueba de un símbolo en Visual Studio](./media/lut-failedinfo.png)

Además de proporcionar los nombres y el resultado de las pruebas, la información sobre herramientas permite volver a ejecutar o depurar el conjunto de pruebas. Si selecciona una o más de las pruebas en la información sobre herramientas, también puede ejecutar o depurar solo esas pruebas. Esto le permite depurar las pruebas sin tener que salir de la ventana de código. Durante la depuración, además de observar cualquier punto de interrupción que ya pueda estar establecido, la ejecución del programa se pausa cuando el depurador ejecuta un método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> que devuelve un resultado inesperado.

Cuando mantiene el puntero sobre una prueba con error en la información sobre herramientas, se expande para proporcionar información adicional sobre el error, como se muestra en la imagen siguiente. Para navegar directamente a una prueba con errores, haga doble clic en ella en la información sobre herramientas.

![Información sobre herramientas de prueba con errores en Visual Studio](./media/lut-failedmsg.png)

Cuando navega a la prueba con errores, Live Unit Testing indica visualmente en la firma del método las pruebas que:

- se han superado (indicado por un vaso de precipitado a la mitad junto con una marca "✓" verde)
- han dado error (un vaso de precipitado a la mita con una marca "🞩" roja)
- no están implicadas en Live Unit Testing (un vaso de precipitado a la mitad con una marca "➖" azul)

Los métodos que no son de prueba no se muestran con ningún símbolo. En la imagen siguiente se muestran los cuatro tipos de métodos.

![Métodos de prueba en Visual Studio con el símbolo de superación o error](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnosticar y corregir errores en las pruebas

A partir de la prueba con error, puede depurar fácilmente el código del producto, realizar ediciones y continuar desarrollando la aplicación. Dado que Live Unit Testing se ejecuta en segundo plano, no es necesario detener y reiniciar Live Unit Testing durante el ciclo de depuración, edición y continuación.

Por ejemplo, el error de la prueba que se muestra en la imagen anterior fue causado por una asunción incorrecta en el método de prueba de que caracteres no alfabéticos devolverían `true` cuando se pasaran al método <xref:System.Char.IsLower%2A?displayProperty=fullName>. Después de corregir el método de prueba, se deberían superar todas las pruebas. No tiene que pausar ni detener Live Unit Testing.

::: moniker range="vs-2017"
## <a name="test-explorer"></a>Explorador de pruebas

El **Explorador de pruebas** proporciona una interfaz que permite ejecuta y depurar pruebas y analizar sus resultados. Live Unit Testing se integra con el **Explorador de pruebas**. Cuando la característica Live Unit Testing no está habilitada o está detenida, el **Explorador de pruebas** muestra el estado de las pruebas unitarias la última vez que se ejecutó una prueba. Los cambios de código fuente requieren que se vuelvan a ejecutar las pruebas. En cambio, cuando Live Unit Testing se ha habilitado, el estado de las pruebas unitarias en el **Explorador de pruebas** se actualiza inmediatamente. No es necesario que ejecute de forma explícita las pruebas unitarias.

> [!TIP]
> Para abrir **Live Unit Testing**, seleccione **Prueba** > **Windows** > **Explorador de pruebas** en el menú de Visual Studio de nivel superior.

Puede observar en la ventana del **Explorador de pruebas** que algunas de las pruebas aparecen atenuadas. Por ejemplo, cuando se habilita Live Unit Testing después de abrir un proyecto guardado anteriormente, la ventana del **Explorador de pruebas** atenuó todas las pruebas, excepto la prueba con error, tal como se muestra en la imagen siguiente. En este caso, Live Unit Testing ha vuelto a ejecutar la prueba con errores, pero no ha vuelto a ejecutar las pruebas correctas. Esto se debe a que los datos persistentes de Live Unit Testing indican que no hubo cambios, ya que las pruebas se ejecutaron correctamente la última vez.

![Prueba con errores en el Explorador de pruebas](media/lut-test-explorer.png)

Puede volver a ejecutar las pruebas que aparecen atenuadas seleccionando las opciones **Ejecutar todo** o **Ejecutar** en el **Explorador de pruebas**. O bien, seleccione una o varias pruebas en el menú **Explorador de pruebas**, haga clic en ellas con el botón secundario y luego seleccione **Ejecutar pruebas seleccionadas** o **Depurar pruebas seleccionadas** en el menú emergente. Cuando las pruebas se ejecutan, se propagan a la parte superior.

Hay algunas diferencias entre la ejecución y actualización automáticas de resultados de pruebas en Live Unit Testing y la ejecución explícita de pruebas desde el **Explorador de pruebas**. Estas diferencias incluyen:

- La ejecución o depuración de pruebas desde la ventana Explorador de pruebas ejecuta binarios normales, mientras que Live Unit Testing ejecuta binarios instrumentados.
- Live Unit Testing no crea un nuevo dominio de aplicación para ejecutar las pruebas, sino que ejecuta pruebas del dominio predeterminado. Las pruebas que se ejecutan desde la ventana **Explorador de pruebas** crean un nuevo dominio de aplicación.
- Live Unit Testing ejecuta pruebas secuencialmente en cada ensamblado de prueba. En la ventana **Explorador de pruebas**, puede optar por ejecutar varias pruebas en paralelo.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="live-unit-testing-window"></a>Ventana de Live Unit Testing

**Live Unit Testing**, similar al **Explorador de pruebas**, proporciona una interfaz que permite ejecutar y depurar pruebas, y analizar sus resultados. Cuando se habilita Live Unit Testing, el estado de las pruebas unitarias en el **Explorador de pruebas** se actualiza inmediatamente. No es necesario que ejecute de forma explícita las pruebas unitarias. Cuando Live Unit Testing no está habilitado o está detenido, en **Live Unit Testing** se muestra el estado de las pruebas unitarias la última vez que se ha ejecutado una prueba. Después de reiniciar Live Unit Testing, se necesita un cambio del código fuente para volver a ejecutar las pruebas.

> [!TIP]
> Para iniciar Live Unit Testing, seleccione **Prueba** > **Live Unit Testing** > **Iniciar** en el menú de Visual Studio de nivel superior. También puede abrir la ventana de **Live Unit Testing** mediante **Vista** > **Otras ventanas** > **Ventana de Live Unit Testing**.

Es posible que en la ventana de **Live Unit Testing** vea que algunas de las pruebas aparecen atenuadas. Por ejemplo, al detener y reiniciar Live Unit Testing, en la ventana de **Live Unit Testing** se atenúan todas las pruebas, como se muestra en la imagen siguiente. Los resultados de las pruebas atenuadas indican que la prueba no formaba parte de la última ejecución de pruebas unitarias dinámicas. Las pruebas solo se ejecutan cuando se detecta un cambio en la prueba o en sus dependencias. Si no hay ningún cambio, evita que la prueba se ejecute de manera innecesaria. En este caso, el resultado de la prueba atenuada sigue siendo "actualizado", aunque no formaba parte de la última ejecución.

![Pruebas atenuadas en el Explorador de pruebas](media/vs-2019/lut-test-explorer.png)

Puede volver a ejecutar las pruebas que aparecen atenuadas si realiza un cambio en el código.

Hay algunas diferencias entre la ejecución y actualización automáticas de resultados de pruebas en Live Unit Testing y la ejecución explícita de pruebas desde el **Explorador de pruebas**. Estas diferencias incluyen:

- La ejecución o depuración de pruebas desde la ventana Explorador de pruebas ejecuta binarios normales, mientras que Live Unit Testing ejecuta binarios instrumentados.
- Live Unit Testing no crea un nuevo dominio de aplicación para ejecutar las pruebas, sino que ejecuta pruebas del dominio predeterminado. Las pruebas que se ejecutan desde la ventana **Explorador de pruebas** crean un nuevo dominio de aplicación.
- Live Unit Testing ejecuta pruebas secuencialmente en cada ensamblado de prueba. En la ventana **Explorador de pruebas**, puede optar por ejecutar varias pruebas en paralelo.
::: moniker-end

## <a name="large-solutions"></a>Soluciones grandes

Si la solución tiene 10 o más proyectos, Visual Studio muestra el siguiente cuadro de diálogo cuando:

- Inicia Live Unit Testing y no hay datos persistentes.
- Selecciona **Herramientas** > **Opciones** > **Live Unit Testing** > **Delete Persisted Data** (Eliminar datos persistentes).

![Cuadro de diálogo de Live Unit Testing para proyectos de gran tamaño](media/lut-large-project.png)

El cuadro de diálogo le advierte de que la ejecución dinámica de un gran número de pruebas en proyectos grandes puede afectar gravemente al rendimiento. Si hace clic en **Aceptar**, Live Unit Testing ejecuta todas las pruebas de la solución. Si selecciona **Cancelar**, puede seleccionar las pruebas que desea ejecutar. En la siguiente sección se explica cómo hacerlo.

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Incluir y excluir proyectos de prueba y métodos de prueba

Para soluciones con muchos proyectos de prueba, puede controlar qué proyectos y qué métodos individuales de un proyecto participan en Live Unit Testing. Por ejemplo, si tiene una solución con cientos de proyectos de prueba, puede seleccionar un conjunto de proyectos de prueba de destino para participar en Live Unit Testing. Existen varias maneras de llevar esto a cabo, en función de si desea excluir todas las pruebas en el proyecto o la solución, incluir o excluir la mayoría de las pruebas o excluir pruebas de forma individual. Live Unit Testing guarda el estado de inclusión o exclusión como una configuración de usuario y lo recuerda cuando una solución se cierra y se vuelve a abrir.

### <a name="exclude-all-tests-in-a-project-or-solution"></a>Exclusión de todas las pruebas en un proyecto o solución

Para seleccionar proyectos individuales en pruebas unitarias, haga lo siguiente después de iniciar Live Unit Testing:

1. Haga clic con el botón derecho en la solución en el **Explorador de soluciones** y elija **Live Unit Testing** > **Excluir** para excluir toda la solución.
1. Haga clic con el botón derecho en cada proyecto de prueba que le gustaría incluir en las pruebas y elija **Live Unit Testing** > **Incluir**.

### <a name="exclude-individual-tests-from-the-code-editor-window"></a>Exclusión de pruebas individuales de la ventana del editor de código

Puede usar la ventana del editor de código para incluir o excluir métodos de prueba individuales. Haga clic con el botón derecho en la firma del método de prueba en la ventana del editor de código y seleccione una de las opciones siguientes:

- **Live Unit Testing** > **Incluir \<selected method>**
- **Live Unit Testing** > **Excluir\<selected method>**
- **Live Unit Testing** > **Excluir todas menos\<selected method>**

### <a name="exclude-tests-programmatically"></a>Exclusión de pruebas mediante programación

Puede aplicar el atributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> para, mediante programación, excluir los métodos, las clases o las estructuras y evitar que informen de su cobertura en Live Unit Testing.

Use los atributos siguientes para excluir los métodos individuales de Live Unit Testing:

- Para xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Para NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- Para MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

Use los atributos siguientes para excluir un conjunto entero de pruebas de Live Unit Testing:

- Para xUnit: `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Para NUnit: `[assembly: Category("SkipWhenLiveUnitTesting")]`
- Para MSTest: `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Vea también

- [Herramientas de pruebas de código](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Blog de Live Unit Testing](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [Preguntas más frecuentes de Live Unit Testing](live-unit-testing-faq.md)
- [Vídeo de Channel 9: Live Unit Testing en Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
