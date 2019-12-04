---
title: 'DA0030: Recopilar medidas de interacción de capas para proyectos de base de datos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 26b0905882ef8ec2e3fcddc4cf699ecae7dbe7a4
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777481"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: Recopilar medidas de interacción de capas para proyectos de base de datos

|||
|-|-|
|Identificador de regla|DA0030|
|Categoría|Uso de Herramientas de generación de perfiles|
|Método de generación de perfiles|Muestreo|
|Mensaje|La recopilación de mediciones de interacción para aplicaciones de varias capas ayudará a comprender los modelos de uso de bases de datos y las demoras en el acceso a datos clave. Intente generar de nuevo el perfil de la aplicación con la opción de generación de perfiles de interacción de capas habilitada.|
|Tipo de regla|Información|

## <a name="cause"></a>Motivo
 Las llamadas a los métodos <xref:System.Data> constituyen una proporción considerable de los datos de generación de perfiles; además, no ha recopilado datos de interacción de capas en la generación de perfiles. Considere la opción de volver a generar los perfiles y agregar los datos de interacción de capas.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla se activa siempre que hay una actividad significativa en las funciones que residen en los espacios de nombres System.Data, incluido <xref:System.Data.Linq><xref:System.Data.Linq>.

 Las aplicaciones con varias capas usan los servicios superpuestos para su presentación y niveles de datos. Normalmente, el nivel de datos es un proceso independiente que ejecuta un sistema de administración de bases de datos, como Microsoft SQL Server. El nivel de datos puede incluso ejecutarse en una máquina distinta a la del resto de la aplicación. Los perfiles de muestreo proporcionan una ligera introducción a las funciones y servicios que se ejecutan fuera de proceso o de forma remota.

 Las herramientas de generación de perfiles pueden recopilar información sobre el control de tiempo de las aplicaciones de varias capas que interactúan con un nivel de datos de Microsoft SQL Server mediante llamadas asincrónicas a los servicios ADO.NET. Debe habilitar explícitamente la generación de perfiles de interacción de capas. No está activada de forma predeterminada.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Esta regla solo tiene un fin informativo y es posible que no necesite acción correctora alguna.

 Para obtener información sobre cómo agregar datos de interacción de capas a los datos de generación de perfiles desde el IDE de Visual Studio, vea [Recopilar datos de interacción de capas](../profiling/collecting-tier-interaction-data.md). Para obtener información sobre cómo agregar datos de interacción de capas desde la línea de comandos, vea [Recopilar datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md).
