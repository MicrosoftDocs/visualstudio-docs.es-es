---
title: 'Cómo: depurar en un clúster de alto rendimiento | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-perfomance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c5d57e1ff9a4ab082698b1c5d31b09a668cdc1c5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262555"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Cómo: Depurar en un clúster de alto rendimiento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La depuración de un programa multiproceso en un clúster de alto rendimiento es similar a la depuración de un programa normal en un equipo remoto. Sin embargo, hay algunas consideraciones adicionales. Para conocer los requisitos de configuración remotos generales, vea [depuración remota](../debugger/remote-debugging.md).  
  
 Al depurar en un clúster de alto rendimiento, puede utilizar todas las ventanas de depuración de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y las técnicas que están disponibles para la depuración remota. Sin embargo, dado que está depurando de forma remota, la ventana de la consola externa no está disponible.  
  
 El **subprocesos** ventana y **procesos** son especialmente útiles para depurar aplicaciones paralelas. Para obtener sugerencias sobre cómo usar estas ventanas, vea [Cómo: utilizar la ventana procesos](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) y [Cómo: utilizar la ventana subprocesos](../debugger/how-to-use-the-threads-window.md).  
  
 En los procedimientos siguientes se presentan algunas técnicas que son especialmente útiles para depurar en un clúster de alto rendimiento.  
  
 Al depurar una aplicación paralela, puede establecer un punto de interrupción en un subproceso, proceso o equipo determinado. Para hacer esto, cree un punto de interrupción normal y, a continuación, agregue un filtro de punto de interrupción.  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>Para abrir el cuadro de diálogo Filtro del punto de interrupción  
  
1.  Haga clic en un glifo de punto de interrupción en una ventana de código fuente, el **desensamblado** ventana, el **pila de llamadas** ventana, o la **puntos de interrupción** ventana.  
  
2.  En el menú contextual, haga clic en **filtro**. Esta opción puede aparecer en la parte superior de bajo nivel o en el submenú **puntos de interrupción**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>Para establecer un punto de interrupción en un equipo concreto  
  
1.  Obtener el nombre del equipo desde el **procesos** ventana.  
  
2.  Seleccione un punto de interrupción y abra el **filtro del punto de interrupción** cuadro de diálogo como se describe en el procedimiento anterior.  
  
3.  En el **filtro del punto de interrupción** cuadro de diálogo, escriba:  
  
     MachineName =*nombredelamáquina*  
  
     Para crear un filtro más complejo, puede combinar cláusulas con `&`, el operador AND, `||`, el operador OR, `!`, el operador NOT y paréntesis.  
  
4.  Haga clic en **Aceptar**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>Para establecer un punto de interrupción en un proceso concreto  
  
1.  Obtenga el nombre o número de Id. de proceso del **procesos** ventana.  
  
2.  Seleccione un punto de interrupción y abra el **filtro del punto de interrupción** cuadro de diálogo como se muestra en el primer procedimiento.  
  
3.  En el **filtro del punto de interrupción** cuadro de diálogo, escriba:  
  
     `ProcessName =`  *yourprocessname*  
  
     -O bien-  
  
     `ProcessID =` *yourprocessIDnumber*  
  
     Para crear un filtro más complejo, puede combinar cláusulas con `&`, el operador AND, `||`, el operador OR, `!`, el operador NOT y paréntesis.  
  
4.  Haga clic en **Aceptar**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Para establecer un punto de interrupción en un subproceso concreto  
  
1.  Obtiene el nombre del subproceso o subprocesos el número de Id. de la **subprocesos** ventana.  
  
2.  Seleccione un punto de interrupción y abra el **filtro del punto de interrupción** cuadro de diálogo como se describe en el primer procedimiento.  
  
3.  En el **filtro del punto de interrupción** cuadro de diálogo, escriba:  
  
     `ThreadName =` *yourthreadname*  
  
     -O bien-  
  
     `ThreadID =` *yourthreadIDnumber*  
  
     Para crear un filtro más complejo, puede combinar cláusulas con `&`, el operador AND, `||`, el operador OR, `!`, el operador NOT y paréntesis.  
  
4.  Haga clic en **Aceptar**.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo crear un filtro para un punto de interrupción en un equipo denominado `marvin` y un subproceso denominado `fourier1`.  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Depuración remota](../debugger/remote-debugging.md)   
 [Cómo: utilizar la ventana procesos](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Cómo: utilizar la ventana subprocesos](../debugger/how-to-use-the-threads-window.md)   
 [Procesos y subprocesos](http://msdn.microsoft.com/en-us/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Usar puntos de interrupción](../debugger/using-breakpoints.md)



