---
title: Registro de una ventana de herramientas | Microsoft Docs
description: Obtenga información sobre cómo puede registrar las ventanas de herramientas con Visual Studio mediante ProvideToolWindowAttribute y ProvideToolWindowVisibilityAttribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13c3035f089855f88d54ecc8b3c1e6434ac10e65
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056589"
---
# <a name="register-a-tool-window"></a>Registro de una ventana de herramientas
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

 En el código anterior, <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> registra las ventanas de `PersistedWindowPane` `DynamicWindowPane` herramientas y con Visual Studio. La ventana de herramientas conservada está acoplada y con la pestaña **Explorador de soluciones**, y a la ventana dinámica se le asigna una posición inicial y un tamaño predeterminados. La ventana dinámica se hace transitoria, lo que indica que no se crea en el inicio. Esto escribe un `DontForceCreate` valor en la `ToolWindows` clave del registro del sistema. Para obtener más información, vea configuración de visualización de la [ventana de herramientas](/previous-versions/visualstudio/visual-studio-2015/extensibility/tool-window-display-configuration?preserve-view=true&view=vs-2015).