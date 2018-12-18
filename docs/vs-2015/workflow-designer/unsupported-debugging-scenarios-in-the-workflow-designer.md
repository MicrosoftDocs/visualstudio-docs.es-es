---
title: No admite escenarios en el Diseñador de flujo de trabajo de depuración | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
caps.latest.revision: 4
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: aece5a71965a1935218027dd97b1b8363a646388
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184488"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Escenarios de depuración no admitidos en el Diseñador de flujo de trabajo
El Diseñador de flujo de trabajo de [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] tiene muchas características nuevas, pero todavía hay algunos escenarios de depuración que no admite. En este documento se detallan los escenarios de depuración que no admite el Diseñador de flujo de trabajo.  
  
-   No se puede continuar la ejecución una vez editado el código.  
  
-   No se puede continuar la ejecución desde un punto arbitrario en el flujo de trabajo (Establecer siguiente).  
  
-   No se puede continuar la ejecución hasta que se alcanza el cursor (Ejecutar hasta el cursor).  
  
-   El diseñador de flujo de trabajo no se puede utilizar para depurar flujos de trabajo creados en el código sin usar el diseñador.  
  
-   Los flujos de trabajo creados en versiones anteriores de [!INCLUDE[wf](../includes/wf-md.md)] no se pueden depurar en el diseñador de [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].  
  
-   No se pueden definir puntos de interrupción en los vínculos entre actividades o nodos <xref:System.Activities.Statements.Flowchart>.  
  
-   El portapapeles no está disponible durante la depuración.  
  
-   No se retienen los puntos de interrupción cuando se copian o pegan las actividades.  
  
-   No se pueden establecer puntos de interrupción en la ventana de pila de llamadas.  
  
-   Al crear los puntos de interrupción en el diseñador, el **línea** y **carácter** configuración en el **nuevo punto de interrupción** no se utiliza el cuadro de diálogo.  
  
-   La ventana o el menú contextual Punto de interrupción no admiten las siguientes columnas u opciones para la depuración de flujos de trabajo:  
  
    -   Condición  
  
    -   Número de llamadas  
  
    -   Al visitar  
  
    -   Función  
  
    -   Datos  
  
    -   Proceso  
  
    -   Ir al desensamblado