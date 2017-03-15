---
title: "Agregar proyecto existente (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.addexistingproject"
helpviewer_keywords: 
  - "Agregar proyecto existente (comando)"
  - "File.AddExistingProject"
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Agregar proyecto existente (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Agrega un proyecto existente a la solución actual.  
  
## Sintaxis  
  
```  
File.AddExistingProject filename  
```  
  
## Argumentos  
 `filename`  
 Opcional.  Ruta de acceso completa y nombre de archivo, con extensión, del proyecto que se va a agregar a la solución.  
  
 Si el argumento `filename` incluye espacios en blanco, debe aparecer entre comillas.  
  
 Si no se especifica ningún nombre de archivo, el comando abrirá el cuadro de diálogo de archivo para que el usuario pueda elegir un proyecto.  
  
## Comentarios  
 La finalización automática intenta localizar la ruta de acceso y el nombre de archivo correctos a medida que los va escribiendo.  
  
## Ejemplo  
 Este ejemplo agrega el proyecto de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], TestProject1, a la solución actual.  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)