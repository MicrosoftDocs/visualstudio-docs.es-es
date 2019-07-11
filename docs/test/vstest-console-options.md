---
title: Opciones de la línea de comandos para VSTest.Console.exe
ms.date: 07/12/2018
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: gewarren
author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eef81a2075f05acf8ea6ab8b42f77797425a3abd
ms.sourcegitcommit: 74c5360186731de07828764eb32ea1033a8c2275
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2019
ms.locfileid: "67559612"
---
# <a name="vstestconsoleexe-command-line-options"></a>Opciones de la línea de comandos para VSTest.Console.exe

*VSTest.Console.exe* es la herramienta de línea de comandos para ejecutar pruebas. Puede especificar varias opciones en cualquier orden en la línea de comandos. Estas opciones se muestran en [Opciones generales de la línea de comandos](#general-command-line-options).

> [!NOTE]
> El adaptador de MSTest de Visual Studio también funciona en modo heredado (lo que equivale a ejecutar pruebas con *mstest.exe*) por motivos de compatibilidad. En el modo heredado no puede aprovechar la característica TestCaseFilter. El adaptador puede cambiar al modo heredado cuando se especifica un archivo *testsettings*, **forcelegacymode** se establece en **true** en un archivo *runsettings* o se usan atributos como **HostType**.
>
> Para ejecutar pruebas automatizadas en un equipo basado en la arquitectura ARM, debe usar *VSTest.Console.exe*.

## <a name="general-command-line-options"></a>Opciones generales de la línea de comandos

En la siguiente tabla se muestran todas las opciones de *VSTest.Console.exe* junto con una breve descripción. Puede ver un resumen similar si escribe `VSTest.Console/?` en una línea de comandos.

| Opción | DESCRIPCIÓN |
|---|---|
|**[*nombres de archivos de prueba*]**|Ejecuta pruebas desde los archivos especificados. Separe varios nombres de archivos de prueba con espacios.<br />Ejemplos: `mytestproject.dll`, `mytestproject.dll myothertestproject.exe`|
|**/Settings:[*nombre de archivo*]**|Ejecuta pruebas con opciones adicionales, como recolectores de datos.<br />Ejemplo: `/Settings:Local.RunSettings`|
|**/Tests:[*nombre de prueba*]**|Ejecuta pruebas con nombres que incluyen los valores proporcionados. Para proporcionar varios valores, deberá separarlos por comas.<br />Ejemplo: `/Tests:TestMethod1,testMethod2`<br />La opción de línea de comandos **/Tests** no se puede usar con la opción de línea de comandos **/TestCaseFilter**.|
|**/Parallel**|Especifica que las pruebas se ejecutan en paralelo. De forma predeterminada, se pueden usar todos los núcleos disponibles en el equipo. El número de núcleos que se va a usar se puede configurar mediante un archivo de configuración.|
|**/Enablecodecoverage**|Habilita el adaptador de diagnóstico de datos CodeCoverage en la serie de pruebas.<br />Se usa la configuración predeterminada si no se especifica mediante un archivo de configuración.|
|**/InIsolation**|Ejecuta las pruebas en un proceso aislado.<br />Con este aislamiento, es menos probable que el proceso *vstest.console.exe* se detenga por un error de las pruebas, aunque es posible que las pruebas se ejecuten más despacio.|
|**/UseVsixExtensions**|Esta opción hace que el proceso *vstest.console.exe* use u omita las extensiones VSIX instaladas (si procede) en la serie de pruebas.<br />Esta opción está en desuso. A partir de la siguiente versión principal de Visual Studio, esta opción puede desaparecer. Use extensiones disponibles como paquete NuGet.<br />Ejemplo: `/UseVsixExtensions:true`|
|**/TestAdapterPath:[*ruta*]**|Obliga al proceso *vstest.console.exe* a usar adaptadores de prueba personalizados de una ruta de acceso especificada (si los hubiera) en la serie de pruebas.<br />Ejemplo: `/TestAdapterPath:[pathToCustomAdapters]`|
|**/Platform:[*tipo de plataforma*]**|Arquitectura de la plataforma de destino que se usará para la ejecución de pruebas.<br />Los valores válidos son x86, x64 y ARM.|
|**/Framework: [*versión de Framework*]**|Establezca como destino la versión de .NET que se va a usar para la ejecución de pruebas.<br />Los valores válidos son Framework35, Framework40, Framework45 y FrameworkUap10.<br />Si la plataforma de destino se especifica como **Framework35**, las pruebas se ejecutan en "modo de compatibilidad" de CLR 4.0.<br />Ejemplo: `/Framework:framework40`|
|**/TestCaseFilter:[*expresión*]**|Ejecuta pruebas que coinciden con la expresión dada.<br /><Expression\> tiene el formato <property\>=<value\>[\|<Expression\>].<br />Ejemplo: `/TestCaseFilter:"Priority=1"`<br />Ejemplo: `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />La opción de línea de comandos **/TestCaseFilter** no se puede usar con la opción de línea de comandos **/Tests**. <br />Para obtener información sobre cómo crear y usar expresiones, vea [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md) (Filtro TestCase).|
|**/?**|Muestra información de uso.|
|**/Logger:[*uri o nombre descriptivo*]**|Especifica un registrador para resultados de pruebas.<br />Ejemplo: Para registrar resultados en un archivo de resultados de pruebas (TRX) de Visual Studio, use **/Logger:trx**.<br />Ejemplo: Para publicar resultados de pruebas en Team Foundation Server, use TfsPublisher:<br />**/logger:TfsPublisher;**<br />**Collection=<url del proyecto\>;**<br />**BuildName=<nombre de compilación\>;**<br />**TeamProject=<nombre del proyecto\>;**<br />**[;Platform=\<Valor predeterminado "Cualquier CPU">]**<br />**[;Flavor=\<Valor predeterminado "Depurar">]**<br />**[;RunTitle=<título\>]**|
|**/ListTests:[*nombre de archivo*]**|Muestra las pruebas detectadas del contenedor de pruebas especificado.|
|**/ListDiscoverers**|Muestra los programas de detección de pruebas instalados.|
|**/ListExecutors**|Muestra los programas de ejecución de pruebas instalados.|
|**/ListLoggers**|Muestra los registradores de pruebas instalados.|
|**/ListSettingsProviders**|Muestra los proveedores de configuración de pruebas instalados.|
|**/Blame**|Realiza un seguimiento de las pruebas a medida que se ejecutan y, si se bloquea el proceso de host de prueba, emite los nombres de las pruebas en su secuencia de ejecución hasta, e incluyendo, la prueba específica que se estaba ejecutando en el momento del bloqueo. Este resultado facilita el aislamiento de la prueba infractora y un diagnóstico más profundo. [Más información](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/Diag:[*nombre de archivo*]**|Escribe registros de seguimiento de diagnóstico en el archivo especificado.|
|**/ResultsDirectory:[*ruta de acceso*]**|Si no existe, el directorio de los resultados de la prueba se creará en la ruta de acceso especificada.<br />Ejemplo: `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId:[*IdentificadorProcesoPrincipal*]**|Identificador del proceso principal responsable de iniciar el proceso actual.|
|**/Port:[*puerto*]**|El puerto para la conexión de socket y la recepción de mensajes de eventos.|
|**/Collect:[*dataCollector friendlyName*]**|Habilita el recopilador de datos para la ejecución de pruebas. [Más información](https://aka.ms/vstest-collect).|

> [!TIP]
> Las opciones y los valores no distinguen mayúsculas de minúsculas.

## <a name="examples"></a>Ejemplos

La sintaxis para ejecutar *VSTest.Console.exe* es:

`Vstest.console.exe [TestFileNames] [Options]`

El siguiente comando ejecuta *VSTest.Console.exe* para la biblioteca de pruebas **myTestProject.dll**:

```cmd
vstest.console.exe myTestProject.dll
```

El siguiente comando ejecuta *VSTest.Console.exe* con varios archivos de prueba. Separe los nombres de archivos de prueba con espacios:

```cmd
Vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

El siguiente comando ejecuta *VSTest.Console.exe* con varias opciones. Ejecuta las pruebas en el archivo *myTestFile.dll* en un proceso aislado y usa la configuración especificada en el archivo *Local.RunSettings*. Además, solo ejecuta las pruebas marcadas "Prioridad=1" y registra los resultados en un archivo *.trx*.

```cmd
vstest.console.exe  myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```
