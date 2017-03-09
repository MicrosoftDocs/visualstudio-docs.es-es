---
title: "Error de MSBuild MSB8031 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSB8031"
ms.assetid: ebfaca51-fd91-4b04-8194-b4fdededd5fe
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB8031
MSB8031  
  
 Para utilizar la codificación de MBCS en proyectos MFC, debe descargar e instalar una biblioteca adicional.  
  
 Las versiones de MBCS de los archivos DLL de MFC no se incluyen en Visual Studio, pero están disponibles en el complemento de MFC MBCS DLL, que puede descargar si es un cliente de Visual Studio.  Si no instala el complemento e intenta compilar un proyecto MFC que utiliza el juego de caracteres MBCS, el vinculador no encontrará los archivos DLL y la compilación no se realizará correctamente.  
  
### Para corregir este error  
  
1.  [Descargar el complemento de DLL MBCS MFC](http://go.microsoft.com/fwlink/?LinkId=299009) del Centro de descargas de MSDN o, si le resulta más práctico, convierta el proyecto al juego de caracteres UNICODE.  
  
## Vea también  
 [Complemento DLL de MBCS para MFC](/visual-cpp/mfc/mfc-mbcs-dll-add-on)