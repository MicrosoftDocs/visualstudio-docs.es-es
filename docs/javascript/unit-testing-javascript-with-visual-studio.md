---
title: Pruebas unitarias en Node.js
description: Visual Studio admite las pruebas unitarias de código de JavaScript mediante Herramientas de Node.js para Visual Studio
ms.custom: ''
ms.date: 06/06/2018
ms.technology: vs-nodejs
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 071f64c4239441d3c3fd2c111d1b912175e23316
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766540"
---
# <a name="unit-testing-in-nodejs"></a>Pruebas unitarias en Node.js

Herramientas de Node.js para Visual Studio permite escribir y ejecutar pruebas unitarias mediante algunos de los marcos de JavaScript más populares sin necesidad de cambiar a un símbolo del sistema.

Los marcos admitidos son:
* Mocha ([mochajs.org](http://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Tape ([github.com/substack/tape](https://github.com/substack/tape))
* Export Runner (este marco es específico de Herramientas de Node.js para Visual Studio)

> [!WARNING]
> Un problema en Tape de momento evita que se ejecuten pruebas de Tape. Si [PR #361](https://github.com/substack/tape/pull/361) se combina, debería resolverse el problema.

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
> No use la opción `outdir` ni `outfile` en *tsconfig.json*, ya que el Explorador de pruebas no puede buscar las pruebas unitarias en archivos de TypeScript.

## <a name="run-tests"></a>Ejecutar pruebas

Puede ejecutar pruebas en Visual Studio 2017 o desde la línea de comandos.

### <a name="run-tests-in-visual-studio-2017"></a>Ejecutar pruebas en Visual Studio 2017

Puede ejecutar las pruebas si hace clic en el vínculo **Ejecutar todo** del Explorador de pruebas. O bien, puede ejecutar pruebas si selecciona uno o varios grupos o pruebas, hace clic con el botón derecho y selecciona **Ejecutar pruebas seleccionadas** en el menú contextual. Las pruebas se ejecutan en segundo plano y el Explorador de pruebas actualiza y muestra los resultados automáticamente. Además, puede depurar pruebas seleccionadas si selecciona **Depurar pruebas seleccionadas**.

> [!Warning]
> La depuración de pruebas unitarias mediante Node 8+ de momento solo funciona en archivos de prueba de JavaScript; en los archivos de prueba de TypeScript se produce un error al alcanzar puntos de interrupción. Como alternativa, use la palabra clave `debugger`.

> [!NOTE]
> Actualmente no se admiten las pruebas de generación de perfiles ni la cobertura de código.

### <a name="run-tests-from-the-command-line"></a>Ejecutar pruebas desde la línea de comandos

Puede ejecutar las pruebas desde el [Símbolo del sistema para desarrolladores](/dotnet/framework/tools/developer-command-prompt-for-vs) de Visual Studio 2017 mediante el siguiente comando:

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

## <a name="addingFramework"></a>Agregar compatibilidad con un marco de pruebas unitarias

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

> [!NOTE]
> Actualmente, esto no funciona con proyectos de .NET Standard y .NET Core.
