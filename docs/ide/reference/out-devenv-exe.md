---
title: "/Out (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/out (modificador para Devenv)"
  - "compilaciones [Visual Studio], errores"
  - "compilaciones [Visual Studio], registros"
  - "Devenv, /out (modificador)"
  - "registros de errores [Visual Studio]"
  - "registros de errores [Visual Studio], errores de compilación de la línea de comandos"
  - "errores [Visual Studio], compilaciones"
  - "out (modificador para Devenv)"
  - "archivos de salida, errores de compilación"
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Out (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica un archivo donde se almacenarán y mostrarán los errores cuando ejecute, compile, recompile o implemente una solución.  
  
## Sintaxis  
  
```  
devenv /out FileName  
```  
  
## Argumentos  
 `FileName`  
 Obligatorio.  Ruta de acceso y nombre del archivo para recibir errores al compilar un ejecutable.  
  
## Comentarios  
 Si se especifica un nombre de archivo que no existe, el archivo se crea de forma automática.  Si ya existe el archivo, se anexarán los resultados al contenido existente del archivo.  
  
 Los errores de compilación de línea de comandos se muestran en la ventana **Comando** y en la vista Generador de soluciones de la **Ventana de salida**.  Esta opción es útil si está ejecutando compilaciones desatendidas y necesita ver los resultados.  
  
## Ejemplo  
 Este ejemplo ejecuta `MySolution` y escribe errores en el archivo `MyErrorLog.txt`.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Run](../../ide/reference/run-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Deploy](../../ide/reference/deploy-devenv-exe.md)