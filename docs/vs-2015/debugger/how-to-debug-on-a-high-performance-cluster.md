---
title: Procedimiento Depurar en un clúster de alto rendimiento | Documentos de Microsoft
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
- cluster debugging
- high-performance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4487b168c3d405b2449bcfb9515e60f0ea67ed1
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65702692"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Procedimiento Depuración en un clúster de alto rendimiento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La depuración de un programa multiproceso en un clúster de alto rendimiento es similar a la depuración de un programa normal en un equipo remoto. Sin embargo, hay algunas consideraciones adicionales. Para conocer los requisitos de configuración remotos generales, vea [depuración remota](../debugger/remote-debugging.md).  
  
 Al depurar en un clúster de alto rendimiento, puede utilizar todas las ventanas de depuración de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y las técnicas que están disponibles para la depuración remota. Sin embargo, dado que está depurando de forma remota, la ventana de la consola externa no está disponible.  
  
 Las ventanas **Procesos** y **Subprocesos** son especialmente útiles para depurar aplicaciones paralelas. Para obtener sugerencias sobre cómo usar estas ventanas, vea [Cómo: Utilice la ventana procesos](https://msdn.microsoft.com/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) y [Cómo: Utilice la ventana subprocesos](../debugger/how-to-use-the-threads-window.md).  
  
 En los procedimientos siguientes se presentan algunas técnicas que son especialmente útiles para depurar en un clúster de alto rendimiento.  
  
 Al depurar una aplicación paralela, puede establecer un punto de interrupción en un subproceso, proceso o equipo determinado. Para hacer esto, cree un punto de interrupción normal y, a continuación, agregue un filtro de punto de interrupción.  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>Para abrir el cuadro de diálogo Filtro del punto de interrupción  
  
1. Haga clic con el botón derecho del mouse en un glifo de punto de interrupción en la ventana Código fuente, **Desensamblado**, **Pila de llamadas** o **Puntos de interrupción**.  
  
2. En el menú contextual, haga clic en **Filtro**. Esta opción puede aparecer en el nivel superior o en el submenú de **Puntos de interrupción**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>Para establecer un punto de interrupción en un equipo concreto  
  
1. Obtenga el nombre del equipo en la ventana **Procesos**.  
  
2. Seleccione un punto de interrupción y abra el cuadro de diálogo **Filtro del punto de interrupción** como se describió en el procedimiento anterior.  
  
3. En el cuadro de diálogo **Filtro del punto de interrupción**, escriba:  
  
     MachineName =*nombreDelEquipo*  
  
     Para crear un filtro más complejo, puede combinar cláusulas con `&`, el operador AND, `||`, el operador OR, `!`, el operador NOT y paréntesis.  
  
4. Haga clic en **Aceptar**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>Para establecer un punto de interrupción en un proceso concreto  
  
1. Obtenga el nombre o el número de id. del proceso en la ventana **Procesos**.  
  
2. Seleccione un punto de interrupción y abra el cuadro de diálogo **Filtro del punto de interrupción** tal como se describió en el primer procedimiento.  
  
3. En el cuadro de diálogo **Filtro del punto de interrupción**, escriba:  
  
     `ProcessName =`  *nombreDelProceso*  
  
     -O bien-  
  
     `ProcessID =` *númeroDeIddelProceso*  
  
     Para crear un filtro más complejo, puede combinar cláusulas con `&`, el operador AND, `||`, el operador OR, `!`, el operador NOT y paréntesis.  
  
4. Haga clic en **Aceptar**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Para establecer un punto de interrupción en un subproceso concreto  
  
1. Obtenga el nombre o el número de id. del subproceso en la ventana **Subprocesos**.  
  
2. Seleccione un punto de interrupción y abra el cuadro de diálogo **Filtro del punto de interrupción** tal como se describió en el primer procedimiento.  
  
3. En el cuadro de diálogo **Filtro del punto de interrupción**, escriba:  
  
     `ThreadName =` *nombreDelSubproceso*  
  
     -O bien-  
  
     `ThreadID =` *númeroDeIdDelSubproceso*  
  
     Para crear un filtro más complejo, puede combinar cláusulas con `&`, el operador AND, `||`, el operador OR, `!`, el operador NOT y paréntesis.  
  
4. Haga clic en **Aceptar**.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo crear un filtro para un punto de interrupción en un equipo denominado `marvin` y un subproceso denominado `fourier1`.  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## <a name="see-also"></a>Vea también  
 [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Depuración remota](../debugger/remote-debugging.md)   
 [Cómo: Utilice la ventana procesos](https://msdn.microsoft.com/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Cómo: Utilice la ventana subprocesos](../debugger/how-to-use-the-threads-window.md)   
 [Procesos y subprocesos](https://msdn.microsoft.com/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Usar puntos de interrupción](../debugger/using-breakpoints.md)
