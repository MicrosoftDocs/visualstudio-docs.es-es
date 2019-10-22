---
title: Pruebas de cobertura de código
ms.date: 07/23/2019
ms.topic: conceptual
helpviewer_keywords:
- code coverage
dev_langs:
- CSharp
- VB
- CPP
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1962a977cb282613405342f225d63140f1854453
ms.sourcegitcommit: 689ba54ea14257d13031de881f5d4fe937a36f56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71342421"
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Usar cobertura de código para determinar la cantidad de código que se está probando

Para determinar qué proporción de código del proyecto se está probando realmente mediante pruebas codificadas como pruebas unitarias, se puede utilizar la característica de cobertura de código de Visual Studio. Para restringir con eficacia los errores, las pruebas deberían ensayar o “cubrir” una proporción considerable del código.

El análisis de cobertura de código puede aplicarse al código administrado (CLI) y no administrado (nativo).

La cobertura de código es una opción al ejecutar métodos de prueba mediante el Explorador de pruebas. La tabla de salida muestra el porcentaje de código que se ejecuta en cada ensamblado, clase y método. Además, el editor de código fuente muestra qué código se ha probado.

::: moniker range="vs-2017"

![Resultados de cobertura de código con colores](../test/media/codecoverage1.png)

::: moniker-end

## <a name="requirements"></a>Requisitos

La característica de cobertura de código solo está disponible en la edición Visual Studio Enterprise.

## <a name="analyze-code-coverage"></a>Análisis de la cobertura de código

::: moniker range="vs-2017"

1. En el menú **Prueba**, elija **Analizar cobertura de código**.

::: moniker-end

::: moniker range=">=vs-2019"

1. En el menú **Prueba**, seleccione **Analizar cobertura de código para todas las pruebas**.

   ![Menú Análisis de la cobertura de código en VS 2019](../test/media/vs-2019/analyze-code-coverage.png)

   También puede ejecutar la cobertura de código desde la ventana de la herramienta Explorador de pruebas.

::: moniker-end

2. Después de que se hayan ejecutado las pruebas, para ver qué líneas se han ejecutado, elija ![Icono Mostrar colores en cobertura de código](../test/media/codecoverage-showcoloringicon.png) **Mostrar colores en cobertura de código** en la ventana **Resultados de cobertura de código**. De forma predeterminada, el código que se incluye en las pruebas se resalta en color azul claro.

   > [!TIP]
   > Para cambiar los colores o usar la negrita, elija **Herramientas** > **Opciones** > **Entorno** > **Fuentes y colores** > **Mostrar valores para: Editor de texto**. En **Mostrar los elementos**, ajuste la configuración de los elementos "Cobertura", por ejemplo, **Área de cobertura no modificada**.
   >
   > ![Fuentes y colores de cobertura de código](media/vs-2019/coverage-fonts-and-colors.png)

3. Si los resultados muestran una cobertura baja, investigue qué partes del código no se están ensayando y escriba más pruebas para abarcarlas. Los equipos de desarrollo normalmente aspiran a una cobertura de código de un 80 %. En algunas situaciones, una cobertura menor es aceptable. Por ejemplo, una cobertura menor es aceptable cuando el código se genera a partir de una plantilla estándar.

> [!TIP]
> - Desactive la optimización del compilador.
> - Si está trabajando con código no administrado (nativo), utilice una compilación de depuración.
> - Genere archivos. pdb (símbolo) para cada ensamblado.

Si no obtiene los resultados esperados, consulte [Solución de problemas de cobertura de código](../test/troubleshooting-code-coverage.md).

No olvide ejecutar la cobertura de código de nuevo después de actualizar el código. Los resultados de cobertura y color de código no se actualizan automáticamente después de modificar el código o al ejecutar pruebas.

## <a name="report-in-blocks-or-lines"></a>Informar en bloques o líneas

La cobertura de código se cuenta en *bloques*. Un bloque es un fragmento de código con un punto de entrada y de salida exactamente.  Si el flujo de control del programa pasa a través de un bloque durante una serie de pruebas, ese bloque se cuenta como cubierto. El número de veces que se utiliza el bloque no tiene ningún efecto en el resultado.

También se pueden mostrar los resultados en líneas eligiendo **Agregar o quitar columnas** en el encabezado de tabla. Algunos usuarios prefieren un recuento de líneas porque los porcentajes corresponden más al tamaño de los fragmentos que aparece en el código fuente. Un bloque grande de cálculo contaría como un único bloque aunque ocupe muchas líneas.

> [!TIP]
> Una línea de código puede contener más de un bloque de código. Si este es el caso y la serie de pruebas emplea todos los bloques de código en la línea, se cuenta como una línea. Si en la línea se emplean algunos bloques de código, pero no todos, se cuenta como una línea parcial.

## <a name="manage-code-coverage-results"></a>Administrar resultados de cobertura de código

La ventana de **resultados de cobertura de código** normalmente muestra el resultado de la ejecución más reciente. Los resultados variarán si se cambian los datos de prueba, o si se ejecutan solo algunas pruebas cada vez.

La ventana de cobertura de código también se puede utilizar para ver los resultados anteriores o los resultados obtenidos en otros equipos.

