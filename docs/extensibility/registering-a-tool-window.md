---
title: Registro de una ventana de herramientas | Microsoft Docs
description: Obtenga información sobre cómo puede registrar las ventanas de herramientas Visual Studio mediante ProvideToolWindowAttribute y ProvideToolWindowVisibilityAttribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f4fb6330f913989a69c5d8d28374a40ea14d266d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899100"
---
# <a name="register-a-tool-window"></a>Registrar una ventana de herramientas
Puede registrar las ventanas de herramientas mediante <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> y  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> .

## <a name="example"></a>Ejemplo

```csharp

[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]
[ProvideMenuResource(1000, 1)]
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]
public class PackageToolWindow : Package
{
```

 En el código anterior, registra <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> las ventanas de herramientas y con `PersistedWindowPane` `DynamicWindowPane` Visual Studio. La ventana de herramientas persistente está acoplada y con pestañas con Explorador de soluciones **,** y la ventana dinámica tiene una posición inicial y un tamaño predeterminados. La ventana dinámica se hace transitoria, lo que indica que no se crea durante el inicio. Esto escribe un `DontForceCreate` valor en la clave del Registro del `ToolWindows` sistema. Para obtener más información, vea [Configuración de visualización de la ventana de herramientas.](/previous-versions/visualstudio/visual-studio-2015/extensibility/tool-window-display-configuration?preserve-view=true&view=vs-2015)