---
title: Usar los comprobadores de C++ Core Guidelines
ms.date: 08/14/2018
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
dev_langs:
- CPP
ms.openlocfilehash: 95b3af7db7fc0e4c71d78716714031fd07dbdab5
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271770"
---
# <a name="use-the-c-core-guidelines-checkers"></a>Usar los comprobadores de C++ Core Guidelines

Las C++ instrucciones básicas son un conjunto portátil de directrices, reglas y prácticas recomendadas sobre la codificación C++ en creadas C++ por expertos y diseñadores. Visual Studio admite actualmente un subconjunto de estas reglas como parte de sus herramientas de análisis C++de código para. Los comprobadores de instrucciones principales se instalan de forma predeterminada en Visual Studio 2017 y Visual Studio 2019 y están [disponibles como un paquete de NuGet para visual studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Proyecto C++ de directrices básicas

Creado por Bjarne Stroustrup y otros, las C++ directrices principales son una guía para el uso C++ moderno y seguro de forma segura. Las instrucciones resaltan la seguridad de tipos estáticos y la seguridad de los recursos. Identifican maneras de eliminar o minimizar las partes más propensas a errores del lenguaje y sugieren cómo hacer que el código sea más sencillo y más eficaz de forma confiable. Estas instrucciones las mantiene la base estándar C++ . Para obtener más información, consulte la documentación, C++ [ C++ las directrices principales](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)y el acceso a los archivos de proyecto de documentación de directrices básicas en [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Habilitar las C++ directrices de la comprobación básica en el análisis de código
Puede habilitar el análisis de código en el proyecto activando la casilla **Habilitar análisis de código al compilar** en la sección **análisis de código** del cuadro de diálogo **páginas de propiedades** del proyecto.

![Página de propiedades de la configuración general de análisis de código](media/cppcorecheck_codeanalysis_general.png)

Se incluye un C++ subconjunto de reglas de comprobación básica en el conjunto de reglas de Microsoft nativo recomendado que se ejecuta de forma predeterminada cuando se habilita el análisis de código. Para habilitar reglas adicionales de comprobación básica, haga clic en la lista desplegable y elija los conjuntos de reglas que desea incluir:

![Lista desplegable C++ para conjuntos de reglas adicionales de comprobación básica](media/cppcorecheck_codeanalysis_extensions.png)

## <a name="examples"></a>Ejemplos
A continuación se muestra un ejemplo de algunos de los problemas C++ que pueden encontrar las reglas de comprobación básicas:

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

En este ejemplo se muestran algunas de las advertencias que C++ las reglas de comprobación básicas pueden encontrar:

- C26494 es el tipo de regla. 5: Siempre debe inicializarse un objeto.

- C26485 es el límite de reglas. 3: No hay decadencia de matriz a puntero.

- C26481 es el límite de reglas. 1: No usar aritmética de puntero. Utilice `span` en su lugar.

Si los C++ conjuntos de herramientas de análisis de código de comprobación básica se instalan y se habilitan al compilar este código, se generan las dos primeras advertencias, pero se suprime la tercera. Este es el resultado de la compilación del código de ejemplo:

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Aquí C++ encontrará instrucciones básicas que le ayudarán a escribir código mejor y más seguro. Sin embargo, si tiene una instancia de en la que no se debe aplicar una regla o un perfil, es fácil suprimirla directamente en el código. Puede usar el atributo `gsl::suppress` para mantener C++ la comprobación principal de detectar e informar de cualquier infracción de una regla en el siguiente bloque de código. Puede marcar instrucciones individuales para suprimir reglas específicas. Incluso puede suprimir el perfil de límite completo escribiendo `[[gsl::suppress(bounds)]]` sin incluir un número de regla específico.

## <a name="supported-rule-sets"></a>Conjuntos de reglas admitidos
A medida que se agregan nuevas C++ reglas al comprobador de directrices básicas, puede aumentar el número de advertencias que se producen para el código existente previamente. Puede usar conjuntos de reglas predefinidos para filtrar los tipos de reglas que se van a habilitar.
Los temas de referencia de la mayoría de las reglas se encuentran en [referencia de Visual C++ Studio Core check](code-analysis-for-cpp-corecheck.md).

A partir de la versión 15,3 de Visual Studio 2017, los conjuntos de reglas admitidos son:
- **Las reglas de puntero de propietario** aplican [comprobaciones de administración de recursos relacionadas con C++ el propietario\<t > de las directrices básicas](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Las reglas const** aplican [comprobaciones relacionadas con C++ const de las instrucciones básicas](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

- **Las reglas de puntero sin formato** aplican [comprobaciones de administración de recursos relacionadas C++ con los punteros sin formato de las directrices básicas](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Las reglas de puntero único** aplican [comprobaciones de administración de recursos relacionadas con tipos con semántica C++ de puntero única de las instrucciones básicas](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Las reglas de límites** exigen el [Perfil de límite C++ de las directrices básicas](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

- **Las reglas de tipo** exigen el [perfil C++ de tipo de las instrucciones básicas](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

**Versión 15.5 de Visual Studio 2017**:

- **Reglas de clase** Algunas reglas que se centran en el uso correcto de las funciones miembro especiales y las especificaciones virtuales. Este es un subconjunto de las comprobaciones recomendadas para [las clases y las jerarquías](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class)de clases.
- **Reglas de simultaneidad** Una sola regla, que detecta objetos de protección mal declarados. Para obtener más información, consulte las [instrucciones relacionadas con la simultaneidad](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency).
- **Reglas de declaración** Un par de reglas de las [instrucciones](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) de las interfaces que se centran en cómo se declaran las variables globales.
- **Reglas de función** Dos comprobaciones que ayudan en la adopción del especificador de `noexcept`. Esta es una parte de las instrucciones para el [diseño y la implementación de funciones claras](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions).
- **Reglas de puntero compartidas** Como parte del cumplimiento de las directrices de [Administración de recursos](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) , se han agregado algunas reglas específicas de cómo se pasan los punteros compartidos a funciones o se usan de forma local.
- **Reglas de estilo** Una comprobación simple pero importante, que prohíbe el uso de [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto). Este es el primer paso para mejorar el estilo de codificación y el uso de expresiones e C++instrucciones en.

**Visual Studio 2017 versión 15.6**:

- **Reglas aritméticas** Reglas para detectar el [desbordamiento](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow) aritmético, las [operaciones sin firmar](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned) y la [manipulación de bits](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative) con signo.

Puede elegir limitar las advertencias a solo uno o algunos de los grupos. Los conjuntos de reglas predeterminadas nativas C++ **y** **mínimas nativas** incluyen reglas de comprobación básicas además de otras comprobaciones anticipadas. Para ver los conjuntos de reglas disponibles, abra el cuadro de diálogo Propiedades del proyecto, seleccione **código Analysis\General**, abra la lista desplegable en el cuadro combinado de **conjuntos de reglas** y **Elija elegir varios conjuntos de reglas**. Para obtener más información sobre el uso de conjuntos de reglas en Visual Studio, consulte [usar conjuntos de reglas para agrupar reglas de análisis de código](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Macros

El C++ comprobador de directrices básicas incluye un archivo de encabezado, que define macros que facilitan la tarea de suprimir todas las categorías de advertencias en el código:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Estas macros se corresponden con los conjuntos de reglas y se expanden en una lista de números de advertencia separados por espacios. Mediante el uso de las construcciones pragma adecuadas, puede configurar el conjunto efectivo de reglas que es interesante para un proyecto o una sección de código. En el ejemplo siguiente, el análisis de código solo advierte sobre los modificadores de constantes que faltan:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Atributos

El compilador de Microsoft C++ tiene una compatibilidad limitada para el atributo suprimir GSL. Se puede usar para suprimir las advertencias en las instrucciones de expresión y de bloque dentro de una función.

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
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

## <a name="suppress-analysis-by-using-command-line-options"></a>Suprimir análisis mediante opciones de la línea de comandos

En lugar de #pragmas, puede usar las opciones de la línea de comandos en la página de propiedades del archivo para suprimir las advertencias de un proyecto o de un solo archivo. Por ejemplo, para deshabilitar la advertencia 26400 para un archivo:

1. Haga clic con el botón derecho en el archivo en **Explorador de soluciones**

2. Elegir **propiedades | C/C++| Línea de comandos**

3. En la ventana **opciones adicionales** , agregue `/wd26400`.

Puede usar la opción de línea de comandos para deshabilitar temporalmente todo el análisis de código de un archivo especificando `/analyze-`. Esto produce una advertencia *D9025 invalidando '/Analyze ' con '/Analyze-'* , que le recuerda que vuelva a habilitar el análisis de código más adelante.

## <a name="corecheck_per_file"></a>Habilitación C++ del comprobador de directrices básicas en archivos de proyecto específicos

A veces puede resultar útil realizar análisis de código centrado y seguir usando el IDE de Visual Studio. El escenario de ejemplo siguiente se puede usar para proyectos grandes con el fin de ahorrar tiempo de compilación y facilitar el filtrado de los resultados:

1. En el shell de comandos, establezca las variables de entorno `esp.extension` y `esp.annotationbuildlevel`.
2. Para heredar estas variables, abra Visual Studio desde el shell de comandos.
3. Cargue el proyecto y abra sus propiedades.
4. Habilitar el análisis de código, elegir los conjuntos de reglas adecuados, pero no habilitar las extensiones de análisis de código.
5. Vaya al archivo que desea analizar con el C++ comprobador de directrices básicas y abra sus propiedades.
6. Elija **las opcionesC++de la línea C/\Command** y agregue `/analyze:plugin EspXEngine.dll`
7. Deshabilitar el uso del encabezado precompilado (**encabezados de C/C++\Precompiled**). Esto es necesario porque el motor de extensiones puede intentar leer su información interna del encabezado precompilado (PCH); Si el PCH se compila con las opciones predeterminadas del proyecto, no será compatible.
8. Recompile el proyecto. Las comprobaciones de PREfast comunes deben ejecutarse en todos los archivos. Dado que C++ el comprobador de directrices básicas no está habilitado de forma predeterminada, solo se debe ejecutar en el archivo configurado para usarlo.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Cómo usar el C++ comprobador de directrices básicas fuera de Visual Studio

Puede usar las comprobaciones de las C++ instrucciones básicas en compilaciones automatizadas.

### <a name="msbuild"></a>MSBuild
El comprobador de análisis de código nativo (PREfast) se integra en el entorno de MSBuild mediante archivos de destinos personalizados. Puede usar las propiedades del proyecto para habilitarla y agregar el C++ comprobador de directrices básicas (que se basa en PREfast):

```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

Asegúrese de agregar estas propiedades antes de la importación del archivo Microsoft. cpp. targets. Puede seleccionar conjuntos de reglas específicos o crear un conjunto de reglas personalizado o utilizar el conjunto de reglas predeterminado que incluye otras comprobaciones anticipadas.

Solo puede ejecutar el C++ comprobador de núcleo en los archivos especificados con el mismo enfoque [descrito anteriormente](#corecheck_per_file), pero con los archivos de MSBuild. Las variables de entorno se pueden establecer mediante el elemento `BuildMacro`:

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

Si no desea modificar el archivo del proyecto, puede pasar propiedades en la línea de comandos:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Proyectos que no son de MSBuild

Si usa un sistema de compilación que no se basa en MSBuild, puede ejecutar el comprobador, pero debe familiarizarse con algunos aspectos internos de la configuración del motor de análisis de código. No se garantiza que estos elementos internos se admitan en el futuro.

Tiene que establecer algunas variables de entorno y usar las opciones de línea de comandos adecuadas para el compilador. Es mejor trabajar en el entorno de "símbolo del sistema de herramientas nativas" para que no tenga que buscar rutas de acceso específicas para el compilador, directorios de inclusión, etc.

1. **Variables de entorno**
   - `set esp.extensions=cppcorecheck.dll` esto indica al motor que cargue el C++ módulo Core Guidelines.
   - `set esp.annotationbuildlevel=ignore` Esto deshabilita la lógica que procesa las anotaciones de SAL. Las anotaciones no afectan al análisis de código C++ en el comprobador de directrices básicas, pero su procesamiento lleva tiempo (a veces una hora larga). Esta configuración es opcional, pero se recomienda encarecidamente.
   - `set caexcludepath=%include%` es muy recomendable deshabilitar las advertencias que se activan en los encabezados estándar. Aquí puede agregar más rutas de acceso, por ejemplo, la ruta de acceso a los encabezados comunes del proyecto.
2. **Opciones de la línea de comandos**
   - `/analyze` habilita el análisis de código (considere usar también/Analyze: Only y/Analyze: Quiet).
   - `/analyze:plugin EspXEngine.dll` esta opción carga el motor de extensiones de análisis de código en la velocidad rápida. Este motor, a su vez, carga C++ el comprobador de directrices básicas.

## <a name="use-the-guideline-support-library"></a>Usar la biblioteca de compatibilidad de directrices
La biblioteca de compatibilidad de instrucciones está diseñada para ayudarle a seguir las directrices básicas. GSL incluye definiciones que permiten reemplazar construcciones propensas a errores por alternativas más seguras. Por ejemplo, puede reemplazar un par `T*, length` de parámetros con el tipo `span<T>`. GSL está disponible en [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl). La biblioteca es de código abierto, por lo que puede ver los orígenes, hacer comentarios o contribuir. El proyecto se puede encontrar en [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).

## <a name="vs2015_corecheck"></a>Usar las C++ directrices de comprobación básica en proyectos de Visual Studio 2015

Si usa Visual Studio 2015, los conjuntos C++ de reglas de análisis de código de comprobación básica no se instalan de forma predeterminada. Debe realizar algunos pasos adicionales para poder habilitar las C++ herramientas de análisis de código de comprobación básica en Visual Studio 2015. Microsoft proporciona compatibilidad con los proyectos de Visual Studio 2015 mediante un paquete Nuget. El paquete se denomina Microsoft. CppCoreCheck y está disponible en [http://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck). Este paquete requiere que haya al menos Visual Studio 2015 con Update 1 instalado.

El paquete también instala otro paquete como una dependencia, una biblioteca de compatibilidad de instrucciones solo de encabezado (GSL). GSL también está disponible en GitHub en [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).

Debido a la forma en que se cargan las reglas de análisis de código, debe instalar el paquete NuGet Microsoft C++ . CppCoreCheck en cada proyecto que desee comprobar en Visual Studio 2015.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Para agregar el paquete Microsoft. CppCoreCheck al proyecto en Visual Studio 2015

1. En **Explorador de soluciones**, haga clic con el botón derecho para abrir el menú contextual del proyecto en la solución a la que desea agregar el paquete. Elija **administrar paquetes Nuget** para abrir el **Administrador de paquetes Nuget**.

2. En la ventana **Administrador de paquetes NuGet** , busque Microsoft. CppCoreCheck.

    ![La ventana Administrador de paquetes Nuget muestra el paquete CppCoreCheck](../code-quality/media/cppcorecheck_nuget_window.png)

3. Seleccione el paquete Microsoft. CppCoreCheck y, a continuación, elija el botón **instalar** para agregar las reglas al proyecto.

   El paquete NuGet agrega un archivo MSBuild *. targets* adicional al proyecto que se invoca cuando se habilita el análisis de código en el proyecto. Este archivo *. targets* agrega C++ las reglas de comprobación básicas como extensión adicional a la herramienta de análisis de código de Visual Studio. Una vez instalado el paquete, puede usar el cuadro de diálogo páginas de propiedades para habilitar o deshabilitar las reglas publicadas y experimentales.

## <a name="see-also"></a>Vea también

- [Referencia de C++ Visual Studio Core check](code-analysis-for-cpp-corecheck.md)
