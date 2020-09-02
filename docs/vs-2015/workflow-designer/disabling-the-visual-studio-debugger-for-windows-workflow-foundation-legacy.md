---
title: Deshabilitar el depurador para Windows Workflow Foundation (heredado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eddd72d648e7349f51096a21131f38c2e370a277
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656783"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Deshabilitar el Depurador de Microsoft Visual Studio para Windows Workflow Foundation (Heredado)
En este tema se describe cómo deshabilitar el depurador de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mediante el archivo de configuración cuando se compilen aplicaciones [!INCLUDE[wf](../includes/wf-md.md)] en [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 De forma predeterminada, el depurador de [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] para [!INCLUDE[wf](../includes/wf-md.md)] se habilita para un proceso de host. Para deshabilitar la depuración de flujos de trabajo, debe desactivarlo explícitamente agregando un elemento de entrada "DisableWorkflowDebugging" **\<switches>** en la **\<system.diagnostics>** sección del archivo de configuración del host.

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

## <a name="see-also"></a>Consulte también
 [Invocar el depurador de Visual Studio para la depuración de Windows Workflow Foundation (heredada) flujos de](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)