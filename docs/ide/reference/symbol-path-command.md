---
title: "Ruta de acceso de s&#237;mbolos (Comando) | Microsoft Docs"
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
  - "debug.symbolpath"
helpviewer_keywords: 
  - "Debug.SymbolPath (comando)"
  - "ruta de acceso de símbolos (comando)"
  - "SymbolPath (comando)"
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Ruta de acceso de s&#237;mbolos (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Establece la lista de directorios para que el depurador busque símbolos.  
  
## Sintaxis  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## Argumentos  
 `pathname`  
 Opcional.  Lista de rutas de acceso delimitada por signos de punto y coma para que el depurador busque símbolos.  
  
## Comentarios  
 Si no se especifica `pathname`, el comando muestra las rutas de acceso de símbolos actuales.  
  
## Ejemplo  
 Este ejemplo agrega dos rutas de acceso a la lista de directorios de símbolos.  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## Ejemplo  
 Este ejemplo muestra una lista de rutas de acceso de símbolos actuales delimitada por signos de punto y coma.  
  
```  
Debug.SymbolPath  
```  
  
## Vea también  
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)