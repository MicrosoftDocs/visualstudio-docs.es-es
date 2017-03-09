---
title: "C&#243;mo: Crear un archivo .vsct a partir de un archivo .cto existente | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "archivos VSCT, crear a partir de un archivo .cto"
ms.assetid: 847717c9-477d-4ac9-8b2c-2da878912478
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# C&#243;mo: Crear un archivo .vsct a partir de un archivo .cto existente
Puede crear un archivo .vsct basado en XML a partir de un archivo .cto binario existente. Si lo hace, podrá aprovechar el nuevo formato de compilador de tabla de comandos. Este proceso funciona aunque el archivo .cto esté compilado a partir de un archivo .ctc. Puede editar y compilar el archivo .vsct en otro archivo .cto.  
  
### Para crear un archivo .vsct a partir de un archivo .cto  
  
1.  Obtenga copias del archivo .cto y el archivo .ctsym correspondiente.  
  
2.  Coloque los archivos en el mismo directorio que el compilador vsct.exe.  
  
3.  En el símbolo del sistema de Visual Studio, vaya al directorio que contiene los archivos .cto y .ctsym.  
  
4.  Escriba **vsct.exe** *ctofilename***.cto** *vsctfilename***.vsct \-S***symfilename***.ctsym**.  
  
     `ctofilename` es el nombre del archivo .cto, `vsctfilename` es el nombre del archivo .vsct que desea crear y `symfilename` es el nombre del archivo .ctsym.  
  
     Este proceso crea un nuevo archivo compilador de tabla de comandos XML .vsct. Puede editar y compilar el archivo con vsct.exe, el compilador de .vsct, tal como lo haría con cualquier otro archivo .vsct.  
  
## Vea también  
 [Cómo: crear una. Archivo de Vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)