Se pueden fusionar mediante combinación los resultados de varias ejecuciones, por ejemplo de las ejecuciones que utilizan distintos datos de prueba.

- **Para ver un conjunto anterior de resultados**, selecciónelo en el menú desplegable. El menú muestra una lista temporal que se borra cuando se abre una nueva solución.

- **Para ver los resultados de una sesión anterior**, elija **Importar resultados de la cobertura de código**, navegue hasta la carpeta **TestResults** de la solución e importe un archivo *.coverage*.

   El color de cobertura puede ser incorrecto si el código fuente ha cambiado desde que se generó el archivo *.coverage*.

- **Para crear resultados legibles como texto**, elija **Exportar resultados de la cobertura de código**. Esto genera un archivo *.coveragexml* legible que se puede procesar con otras herramientas o enviar por correo fácilmente.

- **Para enviar resultados a otra persona**, envíe un archivo *.coverage* o un archivo exportado *.coveragexml*. Después pueden importar el archivo. Si tienen la misma versión de código fuente, pueden ver el color de cobertura.

## <a name="merge-results-from-different-runs"></a>Combinar resultados de diferentes ejecuciones

En algunas situaciones, se utilizarán diferentes bloques de código, en función de los datos de prueba. Por consiguiente, es posible que se deseen combinar los resultados de varias series de pruebas.

Por ejemplo, suponga que al ejecutar una prueba con la entrada “2", se detecta que el 50 % de una determinada función está cubierto. Al ejecutar la prueba una segunda vez con la entrada "-2" se observa en la vista de color de destino que el otro 50 % de la función está cubierto. Ahora se fusionan mediante combinación los resultados de las dos series de pruebas y tanto el informe como la vista de color de cobertura muestran que el 100 % de la función se ha analizado.

Use ![Icono para el botón Combinar en la ventana de cobertura de código](../test/media/codecoverage-mergeicon.png) **Combinar resultados de la cobertura de código** para ello. Se puede elegir cualquier combinación de ejecuciones recientes o de resultados importados. Si se desea combinar resultados exportados, se deben importar primero.

Utilice **Exportar resultados de la cobertura de código** para guardar los resultados de una operación Merge.

### <a name="limitations-in-merging"></a>Limitaciones de la combinación

- Si se combinan datos de cobertura de distintas versiones del código, los resultados se muestran por separado, pero no se combinan. Para obtener resultados combinados totalmente, utilice la misma compilación del código, cambiando únicamente los datos de prueba.

- Si se fusiona mediante combinación un archivo de resultados que se ha exportado y después se ha importado, se pueden ver únicamente los resultados por líneas, no por bloques. Utilice el comando **Agregar o quitar columnas** para mostrar los datos de línea.

- Si se fusionan mediante combinación los resultados de pruebas de un proyecto ASP.NET, los resultados de pruebas separadas se muestran, pero no se combinan. Esto se aplica solo a los artefactos de ASP.NET: los resultados para cualquier otro ensamblado se combinan.

## <a name="exclude-elements-from-the-code-coverage-results"></a>Excluir elementos de los resultados de la cobertura de código

Puede que se desee excluir elementos concretos del código de las puntuaciones de cobertura, por ejemplo si el código se genera a partir de una plantilla de texto. Agregue el atributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> a cualquiera de los elementos de código: clase, struct, método, propiedad, establecedor o captador de propiedad, evento.

> [!TIP]
> Excluir una clase no excluye sus clases derivadas.

Por ejemplo:

```csharp
using System.Diagnostics.CodeAnalysis;
...
public class ExampleClass1
{
    [ExcludeFromCodeCoverage]
    void ExampleMethod() {...}

    [ExcludeFromCodeCoverage] // exclude property
    int ExampleProperty1
    { get {...} set{...}}

    int ExampleProperty2
    {
        get
        {
            ...
        }
        [ExcludeFromCodeCoverage] // exclude setter
        set
        {
            ...
        }
    }

}
[ExcludeFromCodeCoverage]
class ExampleClass2 { ... }
```

```vb
Imports System.Diagnostics.CodeAnalysis

Class ExampleClass1
    <ExcludeFromCodeCoverage()>
    Public Sub ExampleSub1()
        ...
    End Sub

    ' Exclude property
    < ExcludeFromCodeCoverage()>
    Property ExampleProperty1 As Integer
        ...
    End Property

    ' Exclude setter
    Property ExampleProperty2 As Integer
        Get
            ...
        End Get
        <ExcludeFromCodeCoverage()>
        Set(ByVal value As Integer)
            ...
        End Set
    End Property
End Class

<ExcludeFromCodeCoverage()>
Class ExampleClass2
...
End Class
```

```cpp
// A .cpp file compiled as managed (CLI) code.
using namespace System::Diagnostics::CodeAnalysis;
...
public ref class ExampleClass1
{
  public:
    [ExcludeFromCodeCoverage]
    void ExampleFunction1() { ... }

    [ExcludeFromCodeCoverage]
    property int ExampleProperty2 {...}

    property int ExampleProperty2 {
      int get() { ... }
     [ExcludeFromCodeCoverage]
      void set(int value) { ...  }
   }
}

[ExcludeFromCodeCoverage]
public ref class ExampleClass2
{ ... }
```

