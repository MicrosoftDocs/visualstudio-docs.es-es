---
title: Usar los comprobadores de directrices de núcleo de C++
ms.date: 11/04/2016
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
dev_langs:
- CPP
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 7f1ec5df06cbe24008f0506b838c3743a572ea5b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="using-the-c-core-guidelines-checkers"></a>Usar los comprobadores de directrices de núcleo de C++
Las directrices de núcleo de C++ son un conjunto portátil de directrices, reglas y procedimientos recomendados acerca de cómo escribir código en C++ creados por los diseñadores y los expertos en C++. Visual Studio admite actualmente un subconjunto de estas reglas como parte de sus herramientas de análisis de código de C++. Los comprobadores de la directriz principal se instalan de forma predeterminada en Visual Studio de 2017 y se [disponible como un paquete de NuGet para Visual Studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>El proyecto de directrices de núcleo de C++
 Creado por Bjarne Stroustrup etc., las instrucciones de núcleo de C++ son una guía para utilizar C++ moderno de forma segura y eficaz. Céntrese en las directrices de seguridad de tipos estáticos y seguridad de recursos. Identificar formas de eliminar o minimizar las partes más propensos a errores del lenguaje y sugieren cómo hacer que el código sea más sencillo y más eficiente de forma confiable. Estas instrucciones se mantienen por la base de C++ estándar. Para obtener más información, consulte la documentación, [C++ Core directrices](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)y tener acceso a los archivos de proyecto de la documentación de directrices de núcleo de C++ en [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Habilitar las instrucciones de comprobación de núcleo de C++ en el análisis de código
 Puede habilitar análisis de código en el proyecto seleccionando la **Habilitar análisis de código al compilar** casilla de verificación en la **análisis de código** sección de la **páginas de propiedades** cuadro de diálogo para el proyecto.

 ![Página de propiedades de configuración General de análisis de código](../code-quality/media/cppcorecheck_codeanalysis_general.png "CPPCoreCheck_CodeAnalysis_General")

 Las reglas de comprobación de núcleo de C++ son extensiones para los conjuntos de reglas predeterminado que se ejecutan cuando se habilita el análisis de código. Dado que las reglas de comprobación de núcleo de C++ están en desarrollo, algunas reglas están bien consolidadas y algunos pueden no estar listos para su uso en todo el código, pero todavía pueden ser informativos. Las reglas se dividen en dos grupos: publicadas y experimental. Puede elegir si desea ejecutar las reglas publicadas o experimental en las propiedades del proyecto.

 ![Página de propiedades de configuración de las extensiones de análisis de código](../code-quality/media/cppcorecheck_codeanalysis_extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")

 Para habilitar o deshabilitar los conjuntos de reglas de comprobación de núcleo de C++, abra el **páginas de propiedades** cuadro de diálogo para el proyecto. En **propiedades de configuración**, expanda **análisis de código**, **extensiones**. En la lista desplegable junto al control **habilitar C++ Core comprobar (lanzamiento)** o **habilitar C++ Core comprobar (Experimental)**, elija **Sí** o **No**. Elija **Aceptar** o **aplicar** para guardar los cambios.

## <a name="examples"></a>Ejemplos
 Este es un ejemplo de algunos de los problemas que pueden encontrar las reglas de comprobación de núcleo de C++:

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

 En este ejemplo se muestra algunas de las advertencias que pueden encontrar las reglas de comprobación de núcleo de C++:

-   C26494 es regla Type.5: siempre inicializar un objeto.

-   C26485 es regla Bounds.3: ningún decadencia de matriz de puntero.

-   C26481 es regla Bounds.1: no utilizar aritmética de punteros. Utilice `span` en su lugar.

 Si los rulesets de análisis de código de C++ Core comprobará estén instalados y habilitados cuando se compila este código, las dos primeras advertencias son salida, pero se suprime el tercer argumento. Este es el resultado de compilación desde el código de ejemplo:

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Las directrices de núcleo de C++ sirven para ayudarle a escribir código mejor y más seguro. Sin embargo, si tiene una instancia que no debe aplicarse una regla o un perfil, es fácil suprimir directamente en el código. Puede usar el `gsl::suppress` atributo para impedir que C++ Core comprobará detectar e informes cualquier infracción de una regla en el siguiente bloque de código. Puede marcar las instrucciones individuales para suprimir reglas específicas. Incluso puede suprimir el perfil completo de límites escribiendo `[[gsl::suppress(bounds)]]` sin necesidad de incluir un número de regla concreta.

## <a name="supported-rule-sets"></a>Admite conjuntos de reglas
Cuando se agregan nuevas reglas para el Comprobador de directrices de núcleo de C++, puede aumentar el número de advertencias que se generan para el código existente. Puede utilizar conjuntos de reglas predefinidas para filtrar los tipos de reglas para habilitar.
Temas de referencia para la mayoría de las reglas están bajo [comprobar referencia de C++ básica de Visual Studio](code-analysis-for-cpp-corecheck.md).

A partir de Visual Studio 2017 versión 15.3, los conjuntos de reglas compatibles son:
  - **Reglas de puntero de propietario** aplicar [comprueba de administración de recursos relacionados con propietario<T> de las directrices de núcleo de C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Reglas constantes** aplicar [relacionados con const comprobaciones de las directrices de núcleo de C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

  - **Reglas de puntero sin formato** aplicar [administración de recursos comprueba relacionados a raw punteros de las directrices de núcleo de C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Reglas de puntero único** aplicar [comprueba de administración de recursos relacionados con los tipos con la semántica del puntero único de las directrices de núcleo de C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Delimita reglas** exigir la [delimita el perfil de las directrices de núcleo de C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

  - **Reglas de tipos de** exigir la [tipo de perfil de las directrices de núcleo de C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

  **Versión 15.5 de Visual Studio 2017**:
  - **Clase reglas** varias reglas que se centran en el uso correcto de métodos especiales y especificaciones virtuales. Se trata de un subconjunto de los controles que se recomienda para [las clases y las jerarquías de clases](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class).
  - **Las reglas de simultaneidad** una única regla, que detecta los objetos declarados mal protección. Para obtener más información, consulte [instrucciones relacionados con la simultaneidad](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency).
  - **Reglas de la declaración** un par de reglas a partir de la [interfaces directrices](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) que se centran en las variables globales de cómo se declaran.
  - **Función reglas** dos comprobaciones que simplifican la adopción de la `noexcept` especificador. Se trata de una parte de las instrucciones para [borrar función diseño e implementación](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions).
  - **Reglas de puntero compartido** como parte de [administración de recursos](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) cumplimiento de las directrices, agregamos unas reglas específicas de punteros compartidos cómo se pasan a las funciones o los utiliza localmente.
  - **Reglas de estilo** una comprobación simple pero importante, que prohíbe el uso de [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto). Este es el primer paso en la mejora de la codificación de estilo y el uso de expresiones e instrucciones en C++.

  **Visual Studio 2017 versión 15.6**:
  - **Reglas aritméticas** reglas para detectar operaciones aritméticas [desbordamiento](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow), [firmadas-sin firmar operations](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned) y [manipulación de bits](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative).


 Puede limitar las advertencias para uno o algunos de los grupos. El **mínimo nativo** y **recomienda nativo** regla conjuntos incluyen reglas de comprobación de núcleo de C++ además de otras comprobaciones de PREfast. Para ver los contadores a conjuntos de reglas, abra el cuadro de diálogo de propiedades del proyecto, seleccione **código Analysis\General**, abra la lista desplegable en el **conjuntos de reglas** cuadro combinado y selección **elegir varios conjuntos de reglas** . Para obtener más información sobre el uso de conjuntos de reglas en Visual Studio, vea [utilizando conjuntos de reglas para agrupar reglas de análisis de código](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Macros
 El Comprobador de directrices de núcleo de C++ incluye un archivo de encabezado que define macros que resulte más fácil suprimir todas las categorías de advertencias en el código:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Estas macros corresponden a los conjuntos de reglas y expandir en una lista de números de advertencia separados por espacios. Mediante el uso de las construcciones de pragma adecuado, puede configurar el conjunto efectivo de reglas que sean de interés para un proyecto o una sección de código. En el ejemplo siguiente, el análisis de código se advierte solo sobre falta modificadores constantes:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Atributos
 El compilador de Microsoft Visual C++ tiene una compatibilidad limitada para la GSL suprimir el atributo. Se puede utilizar para suprimir las advertencias de expresión y las instrucciones de bloques dentro de una función.

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

## <a name="suppressing-analysis-by-using-command-line-options"></a>Supresión de análisis con las opciones de línea de comandos
 En lugar de #pragmas, puede utilizar opciones de línea de comandos en la página de propiedades del archivo para suprimir las advertencias para un proyecto o un único archivo. Por ejemplo, para deshabilitar la advertencia 26400 para un archivo:

 1) Haga clic en el archivo en **el Explorador de soluciones**

 2) Elija **propiedades | C / C ++ | Línea de comandos**

 3) En el **opciones adicionales** ventana, agregar `/wd26400`.

 Puede usar la opción de línea de comandos para deshabilitar temporalmente todos los análisis de código para un archivo mediante la especificación de `/analyze-`. Esto genera la advertencia *D9025 reemplazar '/ analyze' con ' / analyze-'*, que le recuerda que debe volver a habilitar análisis de código más adelante.

 ## <a name="corecheck_per_file"></a> Habilitar el Comprobador de instrucciones de C++ principales en los archivos de proyecto específico
A veces puede ser útil realizar centrado de análisis de código y todavía el uso del IDE de Visual Studio. El siguiente escenario de ejemplo puede usarse para los proyectos grandes para ahorrar tiempo de compilación y resulte más fácil a los resultados del filtro:

1.  En el shell de comandos establece la `esp.extension` y `esp.annotationbuildlevel` las variables de entorno.
2.  Para que hereden estas variables, inicie Visual Studio desde el shell de comandos.
3.  Cargar el proyecto y abra sus propiedades.
4.  Habilitar análisis de código, seleccionar los conjuntos de reglas adecuado, pero no habilita las extensiones de análisis de código.
5.  Vaya al archivo que desea analizar con el Comprobador de directrices de núcleo de C++ y abra sus propiedades.
6.  Elija **C / C ++ \Command opciones de la línea** y agregar `/analyze:plugin EspXEngine.dll`
7.  Deshabilitar el uso del encabezado precompilado (**C / C ++ \Precompiled encabezados**). Esto es necesario porque el motor de extensiones puede intentar leer su información interna del encabezado precompilado (PCH); Si el encabezado Precompilado se compila con las opciones de proyecto predeterminadas, no serán compatible.
8.  Recompile el proyecto. Deben ejecutar las comprobaciones de PREFast común en todos los archivos. Dado que el Comprobador de directrices de núcleo de C++ no está habilitado de forma predeterminada, solo debe ejecutarse en el archivo que está configurado para utilizarlo.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Cómo utilizar el Comprobador de instrucciones de C++ Core fuera de Visual Studio
Puede usar las comprobaciones de directrices de núcleo de C++ en compilaciones automatizadas.

### <a name="msbuild"></a>MSBuild
 El Comprobador de análisis de código nativo (PREfast) se integra en el entorno de MSBuild por archivos de destino personalizados. Puede utilizar propiedades de proyecto para habilitarla y agregar el Comprobador de directrices de núcleo de C++ (que se basa en PREfast):

 ```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```
Asegúrese de que agregar estas propiedades antes de importar el archivo Microsoft.Cpp.targets. Puede elegir conjuntos de reglas específicas o crear un conjunto de reglas personalizado o usar el conjunto de reglas predeterminado que incluye otras comprobaciones de PREfast.

Puede ejecutar el Comprobador de núcleo de C++ solo en los archivos especificados utilizando el mismo enfoque que [descritos anteriormente](#corecheck_per_file), pero con archivos de MSBuild. Las variables de entorno se pueden establecer mediante el `BuildMacro` elemento:

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

### <a name="non-msbuild-projects"></a>Proyectos de MSBuild no
Si utiliza un sistema de compilación que no se basa en MSBuild todavía puede ejecutar el Comprobador, pero debe familiarizarse con algunos elementos internos de la configuración del motor de análisis de código. No se garantiza que estos elementos internos se admite en el futuro.

Tendrá que establecer algunas variables de entorno y usar las opciones de línea de comandos apropiadas para que el compilador. Es mejor trabajar en el entorno de "línea de comandos de herramientas nativo" para que no tiene que buscar rutas de acceso específicas para el compilador, incluya directorios, etcetera.

1.  **Variables de entorno**
  - `set esp.extensions=cppcorecheck.dll` Esto indica al motor para cargar el módulo de directrices de núcleo de C++.
  - `set esp.annotationbuildlevel=ignore` Esto deshabilita la lógica que procesa las anotaciones de SAL. Las anotaciones no afectan a análisis de código en el Comprobador de directrices de núcleo de C++, aunque su procesamiento tarda (a veces, una hora larga). Este valor es opcional, pero muy recomendado.
  - `set caexcludepath=%include%` Se recomienda que deshabilite las advertencias que se activan en encabezados estándar. Puede agregar más rutas de acceso aquí, por ejemplo la ruta de acceso a los encabezados comunes en el proyecto.
2.  **Opciones de línea de comandos**
  - `/analyze`  Habilita el análisis de código (tenga en cuenta también usa / analyze: solo y / analyze: silencioso).
  - `/analyze:plugin EspXEngine.dll` Esta opción carga el motor de extensiones de análisis de código en el PREfast. Este motor, a su vez, carga el Comprobador de directrices de núcleo de C++.



## <a name="use-the-guideline-support-library"></a>Usar la biblioteca de compatibilidad de la regla
 La biblioteca de compatibilidad de la regla está diseñada para ayudar a seguir las directrices de núcleo. El GSL incluye las definiciones que permiten sustituir construcciones propensas a errores con alternativas más seguras. Por ejemplo, puede reemplazar un `T*, length` par de parámetros con el `span<T>` tipo. Está disponible en la GSL [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). La biblioteca es código abierto, por lo que puede ver los orígenes, hacer comentarios o contribuir. El proyecto se encuentra en [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

 ## <a name="vs2015_corecheck"></a> Utilice las instrucciones de comprobación de núcleo de C++ en proyectos de Visual Studio 2015
  Si usa Visual Studio 2015, los conjuntos de reglas de análisis de código de C++ Core comprobará no se instalan de forma predeterminada. Debe realizar algunos pasos adicionales antes de poder habilitar las herramientas de análisis de código de comprobación de núcleo de C++ en Visual Studio 2015. Microsoft proporciona compatibilidad para los proyectos de Visual Studio 2015 con un paquete de Nuget. El paquete se denomina Microsoft.CppCoreCheck y está disponible en [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Este paquete requiere que tenga al menos Visual Studio 2015 con Update 1 instalado.

 El paquete también instala otro paquete como una dependencia, un solo encabezado directriz soporte técnico de biblioteca (GSL). El GSL también está disponible en GitHub en [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

 Debido al modo en que se cargan las reglas de análisis de código, debe instalar el paquete de Microsoft.CppCoreCheck NuGet en cada proyecto de C++ que se va a comprobar en Visual Studio 2015.

#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Para agregar el paquete de Microsoft.CppCoreCheck al proyecto en Visual Studio 2015

1.  En **el Explorador de soluciones**, menú contextual para abrir el menú contextual del proyecto en la solución que desea agregar el paquete. Elija **administrar paquetes de NuGet** para abrir el **Administrador de paquetes de NuGet**.

2.  En el **Administrador de paquetes de NuGet** ventana, busque Microsoft.CppCoreCheck.

     ![Ventana del Administrador de paquetes de NuGet muestra paquete CppCoreCheck](../code-quality/media/cppcorecheck_nuget_window.PNG "CPPCoreCheck_Nuget_Window")

3.  Seleccione el paquete de Microsoft.CppCoreCheck y, a continuación, elija la **instalar** botón para agregar las reglas a su proyecto.

 El paquete NuGet agrega un MSBuild adicional *.targets* archivo al proyecto que se invoca cuando se habilita el análisis de código en el proyecto. Esto *.targets* archivo agrega las reglas de comprobación de núcleo de C++ como una extensión adicional a la herramienta de análisis de código de Visual Studio. Cuando se instala el paquete, puede usar el cuadro de diálogo páginas de propiedades para habilitar o deshabilitar las reglas publicadas y experimental.

## <a name="see-also"></a>Vea también
[Referencia de Visual Studio C++ Core comprobación](code-analysis-for-cpp-corecheck.md).

