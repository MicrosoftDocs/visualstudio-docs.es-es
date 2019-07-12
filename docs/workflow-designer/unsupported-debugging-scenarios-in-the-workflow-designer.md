---
title: Escenarios de depuración no admitidos en el Diseñador de flujo de trabajo
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9cda710a3a2f4945e96e706479996da0a1fa7e12
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825732"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Escenarios de depuración no admitidos en el Diseñador de flujo de trabajo

El Diseñador de flujo de trabajo no admite los siguientes escenarios de depuración:

- No se puede continuar la ejecución una vez editado el código.

- No se puede continuar la ejecución desde un punto arbitrario en el flujo de trabajo (Establecer siguiente).

- No se puede continuar la ejecución hasta que se alcanza el cursor (Ejecutar hasta el cursor).

- El diseñador de flujo de trabajo no se puede utilizar para depurar flujos de trabajo creados en el código sin usar el diseñador.

- No se puede depurar flujos de trabajo creados en versiones anteriores de Windows Workflow Foundation (WF) en .NET Framework 4 o posterior.

- No se pueden definir puntos de interrupción en los vínculos entre actividades o nodos <xref:System.Activities.Statements.Flowchart>.

- El portapapeles no está disponible durante la depuración.

- No se retienen los puntos de interrupción cuando se copian o pegan las actividades.

- No se pueden establecer puntos de interrupción en la ventana de pila de llamadas.

- Al crear los puntos de interrupción en el diseñador, el **línea** y **carácter** configuración en el **nuevo punto de interrupción** no se utiliza el cuadro de diálogo.

- La ventana o el menú contextual Punto de interrupción no admiten las siguientes columnas u opciones para la depuración de flujos de trabajo:

  - Condición

  - Número de llamadas

  - Al visitar

  - Función

  - Datos

  - Process

  - Ir al desensamblado
