---
title: Ejecutar una prueba unitaria como un proceso de 64 bits | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: 27
ms.author: gewarren
manager: douge
ms.openlocfilehash: 32f85c68756368f2b2ee2d5b9a1d842497102f41
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259040"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Ejecutar una prueba unitaria como un proceso de 64 bits
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Hacer una prueba unitaria de su código](../test/unit-test-your-code.md)   
 [Especificar la configuración de pruebas para las pruebas en Visual Studio](http://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901)



