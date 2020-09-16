---
title: Opciones de la línea de comandos para VSTest.Console.exe
ms.date: 07/17/2020
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 875af363cbd85f8667d56a33cf7646ac2a9da429
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037021"
---
# <a name="vstestconsoleexe-command-line-options"></a>Opciones de la línea de comandos para VSTest.Console.exe

*VSTest.Console.exe* es la herramienta de línea de comandos para ejecutar pruebas. Puede especificar varias opciones en cualquier orden en la línea de comandos. Estas opciones se muestran en [Opciones generales de la línea de comandos](#general-command-line-options).

> [!NOTE]
> El adaptador de MSTest de Visual Studio también funciona en modo heredado (lo que equivale a ejecutar pruebas con *mstest.exe*) por motivos de compatibilidad. En el modo heredado no puede aprovechar la característica TestCaseFilter. El adaptador puede cambiar al modo heredado cuando se especifica un archivo *testsettings*, **forcelegacymode** se establece en **true** en un archivo *runsettings* o se usan atributos como **HostType**.
>
> Para ejecutar pruebas automatizadas en un equipo basado en la arquitectura ARM, debe usar *VSTest.Console.exe*.

Abra un [Símbolo del sistema para desarrolladores](/dotnet/framework/tools/developer-command-prompt-for-vs) para usar la herramienta de línea de comandos. También encontrará la herramienta en *%Archivos de programa(x86)%\Microsoft Visual Studio\\<versión\>\\<edición\>\common7\ide\CommonExtensions\\<Plataforma | Microsoft>* .

## <a name="general-command-line-options"></a>Opciones generales de la línea de comandos

En la siguiente tabla se muestran todas las opciones de *VSTest.Console.exe* junto con una breve descripción. Puede ver un resumen similar si escribe `VSTest.Console/?` en una línea de comandos.

| Opción | Descripción |
|---|---|
|**[*nombres de archivos de prueba*]**|Ejecuta pruebas desde los archivos especificados. Separe varios nombres de archivos de prueba con espacios.<br />Ejemplos: `mytestproject.dll`, `mytestproject.dll myothertestproject.exe`|
|**/Settings:[*nombre de archivo*]**|Ejecuta pruebas con opciones adicionales, como recolectores de datos. Para obtener más información, vea [Configuración de pruebas unitarias con un archivo .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).<br />Ejemplo: `/Settings:local.runsettings`|
|**/Tests:[*nombre de prueba*]**|Ejecuta pruebas con nombres que incluyen los valores proporcionados. Para proporcionar varios valores, deberá separarlos por comas.<br />Ejemplo: `/Tests:TestMethod1,testMethod2`<br />La opción de línea de comandos **/Tests** no se puede usar con la opción de línea de comandos **/TestCaseFilter**.|
|**/Parallel**|Especifica que las pruebas se ejecutan en paralelo. De forma predeterminada, se pueden usar todos los núcleos disponibles en la máquina. Puede configurar el número de núcleos que se van a usar en un archivo de configuración.|
|**/Enablecodecoverage**|Habilita el adaptador de diagnóstico de datos CodeCoverage en la serie de pruebas.<br />Se usa la configuración predeterminada si no se especifica mediante un archivo de configuración.|
|**/InIsolation**|Ejecuta las pruebas en un proceso aislado.<br />Con este aislamiento, es menos probable que el proceso *vstest.console.exe* se detenga por un error de las pruebas, aunque es posible que las pruebas se ejecuten más despacio.|
|**/UseVsixExtensions**|Esta opción hace que el proceso *vstest.console.exe* use u omita las extensiones VSIX instaladas (si procede) en la serie de pruebas.<br />Esta opción está en desuso. A partir de la siguiente versión principal de Visual Studio, esta opción puede desaparecer. Use extensiones disponibles como paquete NuGet.<br />Ejemplo: `/UseVsixExtensions:true`|
|**/TestAdapterPath:[*ruta*]**|Obliga al proceso *vstest.console.exe* a usar adaptadores de prueba personalizados de una ruta de acceso especificada (si los hubiera) en la serie de pruebas.<br />Ejemplo: `/TestAdapterPath:[pathToCustomAdapters]`|
|**/Platform:[*tipo de plataforma*]**|Arquitectura de la plataforma de destino que se usará para la ejecución de pruebas.<br />Los valores válidos son x86, x64 y ARM.|
|**/Framework: [*versión de Framework*]**|Establezca como destino la versión de .NET que se va a usar para la ejecución de pruebas.<br />Algunos valores de ejemplo son `Framework35`, `Framework40`, `Framework45`, `FrameworkUap10` o `.NETCoreApp,Version=v1.1`.<br />TargetFrameworkAttribute se usa para detectar automáticamente esta opción desde el ensamblado y se establece de forma predeterminada en `Framework40` cuando el atributo no está presente. Debe especificar esta opción explícitamente si quita [TargetFrameworkAttribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) de los ensamblados de .NET Core.<br />Si la plataforma de destino se especifica como **Framework35**, las pruebas se ejecutan en "modo de compatibilidad" de CLR 4.0.<br />Ejemplo: `/Framework:framework40`|
|**/TestCaseFilter:[*expresión*]**|Ejecuta pruebas que coinciden con la expresión dada.<br /><Expression\> tiene el formato <property\>=<value\>[\|<Expression\>].<br />Ejemplo: `/TestCaseFilter:"Priority=1"`<br />Ejemplo: `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />La opción de línea de comandos **/TestCaseFilter** no se puede usar con la opción de línea de comandos **/Tests**. <br />Para obtener información sobre cómo crear y usar expresiones, vea [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md) (Filtro TestCase).|
|**/?**|Muestra información de uso.|
|**/Logger:[*uri o nombre descriptivo*]**|Especifica un registrador para resultados de pruebas. Especifique el parámetro varias veces para habilitar varios registradores.<br />Ejemplo: Para registrar resultados en un archivo de resultados de pruebas de Visual Studio (TRX), utilice<br />**/Logger:trx**<br />**[;LogFileName=\<Defaults to unique file name>]**|
|**/ListTests:[*nombre de archivo*]**|Muestra las pruebas detectadas del contenedor de pruebas especificado.|
|**/ListDiscoverers**|Muestra los programas de detección de pruebas instalados.|
|**/ListExecutors**|Muestra los programas de ejecución de pruebas instalados.|
|**/ListLoggers**|Muestra los registradores de pruebas instalados.|
|**/ListSettingsProviders**|Muestra los proveedores de configuración de pruebas instalados.|
|**/Blame**|Ejecuta las pruebas en el modo de culpabilidad. Esta opción es útil para aislar las pruebas problemáticas que hacen que el host de prueba se bloquee. Cuando se detecta un bloqueo, crea un archivo de secuencia en `TestResults/<Guid>/<Guid>_Sequence.xml` que captura el orden de las pruebas ejecutadas antes del bloqueo. Para más información, vea [Recopilador de datos de Blame](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/Diag:[*nombre de archivo*]**|Escribe registros de seguimiento de diagnóstico en el archivo especificado.|
|**/ResultsDirectory:[*ruta de acceso*]**|Si no existe, el directorio de los resultados de la prueba se creará en la ruta de acceso especificada.<br />Ejemplo: `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId:[*IdentificadorProcesoPrincipal*]**|Identificador del proceso principal responsable de iniciar el proceso actual.|
|**/Port:[*puerto*]**|El puerto para la conexión de socket y la recepción de mensajes de eventos.|
|**/Collect:[*dataCollector friendlyName*]**|Habilita el recopilador de datos para la ejecución de pruebas. [Más información](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md).|

> [!TIP]
> Las opciones y los valores no distinguen mayúsculas de minúsculas.

## <a name="examples"></a>Ejemplos

La sintaxis para ejecutar *vstest.console.exe* es:

`vstest.console.exe [TestFileNames] [Options]`

El siguiente comando ejecuta *vstest.console.exe* para la biblioteca de pruebas *myTestProject.dll*:

```cmd
vstest.console.exe myTestProject.dll
```

El siguiente comando ejecuta *vstest.console.exe* con varios archivos de prueba. Separe los nombres de archivos de prueba con espacios:

```cmd
vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

El siguiente comando ejecuta *vstest.console.exe* con varias opciones. Ejecuta las pruebas en el archivo *myTestFile.dll* en un proceso aislado y usa la configuración especificada en el archivo *Local.RunSettings*. Además, solo ejecuta las pruebas marcadas "Prioridad=1" y registra los resultados en un archivo *.trx*.

```cmd
vstest.console.exe myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```

El siguiente comando ejecuta *vstest.console.exe* con la opción `/blame` para la biblioteca de pruebas *myTestFile.dll*:

```cmd
vstest.console.exe myTestFile.dll /blame
```

Si el host de prueba se bloquea, se genera el archivo *sequence.xml*, que contiene los nombres completos de las pruebas en su secuencia de ejecución hasta (e incluyendo) la prueba específica que se estaba ejecutando en el momento del bloqueo.

Si no hay ningún bloqueo del host de prueba, el archivo *sequence.xml* no se generará.

Ejemplo de un archivo *sequence.xml* generado: 

```xml
<?xml version="1.0"?>
<TestSequence>
  <Test Name="TestProject.UnitTest1.TestMethodB" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
  <Test Name="TestProject.UnitTest1.TestMethodA" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
</TestSequence>
```