---
title: Cobertura de código en Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: article
helpviewer_keywords:
- code coverage
dev_langs:
- CSharp
- VB
- CPP
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 5df1d946dff9d02756a08905d6d0092a10d49ae1
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Usar cobertura de código para determinar la cantidad de código que se está probando

Para determinar qué proporción de código del proyecto se está probando realmente mediante pruebas codificadas como pruebas unitarias, se puede utilizar la característica de cobertura de código de Visual Studio. Para restringir con eficacia los errores, las pruebas deberían ensayar o “cubrir” una proporción considerable del código.

El análisis de cobertura de código puede aplicarse al código administrado (CLI) y no administrado (nativo).

La cobertura de código es una opción al ejecutar métodos de prueba mediante el Explorador de pruebas. La tabla de salida muestra el porcentaje de código que se ejecuta en cada ensamblado, clase y método. Además, el editor de código fuente muestra qué código se ha probado.

![Resultados de cobertura de código con colores](../test/media/codecoverage1.png)

 **Requisitos**

-   Visual Studio Enterprise

## <a name="to-analyze-code-coverage-on-unit-tests-in-test-explorer"></a>Para analizar la cobertura de código en pruebas unitarias en el Explorador de pruebas

1.  En el menú **Prueba**, elija **Analizar cobertura de código**.

2.  Para ver qué líneas se han ejecutado, elija ![Icono Mostrar colores en cobertura de código](../test/media/codecoverage-showcoloringicon.png)**Mostrar colores en cobertura de código**.

     Para modificar los colores o utilizar la negrita, elija **Herramientas** > **Opciones** > **Entorno** > **Fuentes y colores** > **Mostrar valores para: Editor de texto**. En **Mostrar los elementos**, ajuste los elementos de cobertura.

3.  Si los resultados muestran una cobertura baja, investigue qué partes del código no se están ensayando y escriba más pruebas para abarcarlas. Los equipos de desarrollo normalmente aspiran a una cobertura de código de un 80 %. En algunas situaciones, una cobertura menor es aceptable. Por ejemplo, una cobertura menor es aceptable cuando el código se genera a partir de una plantilla estándar.

> [!TIP]
> - Asegúrese de que la optimización del compilador está desactivada.
> - Si está trabajando con código no administrado (nativo), utilice una compilación de depuración.
> - Asegúrese de que está generando los archivos .pdb (símbolo) para cada ensamblado.

Si no obtiene los resultados esperados, vea [Solución de problemas de cobertura de código](../test/troubleshooting-code-coverage.md). . No olvide ejecutar la cobertura de código de nuevo después de actualizar el código. Los resultados de cobertura y color de código no se actualizan automáticamente después de modificar el código o al ejecutar pruebas.

## <a name="report-in-blocks-or-lines"></a>Informar en bloques o líneas

La cobertura de código se cuenta en *bloques*. Un bloque es un fragmento de código con un punto de entrada y de salida exactamente.  Si el flujo de control del programa pasa a través de un bloque durante una serie de pruebas, ese bloque se cuenta como cubierto. El número de veces que se utiliza el bloque no tiene ningún efecto en el resultado.

También se pueden mostrar los resultados en líneas eligiendo **Agregar o quitar columnas** en el encabezado de tabla. Si la serie de pruebas probó todos los bloques de código en cualquier línea de código, se cuenta como una línea. Siempre que una línea contenga algunos bloques de código que se han ejecutado y otros que no, se cuenta como una línea parcial.

Algunos usuarios prefieren un recuento de líneas porque los porcentajes corresponden más al tamaño de los fragmentos que aparece en el código fuente. Un bloque grande de cálculo contaría como un único bloque aunque ocupe muchas líneas.

## <a name="manage-code-coverage-results"></a>Administrar resultados de cobertura de código

La ventana de resultados de cobertura de código normalmente muestra el resultado de la ejecución más reciente. Los resultados variarán si se cambian los datos de prueba, o si se ejecutan solo algunas pruebas cada vez.

La ventana de cobertura de código también se puede utilizar para ver los resultados anteriores o los resultados obtenidos en otros equipos.

