---
title: 'Diseñador de flujo de trabajo: deshabilitar al depurador de Visual Studio para Windows Workflow Foundation (heredado)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 473ee507e35f5ec5df902df64ee34326dcf90a2b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969970"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Deshabilitar el Depurador de Microsoft Visual Studio para Windows Workflow Foundation (Heredado)

En este tema se describe cómo deshabilitar al depurador de Visual Studio mediante el archivo de configuración al compilar aplicaciones de Windows Workflow Foundation (WF) en el Diseñador de flujo de trabajo de Windows heredado. Use el Diseñador de flujo de trabajo heredado cuando deba tener como destino la versión 3.5 de .NET Framework o el conocido como WinFX.

 De forma predeterminada, el Visual Studio depurador de Windows Workflow Foundation (WF) está habilitada para un proceso de host. Para deshabilitar la depuración de flujo de trabajo, debe desactivarlo explícitamente agregando una entrada "DisableWorkflowDebugging"  **\<conmutadores >** elemento en el  **\<system.diagnostics >** sección del archivo de configuración de host.

 En el ejemplo siguiente se muestra cómo modificar el archivo de configuración de host para deshabilitar la depuración de flujos de trabajo.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <system.diagnostics>
      <switches>
         <add name="DisableWorkflowDebugging" value="true"/>
      </switches>
   </system.diagnostics>
</configuration>
```

## <a name="see-also"></a>Vea también

- [Invocar el Depurador de Visual Studio para Windows Workflow Foundation (heredado)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)