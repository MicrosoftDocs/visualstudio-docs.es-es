---
title: Representaciones de DateTime y TimeSpan de Windows Runtime | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime dates and times
- TimeSpan [JavaScript]
- DateTime [JavaScript]
ms.assetid: 9743e9ac-9054-463e-8264-427183e4905f
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d7c394b57eb0215e3dff857d935b367e602c2b0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="windows-runtime-datetime-and-timespan-representations"></a>Representaciones de DateTime y TimeSpan de Windows Runtime
La representación de fechas y horas en JavaScript es diferente de la versión de Windows Runtime. La estructura [DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx) de Windows Runtime se representa en JavaScript como un elemento [Date](../javascript/reference/date-object-javascript.md) que tiene una memoria auxiliar que coincide con los datos de `DateTime` (y tiene un intervalo y una precisión diferentes del elemento `Date` de JavaScript). Si modifica este objeto `Date` personalizado, se convierte en un `Date` estándar de JavaScript y pierde precisión. Los valores `Date` de JavaScript se pueden pasar a `DateTime` de Windows en tiempo de ejecución y se les comprobará el intervalo, lo que puede provocar excepciones de cálculo de referencias.  
  
 La estructura [TimeSpan](http://msdn.microsoft.com/en-us/c5defb66-819c-4796-85b5-07ed249a5d86) de Windows Runtime se convierte a milisegundos y se devuelve como un número de JavaScript.  
  
## <a name="see-also"></a>Vea también  
 [Uso de Windows Runtime en JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)