Se pueden fusionar mediante combinación los resultados de varias ejecuciones, por ejemplo de las ejecuciones que utilizan distintos datos de prueba.

-   **Para ver un conjunto anterior de resultados**, selecciónelo en el menú desplegable. El menú muestra una lista temporal que se borra cuando se abre una nueva solución.

-   **Para ver los resultados de una sesión anterior**, elija **Importar resultados de la cobertura de código**, navegue hasta la carpeta TestResults de la solución e importe un archivo .coverage.

    El color de cobertura puede ser incorrecto si el código fuente ha cambiado desde que se generó el archivo .coverage.

-   **Para crear resultados legibles como texto**, elija **Exportar resultados de la cobertura de código**. Esto genera un archivo .coveragexml legible que se puede procesar con otras herramientas o enviar por correo fácilmente.

-   **Para enviar resultados a otra persona**, envíe un archivo .coverage o un archivo exportado .coveragexml. Después pueden importar el archivo. Si tienen la misma versión de código fuente, pueden ver el color de cobertura.

## <a name="merge-results-from-different-runs"></a>Combinar resultados de diferentes ejecuciones

En algunas situaciones, se utilizarán diferentes bloques de código, en función de los datos de prueba. Por consiguiente, es posible que se deseen combinar los resultados de varias series de pruebas.

 Por ejemplo, suponga que al ejecutar una prueba con la entrada “2", se detecta que el 50 % de una determinada función está cubierto. Al ejecutar la prueba una segunda vez con la entrada “-2" se observa en la vista de color de destino que el otro 50 % de la función está cubierto. Ahora se fusionan mediante combinación los resultados de las dos series de pruebas y tanto el informe como la vista de color de cobertura muestran que el 100 % de la función se ha analizado.

 Utilice ![icono para el botón Combinar en la ventana de cobertura de código](../test/media/codecoverage-mergeicon.png "CodeCoverage MergeIcon")**combinar resultados de la cobertura de código** para ello. Se puede elegir cualquier combinación de ejecuciones recientes o de resultados importados. Si se desea combinar resultados exportados, se deben importar primero.

 Utilice **Exportar resultados de la cobertura de código** para guardar los resultados de una operación Merge.

### <a name="limitations-in-merging"></a>Limitaciones de la combinación

-   Si se combinan datos de cobertura de distintas versiones del código, los resultados se muestran por separado, pero no se combinan. Para obtener resultados combinados totalmente, utilice la misma compilación del código, cambiando únicamente los datos de prueba.

-   Si se fusiona mediante combinación un archivo de resultados que se ha exportado y después se ha importado, se pueden ver únicamente los resultados por líneas, no por bloques. Utilice el comando **Agregar o quitar columnas** para mostrar los datos de línea.

-   Si se fusionan mediante combinación los resultados de pruebas de un proyecto ASP.NET, los resultados de pruebas separadas se muestran, pero no se combinan. Esto se aplica solo a los artefactos de ASP.NET: los resultados para cualquier otro ensamblado se combinan.

## <a name="exclude-elements-from-the-code-coverage-results"></a>Excluir elementos de los resultados de la cobertura de código

Puede que se desee excluir elementos concretos del código de las puntuaciones de cobertura, por ejemplo si el código se genera a partir de una plantilla de texto. Agregue el atributo `System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverage` a cualquiera de los elementos de código: clase, struct, método, propiedad, establecedor o captador de propiedad, evento. Observe que excluir una clase no excluye sus clases derivadas.

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

-   *ExclusionName* es cualquier hombre único.

-   *FunctionName* es un nombre de función completo. Puede contener comodines. Por ejemplo, para excluir todas las funciones de una clase, escriba `MyNamespace::MyClass::*`

-   *SourceFilePath* es la ruta de acceso UNC o local de un archivo .cpp. Puede contener comodines. En el siguiente ejemplo se excluyen todos los archivos de un directorio concreto: `\\MyComputer\Source\UnitTests\*.cpp`

-   `#include <CodeCoverage\CodeCoverage.h>`

-   Coloque llamadas a macros de exclusión en el espacio de nombres global, no dentro de ningún espacio de nombres o clase.

