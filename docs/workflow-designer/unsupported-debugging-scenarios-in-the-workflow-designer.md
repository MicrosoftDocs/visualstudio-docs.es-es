---
title: Escenarios de depuración no admitidos
description: Obtenga información sobre los escenarios de depuración no admitidos en el Diseñador de flujo de trabajo, por ejemplo, "la ejecución no puede continuar después de que se haya editado el código".
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 4e98e2a75905f4c0a4c007691a99961dbcf1477c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996271"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Escenarios de depuración no admitidos en el Diseñador de flujo de trabajo

En el Diseñador de flujo de trabajo no se admiten los siguientes escenarios de depuración:

- No se puede continuar la ejecución una vez editado el código.

- No se puede continuar la ejecución desde un punto arbitrario en el flujo de trabajo (Establecer siguiente).

- No se puede continuar la ejecución hasta que se alcanza el cursor (Ejecutar hasta el cursor).

- El diseñador de flujo de trabajo no se puede utilizar para depurar flujos de trabajo creados en el código sin usar el diseñador.

- Los flujos de trabajo creados en versiones anteriores de Windows Workflow Foundation (WF) no se pueden depurar en .NET Framework 4 o posterior.

- No se pueden definir puntos de interrupción en los vínculos entre actividades o nodos <xref:System.Activities.Statements.Flowchart>.

- El portapapeles no está disponible durante la depuración.

- No se retienen los puntos de interrupción cuando se copian o pegan las actividades.

- No se pueden establecer puntos de interrupción en la ventana de pila de llamadas.

- Al crear puntos de interrupción en el diseñador, no se utilizan los valores de **línea** y de **carácter** en el cuadro de diálogo **nuevo punto de interrupción** .

- La ventana o el menú contextual Punto de interrupción no admiten las siguientes columnas u opciones para la depuración de flujos de trabajo:

  - Condición

  - Número de llamadas

  - Al visitar

  - Función

  - data

  - Proceso

  - Ir al desensamblado
