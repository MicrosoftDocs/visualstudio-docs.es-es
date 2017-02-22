---
title: "Implementaci&#243;n de VS Shell | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 2
caps.handback.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Implementaci&#243;n de VS Shell
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un shell aislado permite determinar que la funcionalidad de Visual Studio necesita para interactuar con el lenguaje específico y cómo esa solución debe aparecer.  Para obtener más información sobre el shell aislado Visual Studio, vea [Personalizar el Shell aislado](../extensibility/customizing-the-isolated-shell.md).  Puede encontrar más información sobre cómo personalizar el shell aislado en [Customizing the Isolated Shell](http://msdn.microsoft.com/es-es/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### Para establecer un shell de Visual Studio como destino de implementación  
  
1.  En el proyecto de **DslPackage** , abra **source.extension.tt**.  
  
2.  En inserción de `<SupportedProducts>` :  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Reemplace *MyIsolatedShell* con el nombre del paquete de shell aislado.