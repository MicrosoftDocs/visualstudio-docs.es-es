---
title: Registro de una ventana de herramientas ( Tabing a Tool Window) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e7971de5ae5301d99147bbfc374dda6b039662a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701596"
---
# <a name="register-a-tool-window"></a>Registrar una ventana de herramientas
Puede registrar las ventanas de herramientas utilizando <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> y <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>.

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

 En el código <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> anterior, `PersistedWindowPane` las `DynamicWindowPane` ventanas de herramientas y las de Visual Studio registran. La ventana de herramientas persistentes está acoplada y tabulada con el **Explorador**de soluciones y la ventana dinámica tiene una posición y un tamaño iniciales predeterminados. La ventana dinámica se hace transitoria, lo que indica que no se crea en el inicio. Esto escribe `DontForceCreate` un valor `ToolWindows` en la clave en el registro del sistema. Para obtener más información, consulte Configuración de [visualización](/visualstudio/extensibility/tool-window-display-configuration?view=vs-2015)de la ventana de herramientas .
