---
title: 'DA0029: Versión de CLR no admitida | Microsoft Docs'
description: Está intentando generar perfiles de una aplicación que usa .NET Framework 1.1, que no es compatible con Herramientas de generación de perfiles.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b3f5e5129bed479273e141af70121d5a344972e2
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465847"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Versión de CLR no admitida

|Elemento|Valor|
|-|-|
|Identificador de regla|DA0029|
|Categoría|Uso de Herramientas de generación de perfiles|
|Método de generación de perfiles|Generación de perfiles desde la línea de comandos|
|Mensaje|Se ha detectado una versión de CLR no admitida durante la recopilación. Puede que los símbolos administrados no se resuelvan correctamente.|
|Tipo de regla|Información.|

## <a name="cause"></a>Motivo
 Está intentando generar perfiles de una aplicación que usa [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)], que no es compatible con las herramientas de generación de perfiles.

## <a name="rule-description"></a>Descripción de la regla
 Esta advertencia se produce porque las herramientas de generación de perfiles no podrán resolver símbolos del código administrado que se ejecuta en la aplicación. Las herramientas de generación de perfiles no pueden resolver símbolos de código administrado para aplicaciones que ejecutan [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)].

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Ninguno.
