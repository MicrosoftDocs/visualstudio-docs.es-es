---
title: "Archivo ejecutable para sesi&#243;n de depuraci&#243;n (Cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.exefordebug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "archivos ejecutables, especificar en la depuración"
  - "DLL, depurar"
  - "depurador, cuadro de diálogo Ejecutable para sesión de depuración"
  - "Archivo ejecutable para sesión de depuración (cuadro de diálogo)"
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Archivo ejecutable para sesi&#243;n de depuraci&#243;n (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este cuadro de diálogo aparece si se intenta depurar un archivo DLL para el que no se ha especificado ningún archivo ejecutable.  Visual Studio no puede iniciar un archivo DLL directamente.  En su lugar, iniciará el archivo ejecutable especificado.  Puede depurar el archivo DLL cuando lo llame el archivo ejecutable.  
  
 **Nombre del archivo ejecutable**  
 Escriba el nombre de ruta de acceso a un archivo ejecutable que llama al archivo DLL que está depurando.  
  
 **Dirección URL del proyecto \(solo servidor ATL\)**  
 Si está depurando un archivo DLL de un servidor ATL, escriba la dirección URL en la que se puede encontrar el proyecto.  
  
 Una vez escrita, esta configuración se almacena en las Páginas de propiedades del proyecto, por lo que no hace falta volver a escribirla para las siguientes sesiones de depuración.  Si necesita cambiar la configuración, puede abrir las Páginas de propiedades y cambiar los valores.  Para obtener más información sobre cómo especificar un archivo ejecutable para la sesión de depuración, vea [Depurar archivos DLL](../debugger/how-to-debug-native-dlls.md).  
  
## Vea también  
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)