---
title: "DA0007: Evite utilizar excepciones para el flujo de control | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAExceptionsThrown"
  - "vs.performance.7"
  - "vs.performance.rules.DA0007"
  - "vs.performance.DA0007"
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0007: Evite utilizar excepciones para el flujo de control
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0007|  
|Categoría|Uso de .NET Framework|  
|Métodos de generación de perfiles|Todos|  
|Mensaje|Se está generando un alto número de excepciones de forma constante.  Considere reducir el uso de excepciones en la lógica del programa.|  
|Tipo de mensaje|Advertencia|  
  
 Cuando genere perfiles usando métodos de muestreo, memoria de .NET o contención de recursos, debe recopilar al menos 25 muestras para desencadenar esta regla.  
  
## Motivo  
 Se llamó a una alta tasa de controladores de excepciones de .NET Framework en los datos de generación de perfiles.  Puede utilizar otra lógica de flujo de control para reducir el número de excepciones que se producen.  
  
## Descripción de la regla  
 Aunque es aconsejable el uso de controladores de excepciones para detectar errores y otros eventos que interrumpen la ejecución de programas, el uso del controlador de excepciones como parte de la lógica de ejecución de programas normal puede ser costoso y se debe evitar.  En la mayoría de los casos, las excepciones se deben usar solo en circunstancias que se dan con poca frecuencia y que no se esperan.  Las excepciones no se deben utilizar para devolver valores como parte del flujo típico de un programa.  En muchos casos, puede evitar que se produzcan excepciones validando los valores y usando la lógica condicional para detener la ejecución de las instrucciones que producen el problema.  
  
 Para obtener más información vea [Administración de excepciones](http://go.microsoft.com/fwlink/?LinkID=177825) la sección de **Chapter 5 — Improving Managed Code Performance** en el volumen de **Improving .NET Application Performance and Scalability** de la biblioteca de **Microsoft Patterns and Practices** en MSDN.  
  
## Cómo investigar una advertencia  
 Haga doble clic en el mensaje en la ventana Lista de errores para navegar a la vista Marcas.  Encuentre la columna que contiene las medidas de **Excepciones\(@ProcessInstance\) de .NET CLR\\Número de excepciones producidas por segundo**.  Determine si hay fases concretas de la ejecución del programa en las que el control de excepciones es más frecuente que en otras.  Con un perfil del muestreo, intente identificar las instrucciones throw y los bloques Try\-Catch que generan excepciones frecuentes.  Si es necesario, agregue lógica para detectar bloques que sirvan de ayuda para entender qué excepciones se tratan con más frecuencia.  Siempre que sea posible, reemplace instrucciones throw o bloques catch ejecutados con frecuencia con lógica de control de flujo simple o código de validación.  
  
 Por ejemplo, si encontrara que su aplicación estaba administrando las excepciones DivideByZeroException frecuentes, al agregar la lógica a su programa para comprobar los denominadores con valores cero mejorará el rendimiento de la aplicación.