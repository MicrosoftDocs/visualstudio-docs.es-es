---
title: Registrar una ventana de herramientas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 908a850b1e86ffc2e8337096266849efeaf04a51
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="registering-a-tool-window"></a>Registrar una ventana de herramientas
Puede registrar las ventanas de herramienta con <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> y<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## <a name="example"></a>Ejemplo  
  
```csharp  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 En el código anterior, el <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> registra las ventanas de herramientas PersistedWindowPane y DynamicWindowPane con Visual Studio. La ventana de herramientas persistente está acoplada y con pestañas con **el Explorador de soluciones**, y la ventana dinámica tiene un inicial de la posición y el tamaño predeterminado. La ventana dinámica se realiza transitoria, lo que indica que no se crea durante el inicio. Escribe un valor de DontForceCreate en la clave de ToolWindows en el registro del sistema. Para obtener más información, consulte [configuración de pantalla de ventana de herramienta](../extensibility/tool-window-display-configuration.md).