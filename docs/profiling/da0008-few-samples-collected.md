---
title: 'DA0008: Pocos ejemplos recolectados | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4f80f4f08be3c2af8444a41209a8d19909c94a8f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897906"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Pocos ejemplos recolectados

|||  
|-|-|  
|Identificador de regla|DA0008|  
|Categoría|Uso de Herramientas de generación de perfiles|  
|Método de generación de perfiles|Muestreo|  
|Mensaje|Solo se recolectó un reducido número de ejemplos. Considere una ejecución más prolongada o una frecuencia de muestreo más rápida para obtener resultados más significativos.|  
|Tipo de regla|Información|  

## <a name="cause"></a>Motivo  
 Solo se recolectó un reducido número de ejemplos en la ejecución de generación de perfiles.  

## <a name="rule-description"></a>Descripción de la regla  
 Cuando se usa el método de muestreo, se debe recopilar un número estadísticamente significativo de muestras para garantizar que los datos representen el comportamiento real del programa. Para minimizar los errores de muestreo, debe intentar recopilar al menos 1000 muestras del comportamiento de ejecución de las instrucciones de programa. Si no recoge suficientes muestras, puede obtener datos erróneos al analizar los datos de generación de perfiles.  

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Considere la posibilidad de generar perfiles de una ejecución más prolongada de la aplicación o usar una velocidad de muestreo más rápida para obtener resultados estadísticamente significativos. Para obtener información sobre cómo cambiar la velocidad de muestreo en el IDE de Visual Studio, vea [Cómo: Elegir eventos de muestreo](../profiling/how-to-choose-sampling-events.md). Para obtener más información sobre cómo cambiar la velocidad de muestreo al usar la línea de comandos de las herramientas de generación de perfiles, consulte [Temporizador](../profiling/timer.md) en la referencia [VSPerfCmd](../profiling/vsperfcmd.md).