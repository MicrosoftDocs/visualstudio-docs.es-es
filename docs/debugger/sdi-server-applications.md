---
title: "Aplicaciones de servidor SDI | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "aplicaciones de servidor SDI"
  - "aplicaciones de servidor SDI, depurar"
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Aplicaciones de servidor SDI
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si está depurando una aplicación de servidor SDI, debe especificar `/Embedding` o `/Automation` en la propiedad **Argumentos de la línea de comandos** del cuadro de diálogo Páginas de propiedades de *Project* de los proyectos de C\/C\+\+, C\# o Visual Basic.  
  
 Con los argumentos de esta línea de comandos, el depurador puede iniciar la aplicación de servidor como si se iniciara desde un contenedor.  Después, al iniciar el contenedor desde el Administrador de programas o desde el Administrador de archivos, el contenedor utilizará la instancia del servidor que se inició en el depurador.  
  
## Encontrar la propiedad Argumentos de la línea de comandos  
 Para tener acceso al cuadro de diálogo Páginas de propiedades de *Project*, haga clic con el botón secundario en el proyecto desde el Explorador de soluciones y, a continuación, elija Propiedades en el menú contextual.  Para buscar la propiedad Argumentos de la línea de comandos, haga clic en la ficha Depurar y vaya a Opciones de inicio.  
  
## Vea también  
 [Depurar COM y ActiveX](../debugger/com-and-activex-debugging.md)   
 [Cómo: Depurar servidores COM](../debugger/how-to-debug-com-servers.md)