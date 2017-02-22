---
title: "Ejecutar una prueba unitaria como un proceso de 64 bits | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pruebas unitarias, crear"
  - "pruebas unitarias, ejecutar"
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "mlearned"
manager: "douge"
---
# Ejecutar una prueba unitaria como un proceso de 64 bits
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si tiene un equipo de 64 bits, puede ejecutar pruebas unitarias y capturar información de cobertura de código como un proceso de 64 bits.  
  
## Ejecutar una prueba unitaria como un proceso de 64 bits  
  
#### Para ejecutar una prueba unitaria como un proceso de 64 bits  
  
1.  Si el código o las pruebas se compilaron como x86 de 32 bits, pero ahora desea ejecutarlos como un proceso de 64 bits, vuelva a compilarlos como **Cualquier CPU** u, opcionalmente, **64 bits**.  
  
    > [!TIP]
    >  Para tener una flexibilidad máxima, compile los proyectos de prueba con la configuración **Cualquier CPU**.  Después, se pueden ejecutar en ambos agentes de 32 y 64 bits.  No hay ventaja por compilar los proyectos de prueba con la configuración de **64 bits**.  
  
2.  En el menú de Visual Studio, elija **Prueba**, elija **Configuración** y elija **Arquitectura del procesador**.  Elija **x64** para ejecutar las pruebas como un proceso de 64 bits.  
  
     – O bien –  
  
     Especifique `<TargetPlatform>x64</TargetPlatform>` en un archivo de .runsettings.  Una ventaja de este método es que puede especificar grupos de valores en archivos diferentes y intercambiarlos rápidamente entre valores diferentes.  También puede copiar valores entre las soluciones.  Para obtener más información, vea [Configurar pruebas unitarias usando un archivo .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).  
  
## Vea también  
 [Ejecutar pruebas unitarias con el Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md)   
 [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)   
 [Especificar la configuración para las pruebas de Visual Studio](/devops-test-docs/test/specifying-test-settings-for-visual-studio-tests)