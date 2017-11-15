---
title: "Propiedades de error especiales de los métodos de Windows Runtime asincrónicos | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45155584-06d8-4e7f-93a6-8564a93f643d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 120d8f699c8bedd0fe5762300203c5d5ec18e73e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="special-error-properties-from-asynchronous-windows-runtime-methods"></a>Propiedades de error especiales de los métodos asincrónicos de Windows Runtime
En JavaScript puede resultar difícil depurar los métodos de Windows Runtime asincrónicos, porque el error puede generarse desde cualquier parte intrincada de la pila de llamadas. El objeto `Error` de JavaScript tiene propiedades adicionales que solo aparecen cuando el error se genera desde un método de Windows Runtime asincrónico cuando la aplicación se ejecuta en modo de depuración.  
  
## <a name="special-error-properties"></a>Propiedades de error especiales  
 Un objeto de error que procede de una operación asincrónica de Windows Runtime errónea en modo de depuración tiene las siguientes propiedades especiales:  
  
-   `asyncOpSource` (objeto): obtiene información sobre la ubicación original donde se realizó la llamada que generó un error. `asyncOpSource.originatingCall` (cadena): muestra la ubicación en el código del usuario que originó la operación asincrónica.  
  
-   asyncOpType (cadena): obtiene el nombre del tipo de operación asincrónica que produjo el error.  
  
 Para obtener más información sobre los errores con operaciones asincrónicas, consulte:  
  
-   [Cómo controlar errores con promesas](https://msdn.microsoft.com/en-us/library/windows/apps/hh700337.aspx)  
  
-   [Solucionar errores de Windows en tiempo de ejecución](http://msdn.microsoft.com/en-us/1ef7d7df-82ac-441d-8ad0-54ab1318de64)