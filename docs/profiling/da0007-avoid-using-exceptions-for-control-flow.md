---
title: 'DA0007: Evite utilizar excepciones para el flujo de control | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 26819be7cd001e87a6f94ac97d29c8a5e67f3932
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777704"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: Evite utilizar excepciones para el flujo de control

|||
|-|-|
|Identificador de regla|DA0007|
|Categoría|Uso de .NET Framework|
|Métodos de generación de perfiles|Todas|
|Mensaje|Constantemente se está produciendo un gran número de excepciones. Considere la posibilidad de reducir el uso de excepciones en la lógica del programa.|
|Tipo de mensaje|Advertencia|

 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 25 ejemplos para activar esta regla.

## <a name="cause"></a>Motivo
 Se produjo una alta tasa de controladores de excepciones de .NET Framework en los datos de generación de perfiles. Puede utilizar otra lógica de flujo de control para reducir el número de excepciones que se producen.

## <a name="rule-description"></a>Descripción de la regla
 Aunque el uso de controladores de excepciones para detectar errores y otros eventos que interrumpen la ejecución del programa es una buena práctica, el uso del controlador de excepciones como parte de la lógica de ejecución de programa normal puede ser costoso y debe evitarse. En la mayoría de los casos, las excepciones se deben usar solo en circunstancias que se producen con poca frecuencia y no se esperan. Las excepciones no deben utilizarse para devolver valores como parte del flujo del programa normal. En muchos casos, puede evitar generar excepciones si valida los valores y utiliza la lógica condicional para detener la ejecución de las instrucciones que provocan el problema.

 Para obtener más información, vea la sección [Administración de excepciones](/previous-versions/msp-n-p/ff647790(v=pandp.10)#exception-management) de **Capítulo 5: Mejorar el rendimiento de código administrado** en el volumen **Mejorar el rendimiento y la escalabilidad de las aplicaciones .NET** de la biblioteca **Patrones y prácticas de Microsoft** de MSDN.

## <a name="how-to-investigate-a-warning"></a>Cómo investigar una advertencia
 Haga doble clic en el mensaje de la ventana Lista de errores para navegar a la vista Marcas. Busque la columna que contiene las medidas **Excepciones de .NET CLR(@ProcessInstance)\\Número de excepciones producidas por segundo**. Determine si hay fases concretas de ejecución del programa en que el control de excepciones sea más frecuente que en otras. Mediante un perfil de muestreo, intente identificar las instrucciones Throw y los bloques Try/Catch que generan excepciones frecuentes. Si es necesario, agregue lógica a los bloques Catch para entender mejor qué excepciones se controlan con más frecuencia. Siempre que sea posible, reemplace las instrucciones Throw o los bloques Catch que se ejecutan con frecuencia con lógica de control de flujo simple o código de validación.

 Por ejemplo, si descubre que la aplicación controlaba excepciones DivideByZeroException frecuentes, agregar lógica al programa para comprobar los denominadores con valores cero mejorará el rendimiento de la aplicación.