-   Se pueden colocar las exclusiones en el archivo de código de pruebas unitarias o en el archivo de código de aplicación.

-   Las exclusiones se deben compilar como código no administrado (nativo), estableciendo la opción del compilador o mediante `#pragma managed(off)`.

> [!NOTE]
> Para excluir funciones en el código de C++/CLI, aplique el atributo `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` a la función. Este el mismo que para C#.

### <a name="include-or-exclude-additional-elements"></a>Incluir o excluir elementos adicionales

El análisis de cobertura de código se realiza únicamente en los ensamblados que están cargados, para los qué está disponible un archivo .pdb en el mismo directorio que el archivo .dll o .exe. Por consiguiente, en determinadas circunstancias, se puede extender el conjunto de ensamblados que se incluye obteniendo copias de los archivos .pdb adecuados.

Se puede tener más control sobre qué ensamblados y elementos están seleccionados para el análisis de cobertura de código escribiendo un archivo .runsettings. Por ejemplo, se pueden excluir los ensamblados de determinados tipos sin tener que agregar atributos a sus clases. Para obtener más información, consulte [Personalizar el análisis de cobertura de código](../test/customizing-code-coverage-analysis.md).

## <a name="analyze-code-coverage-in-the-build-service"></a>Analizar la cobertura de código en el servicio de compilación

Al insertar en el repositorio el código, las pruebas se ejecutarán en el servidor de compilación, junto con todas las demás pruebas de otros miembros del equipo. (Si aún no lo ha configurado, vea [Ejecutar pruebas en el proceso de compilación](http://msdn.microsoft.com/Library/d05743a1-c5cf-447e-bed9-bed3cb595e38)). Es útil analizar la cobertura de código del servicio de compilación, porque proporciona la imagen más actualizada y más completa de cobertura de todo el proyecto. También se incluyen las pruebas del sistema automatizadas y otras pruebas codificadas que no se ejecutan normalmente en los equipos de desarrollo.

1. En Team Explorer, abra **Compilaciones** y agregue o modifique una definición de compilación.

2. En la página **Proceso**, expanda **Pruebas automatizadas**, **Origen de la prueba**, **Parámetros de ejecución**. Establezca **Tipo de archivo de parámetros de configuración** en **Cobertura de código habilitada**.

   Si tiene más de una definición de origen de la prueba, repita este paso para cada una.

   ![Establecer la definición de compilación para cobertura de código](../test/media/codecoverage-plaincc.png "CodeCoverage-plainCC")

> [!TIP]
> Si no hay ningún campo denominado **Tipo de archivo de parámetros de ejecución**, cambie la propiedad **Ejecutor de pruebas**. En **Pruebas automatizadas**, seleccione **Ensamblado de prueba** y elija los puntos suspensivos **[...]** al final de la línea. En el cuadro de diálogo **Agregar o editar serie de pruebas**, en **Ejecutor de pruebas**, elija **Ejecutor de pruebas de Visual Studio**.

Después de que la compilación se ejecute, los resultados de cobertura de código están asociados a la serie de pruebas y aparecen en el resumen de la compilación.

## <a name="analyze-code-coverage-in-a-command-line"></a>Analizar la cobertura del código en una línea de comandos

Para ejecutar pruebas desde la línea de comandos, utilice vstest.console.exe. La cobertura de código es una opción de la utilidad vstest.console.exe.

1.  Abra el símbolo del sistema de Visual Studio Developer:

    En el menú **Inicio** de Windows, elija **Visual Studio 2017** > **Símbolo del sistema para desarrolladores de VS 2017**.

2.  Ejecute el siguiente comando:

    `vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage`

## <a name="troubleshoot"></a>Solucionar problemas

Si no ve los resultados de la cobertura de código, puede encontrar ayuda en el tema [Solución de problemas de cobertura de código](../test/troubleshooting-code-coverage.md).

## <a name="see-also"></a>Vea también

- [Personalizar el análisis de cobertura de código](../test/customizing-code-coverage-analysis.md)
- [Solucionar problemas de cobertura de código](../test/troubleshooting-code-coverage.md)
- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)
