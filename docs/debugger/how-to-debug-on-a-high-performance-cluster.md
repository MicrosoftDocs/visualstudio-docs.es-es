---
title: Procedimiento para depurar en un clúster de alto rendimiento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-performance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d95c6eeadfdf1bb90471997712299ae03a945be8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733666"
---
# <a name="how-to-debug-on-a-high-performance-cluster-c-visual-basic-c"></a>Procedimiento para depurar en un clúster de alto rendimiento (C#, Visual Basic, C++)

La depuración de un programa multiproceso en un clúster de alto rendimiento es similar a la depuración de un programa normal en un equipo remoto. Sin embargo, hay algunas consideraciones adicionales. Para obtener los requisitos de configuración remota generales, vea [Depuración remota](../debugger/remote-debugging.md).

 Al depurar en un clúster de alto rendimiento, puede utilizar todas las ventanas de depuración de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y las técnicas que están disponibles para la depuración remota. Sin embargo, dado que está depurando de forma remota, la ventana de la consola externa no está disponible.

 Las ventanas **Procesos** y **Subprocesos** son especialmente útiles para depurar aplicaciones paralelas. Para obtener sugerencias sobre el uso de estas ventanas, vea [Procedimiento para usar la ventana Procesos](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100)) y [Tutorial: Depuración con la ventana Subprocesos](../debugger/how-to-use-the-threads-window.md).

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

     `ProcessName =`  *nombre_del_proceso*

     -O bien-

     `ProcessID =` *número_de_id_del_proceso*

     Para crear un filtro más complejo, puede combinar cláusulas con `&`, el operador AND, `||`, el operador OR, `!`, el operador NOT y paréntesis.

4. Haga clic en **Aceptar**.

### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Para establecer un punto de interrupción en un subproceso concreto

1. Obtenga el nombre o el número de id. del subproceso en la ventana **Subprocesos**.

2. Seleccione un punto de interrupción y abra el cuadro de diálogo **Filtro del punto de interrupción** tal como se describió en el primer procedimiento.

3. En el cuadro de diálogo **Filtro del punto de interrupción**, escriba:

     `ThreadName =` *nombre_del_subproceso*

     -O bien-

     `ThreadID =` *número_de_id_del_subproceso*

     Para crear un filtro más complejo, puede combinar cláusulas con `&`, el operador AND, `||`, el operador OR, `!`, el operador NOT y paréntesis.

4. Haga clic en **Aceptar**.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra cómo crear un filtro para un punto de interrupción en un equipo denominado `marvin` y un subproceso denominado `fourier1`.

`(MachineName = marvin) & (ThreadName = fourier1)`

## <a name="see-also"></a>Vea también
- [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Remote Debugging](../debugger/remote-debugging.md)
- [Cómo: para usar la ventana Procesos](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100))
- [Introducción a la depuración de aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md)
- [Subprocesos y procesos](/previous-versions/visualstudio/visual-studio-2010/ms164740(v=vs.100))
- [Usar puntos de interrupción](../debugger/using-breakpoints.md)