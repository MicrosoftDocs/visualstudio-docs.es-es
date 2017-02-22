---
title: "Mostrar m&#243;dulos (Comando) | Microsoft Docs"
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
  - "debug.listmodules"
helpviewer_keywords: 
  - "Debug.ListModules (comando)"
  - "mostrar módulos (comando)"
  - "ListModules (comando)"
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Mostrar m&#243;dulos (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Muestra los módulos para el proceso actual.  
  
## Sintaxis  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### Parámetros  
 \/Address:`yes|no`  
 Opcional.  Especifica si se mostrarán o no las direcciones de memoria de los módulos.  El valor predeterminado es `yes`.  
  
 \/Name:`yes|no`  
 Opcional.  Especifica si se mostrarán o no los nombres de los módulos.  El valor predeterminado es `yes`.  
  
 \/Order:`yes|no`  
 Opcional.  Especifica si se mostrará o no el orden de los módulos.  El valor predeterminado es `no`.  
  
 \/Path:`yes|no`  
 Opcional.  Especifica si se mostrarán o no las rutas de acceso de los módulos.  El valor predeterminado es `yes`.  
  
 \/Process:`yes|no`  
 Opcional.  Especifica si se mostrarán o no los procesos de los módulos.  El valor predeterminado es `no`.  
  
 \/SymbolFile:`yes|no`  
 Opcional.  Especifica si se mostrarán o no los archivos de símbolos de los módulos.  El valor predeterminado es `no`.  
  
 \/SymbolStatus:`yes|no`  
 Opcional.  Especifica si se mostrarán o no los estados de símbolos de los módulos.  El valor predeterminado es `yes`.  
  
 \/Timestamp:`yes|no`  
 Opcional.  Especifica si se mostrarán o no las marcas de tiempo de los módulos.  El valor predeterminado es `no`.  
  
 \/Version:`yes|no`  
 Opcional.  Especifica si se mostrarán o no las versiones de los módulos.  El valor predeterminado es `no`.  
  
## Comentarios  
  
## Ejemplo  
 En este ejemplo se muestran los nombres, las direcciones y las marcas de tiempo de los módulos para el proceso actual.  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cómo: Utilizar la ventana Módulos](../../debugger/how-to-use-the-modules-window.md)