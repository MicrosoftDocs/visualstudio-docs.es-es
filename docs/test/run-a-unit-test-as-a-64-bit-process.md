---
title: Ejecutar una prueba unitaria como un proceso de 64 bits | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 36a33e9be37255e6bcf199e612a44f65ca243a1e
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2018
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Ejecutar una prueba unitaria como un proceso de 64 bits
Si tiene un equipo de 64 bits, puede ejecutar pruebas unitarias y capturar información de cobertura de código como un proceso de 64 bits.  
  
## <a name="running-a-unit-test-as-a-64-bit-process"></a>Ejecutar una prueba unitaria como un proceso de 64 bits  
  
#### <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Para ejecutar una prueba unitaria como un proceso de 64 bits  
  
1.  Si el código o las pruebas se compilaron como un proceso de 32 bits/x86 pero ahora quiere ejecutarlos como un proceso de 64 bits, vuelva a compilarlos como **Cualquier CPU** u opcionalmente como **64 bits**.  
  
    > [!TIP]
    >  Para tener una flexibilidad máxima, compile los proyectos de prueba con la configuración **Cualquier CPU**. Después, se pueden ejecutar en ambos agentes de 32 y 64 bits. No supone ninguna ventaja compilar los proyectos de prueba con la configuración de **64 bits**.  
  
2.  En el menú de Visual Studio, seleccione **Prueba**, **Configuración** y **Arquitectura del procesador**. Seleccione **x64** para ejecutar las pruebas como un proceso de 64 bits.  
  
     \- o -  
  
     Especifique `<TargetPlatform>x64</TargetPlatform>` en un archivo .runsettings. Una ventaja de este método es que puede especificar grupos de configuraciones en archivos diferentes y cambiar rápidamente entre las distintas configuraciones. También puede copiar la configuración entre las soluciones. Para obtener más información, consulte [Configurar pruebas unitarias usando un archivo .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).  
  
## <a name="see-also"></a>Vea también

[Ejecutar pruebas unitarias con el Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md)  
[Haga una prueba unitaria de su código](../test/unit-test-your-code.md)  
