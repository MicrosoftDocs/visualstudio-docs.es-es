---
title: 'DA0029: Versión de CLR no admitida | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad41dc48303fa836e4c15f0e450b3fade60ff646
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Versión de CLR incompatible
|||  
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