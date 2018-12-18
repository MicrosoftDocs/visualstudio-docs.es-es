---
title: 'Cómo: depurar en un clúster de alto rendimiento | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-perfomance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9964621c216d058581d9298956ba90ac6cdbef86
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280797"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Cómo: Depurar en un clúster de alto rendimiento
La depuración de un programa multiproceso en un clúster de alto rendimiento es similar a la depuración de un programa normal en un equipo remoto. Sin embargo, hay algunas consideraciones adicionales. Para conocer los requisitos de configuración remotos generales, vea [depuración remota](../debugger/remote-debugging.md).  
  
 Al depurar en un clúster de alto rendimiento, puede utilizar todas las ventanas de depuración de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y las técnicas que están disponibles para la depuración remota. Sin embargo, dado que está depurando de forma remota, la ventana de la consola externa no está disponible.  
  
 El **subprocesos** ventana y **procesos** son especialmente útiles para depurar aplicaciones paralelas. Para obtener sugerencias sobre cómo usar estas ventanas, vea [Cómo: utilizar la ventana procesos](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100)) y [Tutorial: depurar con la ventana subprocesos](../debugger/how-to-use-the-threads-window.md).  
  
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
  
`(MachineName = marvin) & (ThreadName = fourier1)`  

  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Depuración remota](../debugger/remote-debugging.md)   
 [Cómo: utilizar la ventana procesos](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100))   
 [Empezar a depurar aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md)   
 [Procesos y subprocesos](/previous-versions/visualstudio/visual-studio-2010/ms164740(v=vs.100))   
 [Usar puntos de interrupción](../debugger/using-breakpoints.md)