---
title: Usar los comprobadores de C++ Core Guidelines
ms.date: 08/14/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
dev_langs:
- CPP
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 735b4891449d139058b7cf114639390f6a930b55
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908351"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Usar los comprobadores de C++ Core Guidelines
C++ Core Guidelines son un conjunto de directrices, reglas y procedimientos recomendados sobre cómo codificar en C++ creados por los diseñadores y expertos de C++ portátil. Visual Studio actualmente admite un subconjunto de estas reglas como parte de sus herramientas de análisis de código de C++. Los comprobadores de directrices principales se instalan de forma predeterminada en Visual Studio 2017 y son [disponible como un paquete de NuGet para Visual Studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>El proyecto de C++ Core Guidelines
 Creado por Bjarne Stroustrup etc., C++ Core Guidelines son una guía para utilizar C++ moderno de forma segura y eficaz. Hacer hincapié en las directrices de seguridad de tipos estáticos y seguridad de recursos. Se identifican formas de eliminar o minimizar las partes más propensos a errores del lenguaje y sugieren cómo hacer que el código sea más sencillo y más eficaces de forma confiable. Estas instrucciones se mantienen por la base de C++ estándar. Para obtener más información, consulte la documentación, [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)y obtener acceso a los archivos de proyecto de la documentación de C++ Core Guidelines en [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Habilitar las instrucciones en el análisis de código de C++ Core Check
 Puede habilitar el análisis de código en el proyecto seleccionando el **Habilitar análisis de código al compilar** casilla de verificación en la **análisis de código** sección de la **páginas de propiedades** cuadro de diálogo el proyecto.

 ![Página de propiedades de configuración General de análisis de código](media/cppcorecheck_codeanalysis_general.png)

 Un subconjunto de reglas de C++ Core Check se incluye en el conjunto de reglas recomendadas nativas de Microsoft que se ejecuta de forma predeterminada cuando se habilita el análisis de código. Para habilitar reglas adicionales Core Check, haga clic en la lista desplegable y elija qué conjuntos de reglas que van a incluir:

 ![Lista desplegable de conjuntos de reglas adicionales de C++ Core Check](media/cppcorecheck_codeanalysis_extensions.png)

## <a name="examples"></a>Ejemplos
 Este es un ejemplo de algunos de los problemas que pueden encontrar las reglas de C++ Core Check:

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

En este ejemplo muestra algunas de las advertencias que pueden encontrar las reglas de C++ Core Check:

- C26494 es regla tipo.5: siempre debe inicializarse un objeto.

- C26485 es regla Bounds.3: ninguna decadencia de matriz a puntero.

- C26481 es regla Bounds.1: no usar aritmética de puntero. Utilice `span` en su lugar.

Si los rulesets de análisis de código de C++ Core Check estén instalados y habilitados cuando se compila este código, las dos primeras advertencias son de salida, pero se suprime la tercera. Este es el resultado de compilación del código de ejemplo:

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

C++ Core Guidelines sirven para ayudarle a escribir código mejor y más seguro. Sin embargo, si tiene una instancia que no debe aplicarse una regla o un perfil, es fácil que la suprima directamente en el código. Puede usar el `gsl::suppress` atributo para impedir que C++ Core Check detectar e informes de cualquier infracción de una regla en el bloque de código siguiente. Puede marcar las instrucciones individuales para suprimir reglas específicas. Incluso puede suprimir todo el perfil bounds escribiendo `[[gsl::suppress(bounds)]]` sin necesidad de incluir un número específico de regla.

## <a name="supported-rule-sets"></a>Admite conjuntos de reglas
Cuando se agregan nuevas reglas para el Comprobador de directrices principales de C++, puede aumentar el número de advertencias que se generan para código preexistente. Puede usar conjuntos de reglas predefinidas para filtrar qué tipos de reglas para habilitar.
Temas de referencia para la mayoría de las reglas están bajo [comprobar referencia de C++ Core de Visual Studio](code-analysis-for-cpp-corecheck.md).

A partir de Visual Studio 2017 versión 15.3, los conjuntos de reglas compatibles son:
- **Reglas de puntero Owner** aplicar [administración de recursos comprueba relacionadas con owner<T> de C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Reglas de constantes** aplicar [relacionadas con las comprobaciones de C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

- **Reglas de puntero sin formato** aplicar [administración de recursos comprueba relacionados a raw punteros de C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Reglas de puntero único** aplicar [comprueba de administración de recursos relativas a tipos con semántica de puntero único de C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Reglas de límites** exigir la [delimita el perfil de C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

- **Escriba reglas** exigir la [tipo de perfil de C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

**Versión 15.5 de Visual Studio 2017**:

- **Clase reglas** unas reglas que se centran en el uso correcto de las funciones miembro especiales y especificaciones virtuales. Se trata de un subconjunto de las comprobaciones que se recomienda para [clases y las jerarquías de clases](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class).
- **Las reglas de simultaneidad** una única regla, que detecta los objetos de restricción declarado incorrectamente. Para obtener más información, consulte [directrices relacionadas con la simultaneidad](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency).
- **Reglas de declaración** un par de reglas desde el [interfaces directrices](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) que se centran en las variables globales de cómo se declaran.
- **Función reglas** dos comprobaciones que ayudan con la adopción de la `noexcept` especificador. Esta es una parte de las instrucciones para [borrar función diseño e implementación](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions).
- **Reglas de puntero compartido** como parte de [administración de recursos](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) el cumplimiento de las directrices, hemos agregado unas reglas específicas de punteros compartidos cómo se pasan a las funciones o se usa localmente.
- **Reglas de estilo** una comprobación simple pero importante, que prohíbe el uso de [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto). Este es el primer paso en la mejora de la programación de estilo y el uso de expresiones e instrucciones en C++.

**Visual Studio 2017 versión 15.6**:

- **Reglas aritméticas** reglas para detectar operaciones aritméticas [desbordamiento](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow), [unsigned firmado operaciones](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned) y [manipulación de bits](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative).

Puede limitar las advertencias para solo uno o varios de los grupos. El **mínimo nativo** y **recomienda nativo** regla conjuntos incluyen reglas de C++ Core Check además otras comprobaciones de PREfast. Para ver los contadores a conjuntos de reglas, abra el cuadro de diálogo Propiedades del proyecto, seleccione **código Analysis\General**, abra la lista desplegable en el **conjuntos de reglas** cuadro combinado y seleccionar **elegir varios conjuntos de reglas** . Para obtener más información sobre el uso de conjuntos de reglas en Visual Studio, consulte [utilizando conjuntos de reglas para agrupar reglas de análisis de código](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Macros

El Comprobador de directrices de C++ Core incluye un archivo de encabezado que define las macros que facilitan suprimir todas las categorías de advertencias en el código:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Estas macros se corresponden con los conjuntos de reglas y expandir en una lista separada por espacios de números de advertencia. Mediante el uso de las construcciones de pragma adecuado, puede configurar el conjunto efectivo de reglas que es interesante para un proyecto o una sección de código. En el ejemplo siguiente, el análisis de código advierte solo faltan modificadores constantes:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Atributos

El compilador de Microsoft Visual C++ tiene una compatibilidad limitada con la GSL suprimir el atributo. Se puede usar para suprimir las advertencias en la expresión y las instrucciones del bloque dentro de una función.

```cpp
// Supress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Supress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppressing-analysis-by-using-command-line-options"></a>Supresión de análisis mediante las opciones de línea de comandos

En lugar de #pragmas, puede usar las opciones de línea de comandos en la página de propiedades del archivo para suprimir las advertencias para un proyecto o un único archivo. Por ejemplo, para deshabilitar la advertencia 26400 para un archivo:

1. Haga clic en el archivo en **el Explorador de soluciones**

2. Elija **propiedades | C / C ++ | Línea de comandos**

3. En el **opciones adicionales** ventana, agregar `/wd26400`.

Puede usar la opción de línea de comandos para deshabilitar temporalmente todos los análisis de código para un archivo mediante la especificación `/analyze-`. Esto genera la advertencia *D9025 reemplazar '/ analyze' con ' / analyze: '*, que le recuerda que debe volver a habilitar el análisis de código más adelante.

## <a name="corecheck_per_file"></a> Habilitar el Comprobador de C++ Core directrices en archivos de proyecto específicos

A veces puede ser útil para realizar centrado de análisis de código y todavía uso el IDE de Visual Studio. El siguiente escenario de ejemplo puede usarse para proyectos de gran tamaño para ahorrar tiempo de compilación y para que sea más fácil para filtrar los resultados:

1. En el shell de comandos establece la `esp.extension` y `esp.annotationbuildlevel` variables de entorno.
2. Para heredar estas variables, inicie Visual Studio desde el shell de comandos.
3. Cargar el proyecto y abra sus propiedades.
4. Habilitar análisis de código, seleccionar los conjuntos de reglas adecuada, pero no habilita las extensiones de análisis de código.
5. Vaya al archivo que desea analizar con el Comprobador de directrices principales de C++ y abrir sus propiedades.
6. Elija **C / C ++ \Command las opciones de línea** y agregar `/analyze:plugin EspXEngine.dll`
7. Deshabilitar el uso del encabezado precompilado (**C / C ++ \Precompiled encabezados**). Esto es necesario porque el motor de extensiones puede intentar leer la información interna del encabezado precompilado (PCH); Si el PCH compilado con las opciones de proyecto predeterminadas, no serán compatible.
8. Recompile el proyecto. Deben ejecutar las comprobaciones de PREFast comunes en todos los archivos. Dado que el Comprobador de directrices principales de C++ no está habilitado de forma predeterminada, solo debe ejecutar en el archivo que está configurado para usarlo.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Cómo usar el Comprobador de directrices de C++ Core fuera de Visual Studio

Puede usar las comprobaciones de C++ Core Guidelines en compilaciones automatizadas.

### <a name="msbuild"></a>MSBuild
 El Comprobador de análisis de código nativo (PREfast) se integra en el entorno de MSBuild mediante archivos de destinos personalizados. Puede usar las propiedades del proyecto para habilitarla y agregar el Comprobador de directrices principales de C++ (que se basa en PREfast):

 ```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

Asegúrese de que agregar estas propiedades antes de importar el archivo Microsoft.Cpp.targets. Puede elegir conjuntos de reglas específicas o crear un conjunto de reglas personalizado o usar el conjunto de reglas predeterminado que incluye otras comprobaciones de PREfast.

Puede ejecutar el Comprobador de C++ Core solo en los archivos especificados utilizando el mismo enfoque que [se ha descrito anteriormente](#corecheck_per_file), pero con archivos de MSBuild. Se pueden establecer las variables de entorno mediante el `BuildMacro` elemento:

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>CppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Si no desea modificar el archivo de proyecto, puede pasar propiedades en la línea de comandos:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Proyectos que no son de MSBuild

Si usa un sistema de compilación que no se basa en MSBuild todavía puede ejecutar el Comprobador, pero deberá familiarizarse con algunos aspectos internos de la configuración del motor de análisis de código. Estos elementos internos se garantiza que no se admite en el futuro.

Tendrá que establecer algunas variables de entorno y usar las opciones de línea de comandos adecuadas para el compilador. Es mejor trabajar en el entorno de "línea de comandos de herramientas nativo" para que no tiene que buscar rutas de acceso específicas para el compilador, incluir directorios, etcetera.

1. **Variables de entorno**
   - `set esp.extensions=cppcorecheck.dll` Esto indica al motor para cargar el módulo de C++ Core Guidelines.
   - `set esp.annotationbuildlevel=ignore` Esto deshabilita la lógica que procesa las anotaciones de SAL. Las anotaciones no afectan a los análisis de código en el Comprobador de directrices principales de C++, aunque su procesamiento lleva tiempo (en ocasiones, una hora larga). Esta configuración es opcional, pero muy recomendado.
   - `set caexcludepath=%include%` Se recomienda encarecidamente que deshabilitar las advertencias que se activan en los encabezados estándar. Puede agregar más rutas de acceso, por ejemplo la ruta de acceso a los encabezados comunes en el proyecto.
2. **Opciones de línea de comandos**
   - `/analyze`  Habilita el análisis de código (considere también usar / analyze: solo y / analyze: quiet).
   - `/analyze:plugin EspXEngine.dll` Esta opción, carga el motor de extensiones de análisis de código en el PREfast. Este motor, a su vez, carga el Comprobador de directrices principales de C++.

## <a name="use-the-guideline-support-library"></a>Uso de la biblioteca de compatibilidad con criterio
 La biblioteca de compatibilidad de instrucciones está diseñada para ayudarle a seguir las instrucciones de núcleo. El GSL incluye las definiciones que le permiten reemplazar construcciones propensas a errores por alternativas más seguras. Por ejemplo, puede reemplazar un `T*, length` par de parámetros con el `span<T>` tipo. Está disponible en el GSL [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). La biblioteca es código abierto, por lo que puede ver los orígenes, hacer comentarios o contribuir. El proyecto puede encontrarse en [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

## <a name="vs2015_corecheck"></a> Use las directrices de C++ Core Check en proyectos de Visual Studio 2015

Si usa Visual Studio 2015, los conjuntos de reglas de análisis de código de C++ Core Check no se instalan de forma predeterminada. Debe realizar algunos pasos adicionales antes de poder habilitar las herramientas de análisis de código de C++ Core Check en Visual Studio 2015. Microsoft proporciona compatibilidad para los proyectos de Visual Studio 2015 mediante un paquete de Nuget. El paquete se denomina Microsoft.CppCoreCheck, y está disponible en [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Este paquete requiere que tenga al menos Visual Studio 2015 con Update 1 instalado.

El paquete también instala otro paquete como una dependencia de un solo encabezado directriz soporte técnico de biblioteca (GSL). También está disponible en GitHub en el GSL [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

Debido al modo en que se cargan las reglas de análisis de código, debe instalar el paquete Microsoft.CppCoreCheck NuGet en cada proyecto de C++ que se desea comprobar dentro de Visual Studio 2015.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Para agregar el paquete de Microsoft.CppCoreCheck al proyecto en Visual Studio 2015

1. En **el Explorador de soluciones**, con el botón secundario para abrir el menú contextual del proyecto en la solución que desea agregar el paquete. Elija **administrar paquetes de NuGet** para abrir el **Administrador de paquetes de NuGet**.

2. En el **Administrador de paquetes de NuGet** ventana, busque Microsoft.CppCoreCheck.

    ![Ventana Administrador de paquetes de NuGet muestra el paquete de CppCoreCheck](../code-quality/media/cppcorecheck_nuget_window.png)

3. Seleccione el paquete Microsoft.CppCoreCheck y, a continuación, elija el **instalar** para agregar las reglas a su proyecto.

   El paquete NuGet agrega un MSBuild adicional *.targets* archivo al proyecto que se invoca cuando se habilita el análisis de código en el proyecto. Esto *.targets* archivo agrega las reglas de C++ Core Check como una extensión adicional a la herramienta de análisis de código de Visual Studio. Cuando se instala el paquete, puede usar el cuadro de diálogo páginas de propiedades para habilitar o deshabilitar las reglas publicadas y experimentales.

## <a name="see-also"></a>Vea también

- [Referencia de Visual Studio C++ Core Check](code-analysis-for-cpp-corecheck.md)