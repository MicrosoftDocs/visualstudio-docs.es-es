---
title: 'DA0029: Versión de CLR no admitida | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 532427618f476e1e187d8a1c88749810f9d157c9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803545"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Versión de CLR incompatible
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id. de regla | DA0029 |  
| Categoría | Uso de herramientas de generación de perfiles |  
| Método de generación de perfiles | Generación de perfiles desde la línea de comandos |  
| Mensaje | Se detectó una versión CLR no admitida durante la recolección. Puede que los símbolos administrados no se resuelvan correctamente.  
| Tipo de regla | Información. |  
  
## <a name="cause"></a>Motivo  
 Está intentando generar perfiles de una aplicación que usa [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)], que no es compatible con las herramientas de generación de perfiles.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta advertencia se produce porque las herramientas de generación de perfiles no podrán resolver símbolos del código administrado que se ejecuta en la aplicación. Las herramientas de generación de perfiles no pueden resolver símbolos de código administrado para aplicaciones que ejecutan [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)].  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Ninguno.
