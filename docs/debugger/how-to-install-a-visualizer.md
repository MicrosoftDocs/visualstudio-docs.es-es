---
title: "C&#243;mo: Instalar un visualizador | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, visualizadores"
  - "visualizadores, instalar"
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Instalar un visualizador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Después de crear un visualizador, hay que instalarlo para que esté disponible en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Instalar un visualizador es un proceso sencillo.  
  
> [!NOTE]
>  En las aplicaciones de la **Tienda**, solo se admiten los visualizadores de texto estándar, HTML, XML y JSON.  No se admiten los visualizadores personalizados \(creados por el usuario\).  
  
### Para instalar un visualizador  
  
1.  Busque el archivo DLL que contiene el visualizador que ha compilado.  
  
2.  Copie el archivo DLL a una de las siguientes ubicaciones:  
  
    -   *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\`*VisualStudioVersion*`\Visualizers`  
  
3.  Si desea utilizar un visualizador administrado para la depuración remota, copie el archivo DLL en la misma ruta de acceso en el equipo remoto.  
  
4.  Reinicie la sesión de depuración.  
  
## Vea también  
 [Visualizadores](../debugger/create-custom-visualizers-of-data.md)   
 [Cómo: Escribir un visualizador](../debugger/how-to-write-a-visualizer.md)