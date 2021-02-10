---
title: Pruebas unitarias de JavaScript y TypeScript
description: Visual Studio admite las pruebas unitarias de código de JavaScript y TypeScript mediante Herramientas de Node.js para Visual Studio
ms.date: 07/06/2020
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: e10f9b628d1d9fbbdb2911977fe7e63b1a7b6d57
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957483"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>Pruebas unitarias de JavaScript y TypeScript en Visual Studio

Herramientas de Node.js para Visual Studio permite escribir y ejecutar pruebas unitarias mediante algunos de los marcos de JavaScript más populares sin necesidad de cambiar a un símbolo del sistema.

Los marcos admitidos son:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Tape ([github.com/substack/tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))
* Export Runner (este marco es específico de Herramientas de Node.js para Visual Studio)

Si su marco preferido no es compatible, vea [Agregar compatibilidad con un marco de pruebas unitarias](#addingFramework) para obtener información sobre cómo lograr la compatibilidad.

## <a name="write-unit-tests"></a>Escribir pruebas unitarias

Antes de agregar pruebas unitarias al proyecto, asegúrese de que el marco que piensa usar está instalado localmente en el proyecto. Es sencillo con la [ventana de instalación del paquete de npm](npm-package-management.md#npmInstallWindow).

La mejor manera de agregar pruebas unitarias al proyecto es crear una carpeta *tests* en él y establecerla como raíz de las pruebas en las propiedades del proyecto. También debe seleccionar el marco de pruebas que quiere usar.

![Establecimiento de la raíz y el marco de pruebas](../javascript/media/unit-test-project-properties.png)

Puede agregar pruebas simples en blanco al proyecto mediante el cuadro de diálogo **Agregar nuevo elemento**. JavaScript y TypeScript se admiten en el mismo proyecto.

![Incorporación de nueva prueba unitaria](../javascript/media/unit-test-add-new-item.png)

En una prueba unitaria de Mocha, use el código siguiente:

```javascript
var assert = require('assert');

describe('Test Suite 1', function() {
    it('Test 1', function() {
        assert.ok(true, "This shouldn't fail");
    })

    it('Test 2', function() {
        assert.ok(1 === 1, "This shouldn't fail");
        assert.ok(false, "This should fail");
    })
})
```

Si no ha establecido las opciones de la prueba unitaria en las propiedades del proyecto, debe asegurarse de que la propiedad **Marco de prueba** de la ventana **Propiedades** esté establecida en el marco de pruebas correcto para los archivos de la prueba unitaria. Esto se realiza automáticamente mediante plantillas de archivo de prueba unitaria.

![Marco de prueba](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> Las opciones de pruebas unitarias tienen preferencia sobre la configuración de los archivos individuales.

Después de abrir el Explorador de pruebas (elija **Prueba** > **Windows** > **Explorador de pruebas**), Visual Studio detecta y muestra las pruebas. Si las pruebas no se muestran inicialmente, vuelva a compilar el proyecto para actualizar la lista.

![Explorador de pruebas](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> Para TypeScript, no use la opción `outdir` ni `outfile` en *tsconfig.json*, ya que el Explorador de pruebas no encontrará las pruebas unitarias.

## <a name="run-tests"></a>Ejecutar pruebas

Puede ejecutar pruebas en Visual Studio o desde la línea de comandos.

### <a name="run-tests-in-visual-studio"></a>Ejecución de pruebas en Visual Studio

::: moniker range=">=vs-2019"
Puede ejecutar las pruebas si hace clic en el vínculo **Ejecutar todo** del Explorador de pruebas. O bien, puede ejecutar pruebas si selecciona uno o varios grupos o pruebas, hace clic con el botón derecho y selecciona **Ejecutar** en el menú contextual. Las pruebas se ejecutan en segundo plano y el Explorador de pruebas actualiza y muestra los resultados automáticamente. Además, puede depurar las pruebas seleccionadas si hace clic con el botón derecho y selecciona **Depurar**.
::: moniker-end
::: moniker range="vs-2017"
Puede ejecutar las pruebas si hace clic en el vínculo **Ejecutar todo** del Explorador de pruebas. O bien, puede ejecutar pruebas si selecciona uno o varios grupos o pruebas, hace clic con el botón derecho y selecciona **Ejecutar pruebas seleccionadas** en el menú contextual. Las pruebas se ejecutan en segundo plano y el Explorador de pruebas actualiza y muestra los resultados automáticamente. Además, puede depurar pruebas seleccionadas si selecciona **Depurar pruebas seleccionadas**.
::: moniker-end

Para TypeScript, las pruebas unitarias se ejecutan en el código JavaScript generado.

> [!NOTE]
> En la mayoría de los escenarios de TypeScript, puede depurar una prueba unitaria estableciendo un punto de interrupción en el código TypeScript, haciendo clic con el botón derecho en una prueba en el Explorador de pruebas y eligiendo **Depurar**. En escenarios más complejos, como los que usan mapas de origen, puede que tenga dificultades para llegar a los puntos de interrupción en el código TypeScript. Como solución alternativa, pruebe a usar la palabra clave `debugger`.

> [!NOTE]
> Actualmente no se admiten las pruebas de generación de perfiles ni la cobertura de código.

### <a name="run-tests-from-the-command-line"></a>Ejecutar pruebas desde la línea de comandos

Puede ejecutar las pruebas desde el [Símbolo del sistema para desarrolladores](/dotnet/framework/tools/developer-command-prompt-for-vs) de Visual Studio mediante el siguiente comando:

```
vstest.console.exe <path to project file>\NodejsConsoleApp23.njsproj /TestAdapterPath:<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter
```

Este comando produce un resultado similar al siguiente:

```
Microsoft (R) Test Execution Command Line Tool Version 15.5.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
Processing: NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 1::mocha
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 2::mocha
Processing finished for framework of Mocha
Passed   Test Suite 1 Test 1
Standard Output Messages:
 Using default Mocha settings
 1..2
 ok 1 Test Suite 1 Test 1

Failed   Test Suite 1 Test 2
Standard Output Messages:
 not ok 1 Test Suite 1 Test 2
   AssertionError [ERR_ASSERTION]: This should fail
       at Context.<anonymous> (NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js:10:16)

Total tests: 2. Passed: 1. Failed: 1. Skipped: 0.
Test Run Failed.
Test execution time: 1.5731 Seconds
```

> [!NOTE]
> Si aparece un error que indica que no se puede encontrar *vstest.console.exe*, asegúrese de que ha abierto el Símbolo del sistema para desarrolladores y no un símbolo del sistema normal.

## <a name="add-support-for-a-unit-test-framework"></a><a name="addingFramework"></a>Agregar compatibilidad con un marco de pruebas unitarias

Puede agregar compatibilidad con otros marcos de pruebas si implementa la lógica de detección y ejecución mediante JavaScript. Para ello, agregue una carpeta con el nombre del marco de pruebas en:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Esta carpeta debe contener un archivo de JavaScript con el mismo nombre que exporte las dos funciones siguientes:

* `find_tests`
* `run_tests`

Para obtener un buen ejemplo de las implementaciones `find_tests` y `run_tests`, vea la implementación del marco de pruebas unitarias de Mocha:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

La detección de marcos de pruebas disponibles se produce al inicio de Visual Studio. Si se agrega un marco mientras se está ejecutando Visual Studio, reinicie Visual Studio para detectar el marco. Pero no es necesario reiniciar al realizar cambios en la implementación.

## <a name="unit-tests-in-other-project-types"></a>Pruebas unitarias en otros tipos de proyecto
No está limitado a escribir pruebas unitarias solo en proyectos de Node.js. Al agregar las propiedades TestFramework y TestRoot a cualquier proyecto de C# o Visual Basic, esas pruebas se enumerarán y puede ejecutarlas mediante la ventana Explorador de pruebas.

Para habilitar esta opción, haga clic con el botón derecho en el nodo del proyecto en el Explorador de soluciones, elija **Descargar el proyecto** y después elija **Editar proyecto**. Después, en el archivo del proyecto, agregue los siguientes dos elementos a un grupo de propiedades.

> [!NOTE]
> Asegúrese de que el grupo de propiedades al que está agregando los elementos no tiene ninguna condición especificada.
> Esto puede causar un comportamiento inesperado.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

Luego, agregue sus pruebas a la carpeta raíz de prueba que ha especificado y estarán disponibles para ejecutarse en la ventana Explorador de pruebas. Si no aparecen al principio, puede que tenga que recompilar el proyecto.

### <a name="unit-test-net-core-and-net-standard"></a>Pruebas unitaria en .NET Core y .NET Standard
Además de las propiedades mencionadas, también deberá instalar el paquete [Microsoft.JavaScript.UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/) de NuGet y establecer la propiedad:

```xml
<PropertyGroup>
    <GenerateProgramFile>false</GenerateProgramFile>
</PropertyGroup>
```

Algunas plataformas de pruebas pueden requerir paquetes npm adicionales para la detección de pruebas. Por ejemplo, jest requiere el paquete npm jest-editor-support. Si es necesario, consulte la documentación de la plataforma específica.
