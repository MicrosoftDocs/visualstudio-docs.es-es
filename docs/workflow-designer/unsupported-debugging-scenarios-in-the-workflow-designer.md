---
title: "Escenarios de depuraci&#243;n no admitidos en el Dise&#241;ador de flujo de trabajo | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "sdanie"
manager: "erikre"
---
# Escenarios de depuraci&#243;n no admitidos en el Dise&#241;ador de flujo de trabajo
El Diseñador de flujo de trabajo de [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] tiene muchas características nuevas, pero todavía hay algunos escenarios de depuración que no admite.En este documento se detallan los escenarios de depuración que no admite el Diseñador de flujo de trabajo.  
  
-   No se puede continuar la ejecución una vez editado el código.  
  
-   No se puede continuar la ejecución desde un punto arbitrario en el flujo de trabajo \(Establecer siguiente\).  
  
-   No se puede continuar la ejecución hasta que se alcanza el cursor \(Ejecutar hasta el cursor\).  
  
-   El diseñador de flujo de trabajo no se puede utilizar para depurar flujos de trabajo creados en el código sin usar el diseñador.  
  
-   Los flujos de trabajo creados en versiones anteriores de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] no se pueden depurar en el diseñador de [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)].  
  
-   No se pueden definir puntos de interrupción en los vínculos entre actividades o nodos <xref:System.Activities.Statements.Flowchart>.  
  
-   El portapapeles no está disponible durante la depuración.  
  
-   No se retienen los puntos de interrupción cuando se copian o pegan las actividades.  
  
-   No se pueden establecer puntos de interrupción en la ventana de pila de llamadas.  
  
-   Al crear puntos de interrupción en el diseñador, no se usan las opciones **Líneas** y **Carácter** del cuadro de diálogo **Nuevo punto de interrupción**.  
  
-   La ventana o el menú contextual Punto de interrupción no admiten las siguientes columnas u opciones para la depuración de flujos de trabajo:  
  
    -   Condición  
  
    -   Número de llamadas  
  
    -   Al visitar  
  
    -   Función  
  
    -   Datos  
  
    -   Proceso  
  
    -   Ir al desensamblado