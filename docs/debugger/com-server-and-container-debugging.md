---
title: "Depuraci&#243;n de servidores y contenedores COM | Microsoft Docs"
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
  - "vs.debug.com"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depuración del contenedor de controles ActiveX [Visual Studio]"
  - "controles ActiveX, depurar"
  - "COM [Visual Studio], depurar"
  - "servidores COM, depurar"
  - "depurar controles ActiveX"
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depuraci&#243;n de servidores y contenedores COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las aplicaciones COM realizan una serie de tareas fuera del control directo del programador.  La comunicación entre archivos DLL, los contadores de uso en objetos y las operaciones del Portapapeles son sólo algunas de las áreas en las que se puede encontrar un comportamiento inesperado.  Cuando esto ocurre, el primer paso es determinar el origen del problema.  
  
 El depurador de Visual Studio permite la depuración superficial o exhaustiva de contenedores y servidores.  Esto incluye la capacidad de ejecutar instrucciones paso a paso entre llamadas a procedimientos remotos \(RPC\).  
  
## En este tema  
  
1.  [Depurar un servidor COM y un contenedor en la misma solución](../debugger/com-server-and-container-debugging.md#BKMK_COMServerandContainerintheSameSolution)  
  
2.  [Depurar una aplicación de servidor sin información del contenedor](../debugger/com-server-and-container-debugging.md#BKMK_ServerApplicationWithoutContainerInformation)  
  
3.  [Depurar una aplicación de Aislamiento de servidor y dominio (SDI)](../debugger/com-server-and-container-debugging.md#BKMK_DebuggingaServerandDomainIsolationSDIApplication)  
  
##  <a name="BKMK_COMServerandContainerintheSameSolution"></a> Depurar un servidor COM y un contenedor en la misma solución  
 Se puede depurar un servidor y contenedor COM mediante dos proyectos dentro de la misma solución.  Establezca los puntos de interrupción apropiados en cada proyecto y depure.  Cuando el contenedor llama al servidor que visita un punto de interrupción, el contenedor esperará hasta que regrese el código del servidor, es decir, hasta que termine de depurarlo.  
  
 La depuración de un contenedor COM es similar a la de un programa estándar.  Una diferencia está en la depuración de un evento que genera una devolución de llamada \(por ejemplo, al arrastrar datos a la aplicación contenedora\).  En este caso, debe establecer un punto de interrupción en la función de devolución de llamada.  
  
##  <a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Depurar una aplicación de servidor sin información del contenedor  
 Si no tiene o no desea utilizar información de depuración para la aplicación contenedora, puede empezar el proceso de depuración de la aplicación del servidor en tres pasos:  
  
1.  Comience a depurar el servidor como si se tratara de una aplicación normal.  
  
2.  Establezca puntos de interrupción donde desee.  
  
3.  Inicie la aplicación contenedora.  
  
##  <a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Depurar una aplicación de Aislamiento de servidor y dominio \(SDI\)  
 Si está depurando una aplicación de servidor SDI, debe especificar `/Embedding` o `/Automation` en la propiedad **Argumentos de la línea de comandos** del cuadro de diálogo Páginas de propiedades de *proyecto* de los proyectos de C\/C\+\+, C\# o Visual Basic.  
  
 Con los argumentos de esta línea de comandos, el depurador puede iniciar la aplicación de servidor como si se iniciara desde un contenedor.  Después, al iniciar el contenedor desde el Administrador de programas o desde el Administrador de archivos, el contenedor utilizará la instancia del servidor que se inició en el depurador.  
  
 Para tener acceso al cuadro de diálogo Páginas de propiedades de *proyecto*, haga clic con el botón secundario en el proyecto desde el Explorador de soluciones y, a continuación, elija Propiedades en el menú contextual.  Para buscar la propiedad Argumentos de la línea de comandos, haga clic en la ficha Depurar y vaya a Opciones de inicio.  
  
## Vea también  
 [Depurar COM y ActiveX](../debugger/com-and-activex-debugging.md)