---
title: 'DA0012: Cantidad significativa de reflexión | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: deb6d8f759080caf1933c75f1f3f05428d3cff9d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300306"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Cantidad significativa de reflexión
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rule Id|DA0012|  
|Category|.NET Framework Usage|  
|Profiling methods|Sampling|  
|Message|You may be using Reflection excessively. Es una operación que consume muchos recursos.|  
|Rule type|Warning|  
  
## <a name="cause"></a>Motivo  
 Las llamadas a métodos System.Reflection, como InvokeMember y GetMember, o a métodos Type, como MemberInvoke, constituyen una proporción considerable de los datos de generación de perfiles. Cuando sea posible, considere la posibilidad de reemplazar estos métodos con enlace anticipado a los métodos de ensamblados dependientes.  
  
## <a name="rule-description"></a>Descripción de la regla  
 La reflexión es una herramienta flexible de .NET Framework que puede utilizar para realizar el enlace tardío de la aplicación a un ensamblado de run-time dependiente o para crear y ejecutar dinámicamente nuevos tipos durante el run-time. Sin embargo, estas técnicas pueden disminuir el rendimiento si se utilizan con frecuencia o se llaman en bucles de pequeñas dimensiones.  
  
 Para obtener más información, consulte la sección [Reflexión y enlace tardío](https://go.microsoft.com/fwlink/?LinkId=177826) de Capítulo 5: Mejorar el rendimiento de código administrado en el volumen Mejorar el rendimiento y la escalabilidad de las aplicaciones .NET de la biblioteca Patrones y prácticas de Microsoft de MSDN.  
  
## <a name="how-to-investigate-a-warning"></a>Cómo investigar una advertencia  
 Haga doble clic en el mensaje en la ventana Lista de errores para navegar a la [vista Detalles de la función](../profiling/function-details-view.md) de los datos de generación de perfiles. Examine las funciones de llamada del método System.Type o System.Reflection para encontrar las secciones del programa que hacen un uso más frecuente de las API de reflexión de .NET. Evite usar métodos que devuelvan metadatos. Cuando el rendimiento de su aplicación es crítico, debe evitar el uso de enlace tardío y la creación dinámica de tipos en run-time.
