---
title: "Agregar nuevo elemento (Comando) | Microsoft Docs"
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
  - "project.addnewitem"
helpviewer_keywords: 
  - "Agregar nuevo elemento (comando)"
  - "File.AddNewItem (comando)"
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Agregar nuevo elemento (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Agrega un nuevo elemento de solución, como un .htm, .css, .txt o un conjunto de marcos a la solución actual y los abre.  
  
## Sintaxis  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## Argumentos  
 `filename`  
 Opcional.  Ruta de acceso y nombre de archivo del elemento que se va a agregar a la solución.  
  
## Modificadores  
 \/t: `templatename`  
 Opcional.  Especifica el tipo de archivo que se va a crear.  Si no se proporciona ningún nombre de plantilla, se crea un archivo de texto de forma predeterminada.  
  
 La sintaxis del argumento \/t:`templatename` refleja la información encontrada en el cuadro de diálogo **Agregar nuevo elemento de solución**.  Tiene que especificar la categoría completa seguida del tipo de archivo; para ello, separe el nombre de categoría del tipo de archivo con una barra inversa \(`\`\) e incluya la cadena completa entre comillas.  
  
 Por ejemplo, para crear un archivo de texto nuevo tiene que escribir lo siguiente para el argumento \/t:`templatename`.  
  
```  
/t:"General\Style Sheet"  
```  
  
 \/e: `editorname`  
 Opcional.  Nombre del editor en el que se abrirá el archivo.  Si se especifica el argumento pero no se proporciona ningún nombre de editor, aparece el cuadro de diálogo **Abrir con**.  
  
 La sintaxis del argumento \/e:`editorname` utiliza los nombres de editor tal y como aparecen en el **cuadro de diálogo Abrir con**, incluidos entre comillas.  
  
 Por ejemplo, para abrir una hoja de estilos en el editor de código fuente, tiene que escribir lo siguiente para el argumento \/e:`editorname`.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Ejemplo  
 Este ejemplo agrega un elemento de solución nuevo, MyHTMLpg, a la solución actual.  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)