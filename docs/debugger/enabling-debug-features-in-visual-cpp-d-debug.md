---
title: "Habilitar las caracter&#237;sticas de depuraci&#243;n en Visual C++ (/D_DEBUG) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "/D_DEBUG (opción del compilador) [C++]"
  - "_DEBUG (macro)"
  - "aserciones, habilitar características de depuración"
  - "D_DEBUG (opción del compilador)"
  - "compilaciones de depuración, MFC"
  - "depurar [C++], habilitar características de depuración"
  - "depurar [MFC], habilitar características de depuración"
  - "MFC (bibliotecas), versión de depuración"
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Habilitar las caracter&#237;sticas de depuraci&#243;n en Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], las características de depuración, como las aserciones, se habilitan al compilar el programa con el símbolo **\_DEBUG** definido.  Puede definir **\_DEBUG** de dos maneras:  
  
-   Especifique **\#define \_DEBUG** en el código fuente o  
  
-   Especifique la opción de compilador **\/D\_DEBUG**. \(Si crea el proyecto en Visual Studio utilizando asistentes, **\/D\_DEBUG** se define automáticamente en la configuración de depuración.\)  
  
 Cuando se define **\_DEBUG**, el compilador compila las secciones de código entre **\#ifdef \_DEBUG** y `#endif`.  
  
 La configuración de depuración de un programa MFC debe vincular con la versión de depuración de la biblioteca MFC.  Los archivos de encabezado de MFC determinan la versión correcta de la biblioteca MFC con la que se debe vincular a partir de los símbolos que haya definido, como **\_DEBUG** y **\_UNICODE**.  Para obtener información detallada, vea [Versiones de la biblioteca MFC](/visual-cpp/mfc/mfc-library-versions).  
  
## Vea también  
 [Depuración de código nativo](../debugger/debugging-native-code.md)   
 [Configuración del proyecto para una configuración de depuración de C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)