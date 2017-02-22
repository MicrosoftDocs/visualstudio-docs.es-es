---
title: "/ResetAddin (devenv.exe) | Microsoft Docs"
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
  - "estado del complemento"
  - "deshabilitar complemento"
  - "restablecer complemento"
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quita los comandos y la interfaz de usuario de comandos asociada al complemento especificado.  
  
## Sintaxis  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## Argumentos  
 `AddIn`  
 Opcional.  Nombre de comando del complemento.  
  
## Comentarios  
 De forma predeterminada, el nombre de comando del complemento es igual a *\<nombreDeSoluciónDeComplemento\>*.Connect*.\<nombreDeSoluciónDeComplemento\>* y aparece en Connect.cs como el parámetro `commandName` del método `Exec`.  También puede comprobar el nombre de comando si empieza a escribir el nombre del complemento en la ventana Comandos de Visual Studio y usa Intellisense para rellenar el resto.  
  
## Ejemplo  
 El siguiente ejemplo inicia Visual Studio y evita que el complemento `MiComplemento` se ejecute en el inicio.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## Vea también  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)