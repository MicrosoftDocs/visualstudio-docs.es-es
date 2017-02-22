---
title: "C&#243;mo depurar funciones de la API de Windows | Microsoft Docs"
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
  - "vs.debug.api"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "API, depurar"
  - "depurar [C++], funciones de la API de Windows"
  - "símbolos de NT y depuración de funciones de la API de Windows"
  - "funciones de la API de Windows, depurar"
  - "API de Windows, depurar funciones de la API"
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo depurar funciones de la API de Windows
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si desea depurar una función de la API de Windows que tiene símbolos de NT cargados, deberá hacer lo siguiente.  
  
### Para establecer un punto de interrupción en una función API de Windows con símbolos de NT cargados  
  
-   Escriba el nombre de la función junto con el nombre del archivo DLL en el que se encuentra la función.  En el código de 32 bits, utilice el formato representativo del nombre de la función.  Para establecer un punto de interrupción en **MessageBeep**, por ejemplo, debe especificar lo siguiente:  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Para obtener el nombre representativo, vea [Ver nombres representativos](http://msdn.microsoft.com/es-es/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## Vea también  
 [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)