---
title: 'DA0001: Utilizar StringBuilder para las concatenaciones | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a71a31ec3caf08dd2a6f4b4e044b929dade11f0f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855877"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001: Utilizar StringBuilder para las concatenaciones

|||  
|-|-|  
|Identificador de regla|DA0001|  
|Categoría|Uso de .NET Framework|  
|Métodos de generación de perfiles|Muestreo<br /><br /> Instrumentación|  
|Mensaje|Considere la posibilidad de utilizar StringBuilder para concatenaciones de cadena|  
|Tipo de mensaje|Advertencia|  

## <a name="cause"></a>Motivo  
 Las llamadas a System.String.Concat constituyen una proporción considerable de los datos de generación de perfiles. Considere la posibilidad de usar la clase <xref:System.Text.StringBuilder> para construir cadenas a partir de varios segmentos.  

## <a name="rule-description"></a>Descripción de la regla  
 Un objeto <xref:System.String> es inmutable. Por lo tanto, cualquier modificación en la cadena crea un nuevo objeto de cadena y la recolección de elementos no utilizados del original. Este comportamiento es el mismo si llama a String.Concat explícitamente o utiliza los operadores de concatenación de cadenas, como + o +=. El rendimiento del programa puede reducirse si se llama a estos métodos con frecuencia, como cuando se agregan caracteres a una cadena en un bucle ajustado.  

 La clase StringBuilder es un objeto mutable y, a diferencia de System.String, la mayoría de los métodos en StringBuilder que modifican una instancia de esta clase devuelven una referencia a esa misma instancia. Puede insertar caracteres o anexar texto a una instancia de StringBuilder y quitar o reemplazar caracteres en la instancia sin necesidad de asignar una nueva instancia y eliminar la instancia original.  

## <a name="how-to-investigate-a-warning"></a>Cómo investigar una advertencia  
 Haga doble clic en el mensaje en la ventana **Lista de errores** para navegar a la vista [Detalles de la función](../profiling/function-details-view.md) de los datos del perfil de muestreo. Busque las secciones del programa que utilizan la concatenación de cadenas con mayor frecuencia. Utilice la clase StringBuilder para las manipulaciones de cadenas complejas, incluidas las operaciones de concatenación de cadenas frecuentes.  

 Para obtener más información sobre cómo trabajar con cadenas, consulte la sección [Operaciones de cadenas](http://go.microsoft.com/fwlink/?LinkId=177816) de [Capítulo 5: Mejorar el rendimiento del código administrado](http://go.microsoft.com/fwlink/?LinkId=177817) en la biblioteca Patrones y prácticas de Microsoft.