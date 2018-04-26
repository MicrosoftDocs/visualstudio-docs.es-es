---
title: Escenarios de depuración no admitidos en el Diseñador de flujo de trabajo
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2b876df1b7d997f3999c119d02abd593a88e6d5e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Escenarios de depuración no admitidos en el Diseñador de flujo de trabajo

El Diseñador de flujo de trabajo en .NET Framework 4 tiene muchas características nuevas, pero todavía hay algunos escenarios de depuración no admite.

Éstos son el Diseñador de flujo de trabajo no admitido escenarios de depuración:

-   No se puede continuar la ejecución una vez editado el código.

-   No se puede continuar la ejecución desde un punto arbitrario en el flujo de trabajo (Establecer siguiente).

-   No se puede continuar la ejecución hasta que se alcanza el cursor (Ejecutar hasta el cursor).

-   El diseñador de flujo de trabajo no se puede utilizar para depurar flujos de trabajo creados en el código sin usar el diseñador.

-   No se pueden depurar flujos de trabajo creados en versiones anteriores de Windows Workflow Foundation (WF) en el Diseñador de .NET Framework 4.

-   No se pueden definir puntos de interrupción en los vínculos entre actividades o nodos <xref:System.Activities.Statements.Flowchart>.

-   El portapapeles no está disponible durante la depuración.

-   No se retienen los puntos de interrupción cuando se copian o pegan las actividades.

-   No se pueden establecer puntos de interrupción en la ventana de pila de llamadas.

-   Al crear los puntos de interrupción en el diseñador, el **línea** y **caracteres** configuración en el **nuevo punto de interrupción** no se utiliza el cuadro de diálogo.

-   La ventana o el menú contextual Punto de interrupción no admiten las siguientes columnas u opciones para la depuración de flujos de trabajo:

    -   Condición

    -   Número de llamadas

    -   Al visitar

    -   Función

    -   Datos

    -   Proceso

    -   Ir al desensamblado