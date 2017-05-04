---
title: "Representaciones DateTime y TimeSpan de Windows en tiempo de ejecuci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DateTime [JavaScript]"
  - "JavaScript, Fechas y horas de Windows en tiempo de ejecución"
  - "TimeSpan [JavaScript]"
ms.assetid: 9743e9ac-9054-463e-8264-427183e4905f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Representaciones DateTime y TimeSpan de Windows en tiempo de ejecuci&#243;n
La representación de fechas y horas en JavaScript es diferente de la versión de Windows en tiempo de ejecución.  La estructura [DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx) de Windows en tiempo de ejecución se representa en JavaScript como [Date](../javascript/reference/date-object-javascript.md) con memoria auxiliar que coincide con los datos de `DateTime` \(y tiene un intervalo y una precisión distintos de `Date` de JavaScript\).  Si modifica este objeto `Date` personalizado, se convierte en un `Date` estándar de JavaScript y pierde precisión.  Los valores `Date` de JavaScript se pueden pasar a `DateTime` de Windows en tiempo de ejecución y se les comprobará el intervalo, lo que puede provocar excepciones de cálculo de referencias.  
  
 La estructura [TimeSpan](http://msdn.microsoft.com/es-es/c5defb66-819c-4796-85b5-07ed249a5d86) de Windows en tiempo de ejecución se convierte a milisegundos y se devuelve como un número de JavaScript.  
  
## Vea también  
 [Utilizar Windows en tiempo de ejecución en JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)