---
title: Ejecutar una prueba unitaria como un proceso de 64 bits
description: Aprenda a ejecutar pruebas unitarias y capturar información de cobertura de código como un proceso de 64 bits. Debe usar un equipo de 64 bits.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 7d18a97a3cf8f680e7bfe3d679e8e57f7cc716fb
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329073"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Ejecutar una prueba unitaria como un proceso de 64 bits

Si tiene un equipo de 64 bits, puede ejecutar pruebas unitarias y capturar información de cobertura de código como un proceso de 64 bits.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Para ejecutar una prueba unitaria como un proceso de 64 bits

1. Si el código o las pruebas se compilaron como un proceso de 32 bits/x86, pero ahora quiere ejecutarlos como un proceso de 64 bits, vuelva a compilarlos como **Cualquier CPU**.

   ::: moniker range="vs-2017"
   De forma alternativa, también puede compilar el proyecto como de **64 bits** en Visual Studio 2017.
   ::: moniker-end

    > [!TIP]
    > Para tener una flexibilidad máxima, compile los proyectos de prueba con la configuración **Cualquier CPU**. Después, se pueden ejecutar en ambos agentes de 32 y 64 bits. No hay ninguna ventaja por compilar los proyectos de prueba con la configuración de **64 bits**, a menos que se llame a código que solo se admite en 64 bits.

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
