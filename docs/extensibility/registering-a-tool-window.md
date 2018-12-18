---
title: Registrar una ventana de herramientas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 17c9233d3df0bb7101b374fd1990536d2341fa49
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638334"
---
# <a name="register-a-tool-window"></a>Registrar una ventana de herramientas
Puede registrar las ventanas de herramienta con <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> y <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>.  
  
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
  
 En el código anterior, el <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> registra el `PersistedWindowPane` y `DynamicWindowPane` ventanas con Visual Studio. La ventana de herramientas persistente está acoplada y por fichas con **el Explorador de soluciones**, y la ventana dinámica tiene un valor predeterminado a partir de posición y tamaño. La ventana dinámica se realiza transitoria, lo que indica que no se crea durante el inicio. Escribe un `DontForceCreate` valor en el `ToolWindows` clave del registro del sistema. Para obtener más información, consulte [configuración de pantalla de ventana de herramienta](../extensibility/tool-window-display-configuration.md).
