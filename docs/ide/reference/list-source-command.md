---
title: "Mostrar c&#243;digo fuente (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Debug.ListSource"
helpviewer_keywords: 
  - "Debug.ListSource (comando)"
  - "mostrar código fuente (comando)"
  - "ListSource (comando)"
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Mostrar c&#243;digo fuente (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Muestra las líneas especificadas de código fuente.  
  
## Sintaxis  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## Modificadores  
 \/Count:`number`  
 Opcional.  Especifica el número de líneas que se van a mostrar.  
  
 \/Current  
 Opcional.  Muestra la línea actual.  
  
 \/File:`filename`  
 Opcional.  Ruta de acceso del archivo que se va a mostrar.  Si no se especifica ningún nombre de archivo, el comando muestra el código fuente para la línea de la instrucción actual.  
  
 \/Line:`number`  
 Opcional.  Muestra un número de línea concreto.  
  
 \/ShowLineNumbers:`yes|no`  
 Opcional.  Especifica si se mostrarán o no los números de línea.  
  
## Comentarios  
  
## Ejemplo  
 Este ejemplo muestra el código fuente desde la línea 4 del archivo Form1.vb, con los números de línea visibles.  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)