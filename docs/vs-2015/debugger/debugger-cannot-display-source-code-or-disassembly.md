---
title: El depurador no puede mostrar el código fuente o el desensamblado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ce4460aecb634523de02f2e3f6929b206b415e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186502"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>El depurador no puede mostrar el código fuente o el desensamblado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este error reza como sigue:  
  
 El depurador no puede mostrar el código fuente o el desensamblado disponibles para la ubicación actual donde se ha detenido la ejecución.  
  
 Este error puede producirse por una serie de motivos:  
  
- Puede haber alcanzado un punto de interrupción en una ubicación para la que no existe código fuente, mientras depura un lenguaje que no admite desensamblado. Abra la ventana **Puntos de interrupción**, localice el punto de interrupción y elimínelo.  
  
- Si está depurando un script, puede haber alcanzado un punto de interrupción cuando no existía ningún subproceso en el programa. Elija **Paso** o **Continuar** en el menú **Depurar** para reanudar la depuración.  
  
- Las consideraciones de seguridad pueden haber impedido que el depurador leyera datos de la pila, subprocesos, registros u otra información de contexto del programa que se está depurando. Esta situación es bastante probable si se está depurando una aplicación Web y no se dispone de permiso para obtener acceso al directorio virtual. Haga que la seguridad para el directorio virtual sea "anónimo" y pruebe de nuevo.  
  
## <a name="see-also"></a>Consulte también  
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)   
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)
