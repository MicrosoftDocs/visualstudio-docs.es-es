---
title: "Abrir archivo (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.openfile"
helpviewer_keywords: 
  - "File.OpenFile (comando)"
  - "of (comando)"
  - "Abrir archivo (comando)"
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Abrir archivo (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Abre un archivo existente y permite especificar un editor.  
  
## Sintaxis  
  
```  
File.OpenFile filename [/e:editorname]  
```  
  
## Argumentos  
 `filename`  
 Obligatorio.  Nombre de archivo y ruta de acceso completa o parcial del archivo que se va a abrir.  Las rutas de acceso que contienen espacios en blanco deben aparecer entre comillas.  
  
## Modificadores  
 \/e:`editorname`  
 Opcional.  Nombre del editor en el que se abrirá el archivo.  Si se especifica el argumento pero no se proporciona ningún nombre de editor, aparece el cuadro de diálogo **Abrir con**.  
  
 \/e: la sintaxis de los argumentos de`editorname` utiliza los nombres de editor como aparecen en el cuadro de diálogo abrir con, entre comillas.  
  
 Por ejemplo, para abrir un archivo en el editor de código fuente, tiene que escribir lo siguiente para el argumento \/e:`editorname`.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Comentarios  
 A medida que escribe una ruta de acceso, la finalización automática intenta localizar la ruta de acceso y el nombre de archivo correctos.  
  
## Ejemplo  
 Este ejemplo abre el archivo de estilo "Test1.css" en el editor de código fuente.  
  
```  
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Ventana Inmediato](../../ide/reference/immediate-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)