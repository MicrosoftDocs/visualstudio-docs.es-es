---
title: "Agregar elemento existente (Comando) | Microsoft Docs"
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
  - "project.addexistingitem"
helpviewer_keywords: 
  - "Agregar elemento existente (comando)"
  - "File.AddExistingItem (comando)"
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Agregar elemento existente (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Agrega un archivo existente a la solución actual y lo abre.  
  
## Sintaxis  
  
```  
File.AddExistingItem filename [/e:editorname]  
```  
  
## Argumentos  
 `filename`  
 Obligatorio.  Ruta de acceso completa y nombre de archivo, con extensión, del elemento que se va a agregar a la solución actual.  Si la ruta de acceso del archivo o el nombre de archivo contienen espacios, escriba la ruta de acceso completa entre comillas.  
  
## Modificadores  
 \/e: `editorname`  
 Opcional.  Nombre del editor en el que se abrirá el archivo.  Si se especifica el argumento pero no se proporciona ningún nombre de editor, aparece el cuadro de diálogo **Abrir con**.  
  
 La sintaxis del argumento \/e:`editorname` utiliza los nombres de editor tal y como aparecen en el **cuadro de diálogo Abrir con**, incluidos entre comillas.  Por ejemplo, para abrir una hoja de estilos en el editor de código fuente, tiene que escribir lo siguiente para el argumento \/e:`editorname`.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Comentarios  
 La finalización automática intenta localizar la ruta de acceso completa y el nombre de archivo a medida que escribe.  
  
## Ejemplo  
 Este ejemplo agrega el archivo Form1.frm a la solución actual.  
  
```  
>File.AddExistingItem "C:\public\solution files\Form1.frm"  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)