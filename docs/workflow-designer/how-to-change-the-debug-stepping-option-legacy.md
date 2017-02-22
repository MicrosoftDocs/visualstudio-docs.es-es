---
title: "C&#243;mo: Cambiar la opci&#243;n de ejecuci&#243;n paso a paso de depuraci&#243;n (Heredado) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "ejecución paso a paso por bifurcaciones"
  - "depurar flujos de trabajo, opciones de ejecución paso a paso"
  - "depurar, opciones de ejecución paso a paso"
  - "ejecución paso a paso por instancias"
  - "ejecutar instrucciones paso a paso, cambiar opciones"
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# C&#243;mo: Cambiar la opci&#243;n de ejecuci&#243;n paso a paso de depuraci&#243;n (Heredado)
En este tema se describe cómo cambiar la opción de ejecución paso a paso de depuración para aplicaciones [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado con acciones simultáneas.Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Cuando esté depurando actividades heredadas cuya ejecución sea simultánea, como **ParallelActivity** o **ConditionedActivityGroup**, puede usar una de dos opciones para recorrer el código.  
  
 Siga estos pasos para cambiar la opción de ejecución paso a paso de depuración en el proyecto de flujo de trabajo heredado.  
  
## Procedimientos  
  
#### Para cambiar la opción de ejecución paso a paso de depuración  
  
1.  Inicie Visual Studio.  
  
2.  Abra un proyecto de flujo de trabajo heredado existente o cree un nuevo proyecto que use actividades simultáneas y que tenga como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
3.  En el menú **Flujo de trabajo** del [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado, elija **Depurar** y, a continuación, elija **Opciones de ejecución paso a paso**.  
  
4.  Seleccione **Instancia** o **Bifurcar**.  
  
## Vea también  
 [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)   
 [Depurar opciones de ejecución paso a paso \(Heredado\)](../workflow-designer/debug-stepping-options-legacy.md)