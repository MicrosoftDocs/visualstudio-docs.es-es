---
title: Migración de testsettings a runsettings
description: Aprenda a migrar testsettings a runsettings.
ms.custom: SEO-VS-2020
ms.date: 03/18/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab1cfe921777fa75d4f69251668934e8d78d9bec
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106087201"
---
# <a name="upgrade-from--testsettings-to-runsettings"></a>Actualice de *.testsettings* a *.runsettings*.

Puede actualizar el archivo de configuración de prueba de *.testsettings* a *.runsettings* con la herramienta SettingsMigrator que se instala junto con Visual Studio. En función de la ubicación de instalación de Visual Studio, puede encontrar la herramienta SettingsMigrator en la siguiente ruta de acceso: `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Extensions\TestPlatform\SettingsMigrator.exe`.

En la ubicación de directorio correcta, puede ejecutar la herramienta con el siguiente formato:

```console
SettingsMigrator.exe <Full path to testsettings file to be migrated>
SettingsMigrator.exe <Full path to testsettings file to be migrated> <Full path to runsettings file to be created>
```

## <a name="examples"></a>Ejemplos
```console
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings E:\MyTest\MyNewRunSettings.runsettings
```

Si le interesa leer más sobre cómo se convierten las opciones *.testsettings* en *.runsettings*, puede encontrar más detalles de la implementación en el [repositorio de la plataforma de pruebas de código abierto](https://github.com/microsoft/vstest-docs/blob/master/RFCs/0023-TestSettings-Deprecation.md#migration) de GitHub.

## <a name="see-also"></a>Consulte también

- [Configuración de serie de pruebas con `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Actualización de MSTestv1 a MSTestv2](../test/mstest-update-to-mstestv2.md)
- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)
- [Depurar pruebas unitarias con el Explorador de pruebas](../test/debug-unit-tests-with-test-explorer.md)
