---
title: "Inspecci&#243;n r&#225;pida (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.quickwatch"
helpviewer_keywords: 
  - "Debug.Quickwatch (comando)"
  - "Inspección rápida (comando)"
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Inspecci&#243;n r&#225;pida (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Muestra el texto seleccionado o especificado en el campo Expresión del [Cuadro de diálogo Inspección rápida](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md).  Puede utilizar este cuadro de diálogo para calcular el valor actual de una variable o de una expresión reconocida por el depurador, o el contenido de un registro.  Además, puede cambiar el valor de cualquier variable no constante o el contenido de cualquier registro.  
  
## Sintaxis  
  
```  
Debug.QuickWatchq [text]  
```  
  
## Argumentos  
 `text`  
 Opcional.  Texto que se va a agregar al cuadro de diálogo **Inspección rápida**.  
  
## Comentarios  
 Si se omite `text`, la palabra o el texto seleccionados actualmente en el cursor se agregan a la ventana Inspección.  
  
## Ejemplo  
  
```  
>Debug.QuickWatch  
```  
  
## Vea también  
 [Cómo: Utilizar el cuadro de diálogo Inspección rápida](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)