### <a name="exclude-elements-in-native-c-code"></a>Excluir elementos en código de C++ nativo

Para excluir elementos no administrados (nativos) en código de C++:

```cpp
#include <CodeCoverage\CodeCoverage.h>
...

// Exclusions must be compiled as unmanaged (native):
#pragma managed(push, off)

// Exclude a particular function:
ExcludeFromCodeCoverage(Exclusion1, L"MyNamespace::MyClass::MyFunction");

// Exclude all the functions in a particular class:
ExcludeFromCodeCoverage(Exclusion2, L"MyNamespace::MyClass2::*");

// Exclude all the functions generated from a particular template:
ExcludeFromCodeCoverage(Exclusion3, L"*::MyFunction<*>");

// Exclude all the code from a particular .cpp file:
ExcludeSourceFromCodeCoverage(Exclusion4, L"*\\unittest1.cpp");

// After setting exclusions, restore the previous managed/unmanaged state:
#pragma managed(pop)
```

Use las macros siguientes:

`ExcludeFromCodeCoverage(` *ExclusionName* `, L"` *FunctionName* `");`

`ExcludeSourceFromCodeCoverage(` *ExclusionName* `, L"` *SourceFilePath* `");`

- *ExclusionName* es cualquier hombre único.

- *FunctionName* es un nombre de función completo. Puede contener comodines. Por ejemplo, para excluir todas las funciones de una clase, escriba `MyNamespace::MyClass::*`

- *SourceFilePath* es la ruta de acceso UNC o local de un archivo .cpp. Puede contener comodines. En el siguiente ejemplo se excluyen todos los archivos de un directorio concreto: `\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- Coloque llamadas a macros de exclusión en el espacio de nombres global, no dentro de ningún espacio de nombres o clase.

- Se pueden colocar las exclusiones en el archivo de código de pruebas unitarias o en el archivo de código de aplicación.

- Las exclusiones se deben compilar como código no administrado (nativo), estableciendo la opción del compilador o mediante `#pragma managed(off)`.

> [!NOTE]
> Para excluir funciones en el código de C++/CLI, aplique el atributo `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` a la función. Este el mismo que para C#.

### <a name="include-or-exclude-additional-elements"></a>Incluir o excluir elementos adicionales

El análisis de cobertura de código se realiza únicamente en los ensamblados que están cargados, para los que está disponible un archivo *.pdb* en el mismo directorio que el archivo *.dll* o *.exe*. Por tanto, en determinadas circunstancias, se puede extender el conjunto de ensamblados que se incluye obteniendo copias de los archivos *.pdb* adecuados.

Se puede tener más control sobre qué ensamblados y elementos están seleccionados para el análisis de cobertura de código escribiendo un archivo *.runsettings*. Por ejemplo, se pueden excluir los ensamblados de determinados tipos sin tener que agregar atributos a sus clases. Para obtener más información, vea [Personalizar el análisis de cobertura de código](../test/customizing-code-coverage-analysis.md).

## <a name="analyze-code-coverage-in-azure-pipelines"></a>Analizar la cobertura de código en Azure Pipelines

Al insertar el código en el repositorio, las pruebas se ejecutan en el servidor de compilación junto con las pruebas de otros miembros del equipo. Es útil analizar la cobertura de código en Azure Pipelines para obtener la imagen más actualizada y completa de cobertura de todo el proyecto. También se incluyen las pruebas del sistema automatizadas y otras pruebas codificadas que no se ejecutan normalmente en los equipos de desarrollo. Para más información, consulte [Ejecutar pruebas unitarias con las compilaciones](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts).

## <a name="analyze-code-coverage-from-the-command-line"></a>Analizar la cobertura del código desde una línea de comandos

Para ejecutar pruebas desde la línea de comandos, utilice *vstest.console.exe*. La cobertura de código es una opción de la utilidad *vstest.console.exe*.

1. Inicie el Símbolo del sistema para desarrolladores de Visual Studio:

   ::: moniker range="vs-2017"

   En el menú **Inicio** de Windows, elija **Visual Studio 2017** > **Símbolo del sistema para desarrolladores de VS 2017**.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   En el menú **Inicio** de Windows, elija **Visual Studio 2019** > **Símbolo del sistema para desarrolladores de VS 2019**.

   ::: moniker-end

2. En el símbolo del sistema, ejecute el siguiente comando:

   ```shell
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage
   ```

Para obtener más información, vea [Opciones de la línea de comandos para VSTest.Console.exe](vstest-console-options.md).

## <a name="troubleshoot"></a>Solucionar problemas

Si no ve los resultados de la cobertura de código, puede encontrar ayuda en el artículo [Solución de problemas de cobertura de código](../test/troubleshooting-code-coverage.md).

## <a name="see-also"></a>Vea también

- [Personalizar el análisis de cobertura de código](../test/customizing-code-coverage-analysis.md)
- [Solucionar problemas de cobertura de código](../test/troubleshooting-code-coverage.md)
- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)
