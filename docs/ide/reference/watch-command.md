---
title: "Inspecci&#243;n (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.watch"
helpviewer_keywords: 
  - "Debug.Watch (comando)"
  - "Inspección (comando)"
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Inspecci&#243;n (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Crea y abre una instancia especificada de una ventana **Inspección**.  Puede utilizar una ventana **Inspección** para calcular los valores de variables, expresiones y registros, para modificar estos valores y para guardar los resultados.  
  
## Sintaxis  
  
```  
Debug.Watch[index]  
```  
  
## Argumentos  
 `index`  
 Obligatorio.  Número de instancia de la ventana Inspección.  
  
## Comentarios  
 `index` deben ser un entero.  Los valores válidos son 1, 2, 3 ó 4.  
  
## Ejemplo  
  
```  
>Debug.Watch1  
```  
  
## Vea también  
 [Ventanas de variables locales y automáticas](../../debugger/autos-and-locals-windows.md)   
 [Cómo: Modificar un valor en una ventana de variable](../Topic/How%20to:%20Edit%20a%20Value%20in%20a%20Variable%20Window.md)   
 [Cómo: Utilizar el cuadro de diálogo Inspección rápida](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)