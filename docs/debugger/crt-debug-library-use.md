---
title: "Uso de la biblioteca de depuraci&#243;n CRT | Microsoft Docs"
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
  - "c.debug.runtime"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "/DEBUG (opción del vinculador) [C++]"
  - "/LDd (función del compilador) [C++]"
  - "/MDd (opción del compilador) [C++]"
  - "/MTd (opción del compilador) [C++]"
  - "crtdbg.h (archivo)"
  - "biblioteca de depuración"
  - "DEBUG (opción del vinculador) [C++]"
  - "depurar [CRT], biblioteca de depuración de CRT"
  - "LDd (función del compilador) [C++]"
  - "bibliotecas, biblioteca de depuración de CRT"
  - "MDd (opción del compilador) [C++]"
  - "MTd (opción del compilador) [C++]"
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Uso de la biblioteca de depuraci&#243;n CRT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La biblioteca en tiempo de ejecución de C \(CRT\) proporciona amplias capacidades de depuración.  Si desea utilizar una de las bibliotecas de depuración de CRT, debe crear un vínculo con [\/DEBUG](/visual-cpp/build/reference/debug-generate-debug-info) y compilar con **\/MDd**, **\/MTd** o **\/LDd**.  
  
## Comentarios  
 Las principales definiciones y macros para la depuración con CRT se encuentran en el archivo de encabezado CRTDBG.h.  
  
 Las funciones de las bibliotecas de depuración CRT se compilan con información de depuración \([\/Z7, \/Zd, \/Zi, \/ZI \(Formato de información de depuración\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)\) y sin optimización.  Algunas funciones contienen aserciones para comprobar los parámetros que se les pasan; además, se proporciona el código fuente.  Con este código fuente, se pueden ejecutar las funciones CRT paso a paso para confirmar si las funciones se comportan como se esperaba y para comprobar si existen parámetros o estados de memoria incorrectos. Parte de la tecnología de CRT es propietaria y no proporciona el código fuente para el tratamiento de excepciones, punto flotante y algunas otras rutinas.  
  
 Cuando se instala Visual C\+\+, existe la opción de instalar el código fuente de la biblioteca en tiempo de ejecución de C en el disco duro.  Si no se instala, se necesitará el CD\-ROM para ejecutar las funciones de CRT paso a paso.  
  
 Para obtener más información sobre las diversas bibliotecas en tiempo de ejecución que se pueden utilizar, vea [Bibliotecas en tiempo de ejecución de C](/visual-cpp/c-runtime-library/crt-library-features).  
  
## Vea también  
 [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md)   
 [\/MD, \/MT, \/LD \(Utilizar la biblioteca en tiempo de ejecución\)](/visual-cpp/build/reference/md-mt-ld-use-run-time-library)