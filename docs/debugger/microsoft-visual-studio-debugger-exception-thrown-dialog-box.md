---
title: "Depurador de Microsoft Visual Studio (se produjo una excepci&#243;n) (Cuadro de di&#225;logo) | Microsoft Docs"
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
  - "vs.debug.exceptions.thrown"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Depurador de Microsoft Visual Studio: se inició una excepción (cuadro de diálogo)"
  - "control de excepciones, durante la depuración"
  - "depurador, excepciones"
  - "producir excepciones, durante la depuración"
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurador de Microsoft Visual Studio (se produjo una excepci&#243;n) (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se ha producido una excepción en el programa.  Este cuadro de diálogo informa sobre la clase de excepción producida.  El código necesita tratar esta excepción.  Puede elegir entre las siguientes opciones para controlar la excepción:  
  
 **Inter**  
 Permite a la ejecución interrumpir el depurador.  El controlador de excepciones no se invoca antes de la interrupción.  Si continúa desde la interrupción, se invocará al controlador de excepciones.  
  
 **Continue**  
 Permite que continúe la ejecución y ofrece al controlador de excepciones una oportunidad para controlar la excepción.  Esta opción no está disponible para algunos tipos de excepciones.  **Continuar** permitirá que la aplicación siga adelante.  En una aplicación nativa, se volverá a producir la excepción.  En una aplicación administrada, hará que el programa termine o que una aplicación host controle la excepción.  
  
> [!NOTE]
>  No es posible continuar después de una excepción no controlada en el código administrado.  Si elige **Continuar** después de una excepción no controlada en código administrado, la depuración se detendrá.  
  
 **Ignore**  
 Permite que la ejecución continúe sin invocar al controlador de excepciones.  Puesto que no se invoca al controlador de excepciones, puede provocar otras consecuencias, tales como errores y excepciones adicionales.  Esta opción no está disponible para algunos tipos de excepciones.  
  
## Vea también  
 [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)   
 [Procedimientos recomendados para excepciones](../Topic/Best%20Practices%20for%20Exceptions.md)   
 [Control de excepciones](/visual-cpp/windows/exception-handling-cpp-component-extensions)