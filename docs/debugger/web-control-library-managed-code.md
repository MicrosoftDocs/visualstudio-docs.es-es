---
title: "Biblioteca de controles Web (c&#243;digo administrado) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "depurar [Visual Studio], bibliotecas de controles Web"
  - "depurar las DLL"
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Biblioteca de controles Web (c&#243;digo administrado)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La plantilla de proyecto Biblioteca de controles Web crea un archivo DLL.  Como la biblioteca de clases es un archivo DLL, no se puede ejecutar directamente.  Deberá crear una página de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] que incruste el control.  Para obtener más información, vea [Web Control Library Template](http://msdn.microsoft.com/es-es/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### Para depurar una biblioteca de controles web \(método 1\)  
  
1.  Abra un proyecto de Biblioteca de controles Web existente o cree uno nuevo.  
  
2.  Cree una página de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] que incruste el control.  
  
3.  En el sitio Web donde se hospede el instrumento de prueba de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], cree un subdirectorio denominado `/Code`.  
  
4.  Copie el código fuente del control en el subdirectorio `/Code`.  
  
5.  Abra el código fuente del subdirectorio `/Code` y establezca puntos de interrupción.  
  
6.  Abra una ventana del explorador con una dirección URL que apunte al instrumento de prueba.  Se alcanzará un punto de interrupción del control y podrá iniciar la depuración.  
  
### Para depurar una biblioteca de controles web \(método 2\)  
  
1.  Cree el proyecto de aplicación host y el proyecto de control web en la misma solución.  
  
2.  En el **Explorador de soluciones**, haga clic con el botón secundario en la aplicación hosts y elija **Agregar referencia**.  
  
3.  Agregue una referencia al proyecto de control Web.  
  
## Vea también  
 [Aplicaciones Web ASP.NET](../debugger/debugging-preparation-aspnet-web-applications.md)