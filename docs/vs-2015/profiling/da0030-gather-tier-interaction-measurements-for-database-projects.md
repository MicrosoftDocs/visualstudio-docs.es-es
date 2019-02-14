---
title: 'DA0030: Recopilar las medidas de interacción de capas para los proyectos de base de datos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a4b140c1859d3a3a17eb2f48eb02a60a3e9d50c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54801484"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: Recopilar las medidas de interacción de capas para los proyectos de base de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id. de regla | DA0030 |  
| Categoría | Uso de herramientas de generación de perfiles |  
| Método de generación de perfiles | Muestreo |  
| Mensaje | La recopilación de mediciones de interacción para aplicaciones de varios niveles tendrá ayudará a comprender los patrones de uso de la base de datos y datos clave de acceso a retrasos. Intente generar de nuevo el perfil de la aplicación con la opción de generación de perfiles de interacción de capas habilitada.  
| Tipo de regla | Información |  
  
## <a name="cause"></a>Motivo  
 Las llamadas a los métodos <xref:System.Data> constituyen una proporción considerable de los datos de generación de perfiles; además, no ha recopilado datos de interacción de capas en la generación de perfiles. Considere la opción de volver a generar los perfiles y agregar los datos de interacción de capas.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla se activa siempre que hay una actividad significativa en las funciones que residen en los espacios de nombres System.Data, incluido <xref:System.Data.Linq><xref:System.Data.Linq>.  
  
 Las aplicaciones con varias capas usan los servicios superpuestos para su presentación y niveles de datos. Normalmente, el nivel de datos es un proceso independiente que ejecuta un sistema de administración de bases de datos, como Microsoft Sql Server. El nivel de datos puede incluso ejecutarse en una máquina distinta a la del resto de la aplicación. Los perfiles de muestreo proporcionan una ligera introducción a las funciones y servicios que se ejecutan fuera de proceso o de forma remota.  
  
 Las herramientas de generación de perfiles pueden recopilar información sobre el control de tiempo de las aplicaciones de varias capas que interactúan con un nivel de datos de Microsoft Sql Server usando llamadas asincrónicas a los servicios ADO.NET. Debe habilitar explícitamente la generación de perfiles de interacción de capas. No está activada de forma predeterminada.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Esta regla solo tiene un fin informativo y es posible que no necesite acción correctiva alguna.  
  
 Para obtener información sobre cómo agregar datos de interacción de capas a los datos de generación de perfiles desde el IDE de Visual Studio, consulte [Recopilar datos de interacción de capas](../profiling/collecting-tier-interaction-data.md). Para obtener información sobre cómo agregar datos de interacción de capas desde la línea de comandos, consulte [Recopilar datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md).
