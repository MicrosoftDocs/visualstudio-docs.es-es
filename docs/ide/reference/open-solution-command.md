---
title: "Abrir soluci&#243;n (Comando) | Microsoft Docs"
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
  - "file.opensolution"
helpviewer_keywords: 
  - "File.OpenSolution (comando)"
  - "Abrir solución (comando)"
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Abrir soluci&#243;n (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Abre una solución existente y cierra cualquier otra solución abierta.  
  
## Sintaxis  
  
```  
File.OpenSolution filename  
```  
  
## Argumentos  
 `Filename`  
 Obligatorio.  Nombre de archivo y ruta de acceso completa de la solución que se va a abrir.  
  
 La sintaxis del argumento `filename` requiere que las rutas de acceso que contienen espacios en blanco se incluyan entre comillas.  
  
## Comentarios  
 La finalización automática intenta localizar la ruta de acceso y el nombre de archivo correctos a medida que los va escribiendo.  
  
## Ejemplo  
 En este ejemplo se abre la solución Test1.sln.  
  
```  
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)