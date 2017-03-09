---
title: "/Command (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/command (modificador para Devenv)"
  - "Devenv, /command (modificador)"
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Command (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ejecuta el comando especificado después de iniciar el entorno de desarrollo integrado \(IDE\) de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Sintaxis  
  
```  
devenv /command CommandName  
```  
  
## Argumentos  
 `CommandName`  
 Requerido.  Nombre completo de un comando de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o su alias, incluido entre comillas dobles.  Para obtener más información sobre la sintaxis de comandos y de alias, vea [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md).  
  
## Comentarios  
 Una vez completado el inicio, el IDE ejecuta el comando indicado.  Si se usa este modificador, el IDE no muestra la página principal de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] al iniciarse.  
  
 Si un complemento muestra un comando, puede utilizar este modificador para iniciar el complemento desde la línea de comandos.  Para obtener más información, vea [Cómo: Controlar complementos con el Administrador de complementos](../Topic/How%20to:%20Control%20Add-Ins%20By%20Using%20the%20Add-In%20Manager.md).  
  
## Ejemplo  
 Este ejemplo inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y ejecuta automáticamente la macro Open Favorite Files.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)