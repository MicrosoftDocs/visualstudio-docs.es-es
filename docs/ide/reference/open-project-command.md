---
title: "Abrir proyecto (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.openproject"
helpviewer_keywords: 
  - "File.OpenProject (comando)"
  - "op (comando)"
  - "Abrir proyecto (comando)"
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Abrir proyecto (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Abre un proyecto existente.  
  
## Sintaxis  
  
```  
File.OpenProject filename  
```  
  
## Argumentos  
 `filename`  
 Obligatorio.  Nombre del archivo y ruta de acceso completa del proyecto que se va a abrir.  
  
 La sintaxis del argumento `filename` requiere que las rutas de acceso que contienen espacios en blanco se incluyan entre comillas.  
  
## Comentarios  
 La finalización automática intenta localizar la ruta de acceso y el nombre de archivo correctos a medida que los va escribiendo.  
  
 Este comando no está disponible durante la depuración.  
  
## Ejemplo  
 En este ejemplo se abre el proyecto de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], Test1.  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)