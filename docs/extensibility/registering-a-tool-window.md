---
title: "Registrar una ventana de herramientas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ventanas de herramientas, registrar administrado"
  - "ventanas de herramientas, registrar"
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Registrar una ventana de herramientas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede registrar las ventanas de herramienta con <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> y  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## Ejemplo  
  
```c#  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 En el código anterior, el <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> registra las ventanas de herramienta PersistedWindowPane y DynamicWindowPane con Visual Studio. La ventana de herramientas persistente está acoplada y fichas con **el Explorador de soluciones**, y se proporciona a la ventana dinámica a partir de posición y el tamaño predeterminado. La ventana dinámica se realiza transitoria, lo que indica que no se cree en el inicio. Escribe un valor de DontForceCreate en la clave ToolWindows en el registro del sistema. Para obtener más información, consulta [Configuración de pantalla de ventana de herramienta](../extensibility/tool-window-display-configuration.md).