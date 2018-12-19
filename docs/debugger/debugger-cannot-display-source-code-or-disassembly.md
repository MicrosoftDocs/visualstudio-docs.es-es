---
title: No puede mostrar el depurador de código fuente o el desensamblado
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ea95a2bb4c29f8a23fd597173a10a838baca051c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063971"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>El depurador no puede mostrar el código fuente o el desensamblado
Este error reza como sigue:  
  
 El depurador no puede mostrar el código fuente o el desensamblado disponibles para la ubicación actual donde se ha detenido la ejecución.  
  
 Este error puede producirse por una serie de motivos:  
  
-   Puede haber alcanzado un punto de interrupción en una ubicación para la que no existe código fuente, mientras depura un lenguaje que no admite desensamblado. Abra el **puntos de interrupción** ventana, localice el punto de interrupción y elimínelo.  
  
-   Si está depurando un script, puede haber alcanzado un punto de interrupción cuando no existía ningún subproceso en el programa. Elija **Paso** o **Continuar** en el menú **Depurar** para reanudar la depuración.  
  
-   Las consideraciones de seguridad pueden haber impedido que el depurador leyera datos de la pila, subprocesos, registros u otra información de contexto del programa que se está depurando. Esta situación es bastante probable si se está depurando una aplicación Web y no se dispone de permiso para obtener acceso al directorio virtual. Haga que la seguridad para el directorio virtual sea "anónimo" y pruebe de nuevo.  
  
## <a name="see-also"></a>Vea también  
 [Depuración en Visual Studio](../debugger/index.md) [paseo por las características del depurador](../debugger/debugger-feature-tour.md)   
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)