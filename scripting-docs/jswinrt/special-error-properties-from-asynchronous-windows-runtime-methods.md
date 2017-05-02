---
title: "Propiedades de error especiales de los m&#233;todos asincr&#243;nicos de Windows en tiempo de ejecuci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45155584-06d8-4e7f-93a6-8564a93f643d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Propiedades de error especiales de los m&#233;todos asincr&#243;nicos de Windows en tiempo de ejecuci&#243;n
Puede ser difícil depurar métodos asincrónicos de Windows en tiempo de ejecución en JavaScript porque el error se puede producir de en alguna parte en profundidad de la pila de llamadas.  El objeto `Error` de JavaScript tiene propiedades adicionales que solo aparecen cuando el error se produce desde un método asincrónico de Windows en tiempo de ejecución cuando la aplicación se ejecuta en modo de depuración.  
  
## Propiedades especiales de error  
 Un objeto de error resultante de una operación asincrónica con error de Windows en tiempo de ejecución en modo de depuración, tiene las propiedades especiales siguientes:  
  
-   `asyncOpSource` \(objeto\) recopila información sobre la ubicación original donde se realizó la llamada que generó un error.  La propiedad `asyncOpSource.originatingCall` \(cadena\) muestra la ubicación en el código de usuario que originó la operación asincrónica.  
  
-   asyncOpType \(cadena\) obtiene el nombre del tipo de operación asincrónica que provocó el error.  
  
 Para obtener más información acerca de errores con operaciones asincrónicas, vea:  
  
-   [How to handle errors with promises](http://msdn.microsoft.com/es-es/01d5a901-c4ea-46f6-8005-6d39c32203eb)  
  
-   [Solución de problemas de errores de Windows en tiempo de ejecución](http://msdn.microsoft.com/es-es/1ef7d7df-82ac-441d-8ad0-54ab1318de64)