---
title: "Nuevo archivo (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.newfile"
helpviewer_keywords: 
  - "File.NewFile (comando)"
  - "Nuevo archivo (comando)"
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Nuevo archivo (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Crea un archivo nuevo y lo abre.  El archivo aparece en la carpeta Archivos varios.  
  
## Sintaxis  
  
```  
File.NewFile [filename] [/t:templatename] [/editor:editorname]  
```  
  
## Argumentos  
 `filename`  
 Opcional.  Nombre del archivo.  Si no se especifica ningún nombre, se proporciona un nombre predeterminado.  Si no se muestra ningún nombre de plantilla, se crea un archivo de texto.  
  
## Modificadores  
 \/t:`templatename`  
 Opcional.  Especifica el tipo de archivo que se va a crear.  
  
 \/t: la sintaxis de los argumentos de`templatename` refleja la encontrada en el cuadro de diálogo Nuevo archivo.  Escriba el nombre de categoría seguido de una barra diagonal inversa \(`\`\) y el nombre de plantilla e incluya toda la cadena entre comillas.  
  
 Por ejemplo, para crear un archivo de código fuente de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] tiene que escribir lo siguiente para el argumento \/t:`templatename`.  
  
```  
/t:"Visual C++\C++ File (.cpp)"  
```  
  
 El ejemplo anterior indica que la plantilla de Archivo de C\+\+ está situada en la categoría de Visual C\+\+ en el cuadro de diálogo **Nuevo archivo**.  
  
 \/e:`editorname`  
 Opcional.  Nombre del editor en el que se abrirá el archivo.  Si se especifica el argumento pero no se proporciona ningún nombre de editor, aparece el cuadro de diálogo **Abrir con**.  
  
 \/e: la sintaxis de los argumentos de`editorname` utiliza los nombres de editor como aparecen en el cuadro de diálogo abrir con, entre comillas.  
  
 Por ejemplo, para abrir un archivo en el editor de código fuente, tiene que escribir lo siguiente para el argumento \/e:`editorname`.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Ejemplo  
 Este ejemplo crea una nueva página Web "test1.htm" y la abre en el editor de código fuente.  
  
```  
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Ventana Inmediato](../../ide/reference/immediate-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)