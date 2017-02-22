---
title: "ShowWebBrowser (Comando) | Microsoft Docs"
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
  - "view.showwebbrowser"
helpviewer_keywords: 
  - "ShowWebBrowser (comando)"
  - "View.ShowWebBrowser (comando)"
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ShowWebBrowser (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Muestra la dirección URL especificada en una ventana de explorador web dentro del entorno de desarrollo integrado \(IDE\) o fuera de él.  
  
## Sintaxis  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## Argumentos  
 `URL`  
 Obligatorio.  Localizador de recursos universal \(URL\) del sitio Web.  
  
## Modificadores  
 \/new  
 Opcional.  Especifica que la página aparezca en una nueva instancia del explorador web.  
  
 \/ext  
 Opcional.  Especifica que la página aparezca en el explorador web predeterminado fuera del entorno de desarrollo integrado.  
  
## Comentarios  
 El alias para el comando **ShowWebBrowser** es **navigate** o **nav**.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra la página principal de MSDN Online en un explorador web fuera del IDE.  Se utiliza una instancia ya abierta en el explorador web; en el caso de que no hubiese ninguna instancia abierta, se iniciaría una nueva instancia.  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)