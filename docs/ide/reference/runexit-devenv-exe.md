---
title: "/Runexit (devenv.exe) | Microsoft Docs"
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
  - "/runexit (modificador para Devenv)"
  - "Devenv, /runexit (modificador)"
  - "runexit (modificador para Devenv)"
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Runexit (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Compila y ejecuta el proyecto o la solución que se ha especificado y, a continuación, cierra el entorno de desarrollo integrado \(IDE\).  
  
## Sintaxis  
  
```  
devenv /runexit {SolutionName|ProjectName}  
```  
  
## Argumentos  
 `SolutionName`  
 Obligatorio.  Ruta de acceso y nombre completos de un archivo de solución.  
  
 `ProjectName`  
 Obligatorio.  Ruta de acceso y nombre completos de un archivo de proyecto.  
  
## Comentarios  
 Compila y, a continuación, ejecuta la solución o el proyecto especificados según los valores establecidos para la configuración de solución activa.  Este modificador minimiza el IDE mientras se ejecuta el proyecto o la solución y cierra el IDE una vez finalizada la ejecución del proyecto o la solución.  
  
-   Las cadenas que incluyan espacios en blanco deben aparecer entre comillas dobles.  
  
-   La información de resumen, incluidos los errores, puede mostrarse en la ventana **Comando** o en cualquier archivo de registro especificado con el modificador `/out`.  
  
## Ejemplo  
 Este ejemplo ejecuta la solución `MySolution` en un IDE minimizado con la configuración de implementación activa y, a continuación, cierra el IDE.  
  
```  
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Run](../../ide/reference/run-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)