---
title: Ejecutar una prueba unitaria como un proceso de 64 bits
ms.date: 03/10/2020
ms.topic: how-to
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 04895e3dd72a7cb4f0373c970db0f12582506ef9
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285561"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Ejecutar una prueba unitaria como un proceso de 64 bits

Si tiene un equipo de 64 bits, puede ejecutar pruebas unitarias y capturar información de cobertura de código como un proceso de 64 bits.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Para ejecutar una prueba unitaria como un proceso de 64 bits

1. Si el código o las pruebas se compilaron como un proceso de 32 bits/x86, pero ahora quiere ejecutarlos como un proceso de 64 bits, vuelva a compilarlos como **Cualquier CPU**.

   ::: moniker range="vs-2017"
   De forma alternativa, también puede compilar el proyecto como de **64 bits** en Visual Studio 2017.
   ::: moniker-end

    > [!TIP]
    > Para tener una flexibilidad máxima, compile los proyectos de prueba con la configuración **Cualquier CPU**. Después, se pueden ejecutar en ambos agentes de 32 y 64 bits. No supone ninguna ventaja compilar los proyectos de prueba con la configuración de **64 bits**.

2. Establezca las pruebas unitarias para que se ejecuten como un proceso de 64 bits.

   ::: moniker range=">=vs-2019"
   En el menú de Visual Studio, seleccione **Prueba** y, después, **Arquitectura de procesador para proyectos de AnyCPU**. Seleccione **x64** para ejecutar las pruebas como un proceso de 64 bits.
   ::: moniker-end
   ::: moniker range="vs-2017"
   En el menú de Visual Studio, seleccione **Prueba**, **Configuración de pruebas** y **Arquitectura del procesador**. Seleccione **x64** para ejecutar las pruebas como un proceso de 64 bits.
   ::: moniker-end

   \- o -

   Especifique `<TargetPlatform>x64</TargetPlatform>` en un archivo *.runsettings*. Una ventaja de este método es que puede especificar grupos de configuraciones en archivos diferentes y cambiar rápidamente entre las distintas configuraciones. También puede copiar la configuración entre las soluciones. Para obtener más información, consulte [Configurar pruebas unitarias usando un archivo .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Vea también

- [Ejecutar pruebas unitarias con el Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md)
- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)
