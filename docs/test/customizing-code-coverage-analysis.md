---
title: Personalizar el análisis de cobertura de código
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 8749cd7757796a1b716b1ac9db086d3155f94694
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965564"
---
# <a name="customize-code-coverage-analysis"></a>Personalizar el análisis de cobertura de código

De forma predeterminada, la cobertura de código analiza todos los ensamblados de la solución que se cargan durante las pruebas unitarias. Se recomienda usar este comportamiento de forma predeterminada, porque funciona bien la mayoría de los casos. Para obtener más información, vea [Usar cobertura de código para determinar la cantidad de código que se está probando](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Para excluir el código de prueba de los resultados de cobertura de código e incluir solo código de la aplicación, agregue el atributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> a la clase de prueba.

Para incluir ensamblados que no forman parte de la solución, obtenga los archivos *.pdb* para los ensamblados y cópielos en la misma carpeta que los archivos de ensamblado *.dll*.

## <a name="run-settings-file"></a>Archivo de parámetros de ejecución

Es el [archivo de parámetros de ejecución](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) que usan las herramientas de pruebas unitarias. La configuración avanzada de la cobertura de código se especifica en un archivo *.runsettings*.

Para personalizar la cobertura de código, siga estos pasos:

1. Agregue un archivo de parámetros de ejecución a la solución. En el **Explorador de soluciones**, en el menú contextual de la solución, seleccione **Agregar** > **Nuevo elemento** y seleccione **Archivo XML**. Guarde el archivo con un nombre como *CodeCoverage.runsettings*.

1. Agregue el contenido que se muestra en el archivo de ejemplo al final del artículo y después personalícelo de acuerdo con sus necesidades como se describe en las secciones siguientes.

1. Para seleccionar el archivo de parámetros de ejecución, en el menú **Prueba**, elija **Configuración de pruebas** > **Seleccionar archivo de configuración de pruebas**. Para especificar un archivo de parámetros de ejecución para ejecutar pruebas desde la línea de comandos o en un flujo de trabajo de compilación, vea [Configure unit tests by using a *.runsettings* file](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file) (Configurar pruebas unitarias utilizando el archivo .runsettings).

   Al seleccionar **Analizar cobertura de código**, la información de configuración se lee desde el archivo de parámetros de ejecución.

   > [!TIP]
   > Los anteriores resultados de cobertura de y colores de código no se ocultan automáticamente al ejecutar pruebas o actualizar el código.

Para desactivar y activar la configuración personalizada, anule la selección o seleccione el archivo en el menú **Prueba** > **Configuración de pruebas**.

![Menú de configuración de pruebas con archivo de configuración personalizado](../test/media/codecoverage-settingsfile.png)

### <a name="specify-symbol-search-paths"></a>Especificar rutas de búsqueda de símbolos

La cobertura de código requiere que haya símbolos (archivos *.pdb*) para los ensamblados. En el caso de los ensamblados compilados por su solución, los archivos de símbolos normalmente están presentes con los archivos binarios y la cobertura de código funciona automáticamente. Pero, en algunos casos, puede que desee incluir los ensamblados a los que se hace referencia en el análisis de cobertura de código. En esos casos, los archivos *.pdb* podrían no estar adyacentes a los archivos binarios pero puede especificar la ruta de búsqueda de símbolos en el archivo *.runsettings*.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> La resolución de símbolos puede tardar tiempo, especialmente al utilizar una ubicación de archivo remota con muchos ensamblados. Por tanto, considere la posibilidad de copiar los archivos *.pdb* en la misma ubicación local que los archivos binarios (*.dll* y *.exe*).

### <a name="exclude-and-include"></a>Excluir e incluir

Puede excluir los ensamblados especificados del análisis de cobertura de código. Por ejemplo:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

Como alternativa, puede especificar qué ensamblados deben incluirse. Este enfoque tiene la desventaja de que, cuando agrega más ensamblados a la solución, tiene que recordar agregarlos a la lista:

```xml
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

Si el campo **Incluir** está vacío, el procesamiento de cobertura de código incluye todos los ensamblados que se cargan y para los que se pueden encontrar archivos *.pdb*. La cobertura de código no incluye elementos que coinciden con una cláusula en una lista **Excluir**.

**Incluir** se procesa antes que **Excluir**.

### <a name="regular-expressions"></a>Expresiones regulares

Los nodos de inclusión y exclusión usan expresiones regulares. Para obtener más información, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md). Las expresiones regulares no son iguales que los caracteres comodín. En concreto:

- **.\\*** coincide con una cadena de caracteres cualquiera

- **\\.** coincide con un punto (".")

- **\\(   \\)** coincide con paréntesis "( )"

- **\\\\** coincide con el delimitador de ruta de acceso "\\"

- **^** coincide con el inicio de la cadena

- **$** coincide con el final de la cadena

Ninguna coincidencia distingue entre mayúsculas y minúsculas.

Por ejemplo:

```xml
<ModulePaths>
  <Include>
    <!-- Include all loaded .dll assemblies (but not .exe assemblies): -->
    <ModulePath>.*\.dll$</ModulePath>
  </Include>
  <Exclude>
    <!-- But exclude some assemblies: -->
    <ModulePath>.*\\Fabrikam\.MyTests1\.dll$</ModulePath>
    <!-- Exclude all file paths that contain "Temp": -->
    <ModulePath>.*Temp.*</ModulePath>
  </Exclude>
</ModulePaths>
```

> [!WARNING]
> Si hay un error en una expresión regular, como paréntesis sin caracteres de escape o sin su correspondiente pareja, el análisis de cobertura de código no se ejecutará.

### <a name="other-ways-to-include-or-exclude-elements"></a>Otras maneras de incluir o excluir elementos

- **ModulePath**: busca coincidencias con los ensamblados especificados por la ruta de acceso del ensamblado.

- **CompanyName**: busca coincidencias con los ensamblados por el atributo de **Compañía**.

- **PublicKeyToken**: busca coincidencias con los ensamblados firmados por el token de clave pública.

- **Source**: busca coincidencias con los elementos por el nombre de ruta de acceso del archivo de código fuente en el cual se definen.

- **Attribute**: busca coincidencias con los elementos en los que se asocia un atributo determinado. Especifique el nombre completo del atributo e incluya "Attribute" al final del nombre.

- **Function**: busca coincidencias con procedimientos, funciones o métodos por el nombre completo. Para buscar coincidencias con un nombre de función, la expresión regular debe coincidir con el nombre completo de la función, incluidos el espacio de nombres, el nombre de clase, el nombre de método y la lista de parámetros. Por ejemplo:

   ```csharp
   Fabrikam.Math.LocalMath.SquareRoot(double);
   ```

   ```cpp
   Fabrikam::Math::LocalMath::SquareRoot(double)
   ```

   ```xml
   <Functions>
     <Include>
       <!-- Include methods in the Fabrikam namespace: -->
       <Function>^Fabrikam\..*</Function>
       <!-- Include all methods named EqualTo: -->
       <Function>.*\.EqualTo\(.*</Function>
     </Include>
     <Exclude>
       <!-- Exclude methods in a class or namespace named UnitTest: -->
       <Function>.*\.UnitTest\..*</Function>
     </Exclude>
   </Functions>
   ```

## <a name="sample-runsettings-file"></a>Archivo de ejemplo .runsettings

Copie el código y edítelo para satisfacer sus necesidades.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
<!--
Additional paths to search for .pdb (symbol) files. Symbols must be found for modules to be instrumented.
If .pdb files are in the same folder as the .dll or .exe files, they are automatically found. Otherwise, specify them here.
Note that searching for symbols increases code coverage runtime. So keep this small and local.
-->
<!--
            <SymbolSearchPaths>
                   <Path>C:\Users\User\Documents\Visual Studio 2012\Projects\ProjectX\bin\Debug</Path>
                   <Path>\\mybuildshare\builds\ProjectX</Path>
            </SymbolSearchPaths>
-->

<!--
About include/exclude lists:
Empty "Include" clauses imply all; empty "Exclude" clauses imply none.
Each element in the list is a regular expression (ECMAScript syntax). See https://docs.microsoft.com/visualstudio/ide/using-regular-expressions-in-visual-studio.
An item must first match at least one entry in the include list to be included.
Included items must then not match any entries in the exclude list to remain included.
-->

            <!-- Match assembly file paths: -->
            <ModulePaths>
              <Include>
                <ModulePath>.*\.dll$</ModulePath>
                <ModulePath>.*\.exe$</ModulePath>
              </Include>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- Match fully qualified names of functions: -->
            <!-- (Use "\." to delimit namespaces in C# or Visual Basic, "::" in C++.)  -->
            <Functions>
              <Exclude>
                <Function>^Fabrikam\.UnitTest\..*</Function>
                <Function>^std::.*</Function>
                <Function>^ATL::.*</Function>
                <Function>.*::__GetTestMethodInfo.*</Function>
                <Function>^Microsoft::VisualStudio::CppCodeCoverageFramework::.*</Function>
                <Function>^Microsoft::VisualStudio::CppUnitTestFramework::.*</Function>
              </Exclude>
            </Functions>

            <!-- Match attributes on any code element: -->
            <Attributes>
              <Exclude>
                <!-- Don't forget "Attribute" at the end of the name -->
                <Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.DebuggerNonUserCodeAttribute$</Attribute>
                <Attribute>^System\.Runtime\.CompilerServices.CompilerGeneratedAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis.ExcludeFromCodeCoverageAttribute$</Attribute>
              </Exclude>
            </Attributes>

            <!-- Match the path of the source files in which each method is defined: -->
            <Sources>
              <Exclude>
                <Source>.*\\atlmfc\\.*</Source>
                <Source>.*\\vctools\\.*</Source>
                <Source>.*\\public\\sdk\\.*</Source>
                <Source>.*\\microsoft sdks\\.*</Source>
                <Source>.*\\vc\\include\\.*</Source>
              </Exclude>
            </Sources>

            <!-- Match the company name property in the assembly: -->
            <CompanyNames>
              <Exclude>
                <CompanyName>.*microsoft.*</CompanyName>
              </Exclude>
            </CompanyNames>

            <!-- Match the public key token of a signed assembly: -->
            <PublicKeyTokens>
              <!-- Exclude Visual Studio extensions: -->
              <Exclude>
                <PublicKeyToken>^B77A5C561934E089$</PublicKeyToken>
                <PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>
                <PublicKeyToken>^31BF3856AD364E35$</PublicKeyToken>
                <PublicKeyToken>^89845DCD8080CC91$</PublicKeyToken>
                <PublicKeyToken>^71E9BCE111E9429C$</PublicKeyToken>
                <PublicKeyToken>^8F50407C4E9E73B6$</PublicKeyToken>
                <PublicKeyToken>^E361AF139669C375$</PublicKeyToken>
              </Exclude>
            </PublicKeyTokens>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>Vea también

- [Configurar pruebas unitarias con un archivo de parámetros de ejecución](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Usar cobertura de código para determinar la cantidad de código que se va a probar](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)