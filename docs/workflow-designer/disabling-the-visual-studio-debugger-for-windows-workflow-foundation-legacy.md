---
title: "Deshabilitar el Depurador de Microsoft Visual Studio para Windows Workflow Foundation (Heredado) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "depurar flujos de trabajo, deshabilitar el depurador"
  - "depurador de flujos de trabajo, deshabilitar"
  - "flujos de trabajo, deshabilitar el depurador"
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Deshabilitar el Depurador de Microsoft Visual Studio para Windows Workflow Foundation (Heredado)
En este tema se describe cómo deshabilitar el depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mediante el archivo de configuración cuando se compilen aplicaciones [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado.Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 De forma predeterminada, el depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] para [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] se habilita para un proceso de host.Para deshabilitar la depuración de flujos de trabajo, debe desactivarlo explícitamente agregando un elemento **\<switches\>** de la entrada "DisableWorkflowDebugging" en la sección **\<system.diagnostics\>** del archivo de configuración de host.  
  
 En el ejemplo siguiente se muestra cómo modificar el archivo de configuración de host para deshabilitar la depuración de flujos de trabajo.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="DisableWorkflowDebugging" value="true"/>  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## Vea también  
 [Invocar el Depurador de Microsoft Visual Studio para Windows Workflow Foundation \(Heredado\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)