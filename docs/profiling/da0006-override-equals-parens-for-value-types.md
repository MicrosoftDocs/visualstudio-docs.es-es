---
title: "DA0006: Reemplazar Equals() para tipos de valor | Microsoft Docs"
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
  - "vs.performance.rules.DAOverrideEquals"
  - "vs.performance.6"
  - "vs.performance.DA0006"
  - "vs.performance.rules.DA0006"
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0006: Reemplazar Equals() para tipos de valor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0006|  
|Categoría|Uso de .NET Framework|  
|Métodos de generación de perfiles|Muestreo|  
|Mensaje|Invalida el método Equals y el operador de igualdad en los tipos de valor.|  
|Tipo de mensaje|Advertencia|  
  
## Motivo  
 Las llamadas al método Equals o a los operadores de igualdad de un tipo de valor público constituyen una proporción considerable de los datos de generación de perfiles.  Puede implementar un método más eficaz.  
  
## Descripción de la regla  
 En los tipos de valor, la implementación heredada de Equals usa la biblioteca <xref:System.Reflection> y compara el contenido de todos los campos en el tipo.  Mediante el cálculo, la reflexión es cara y no es necesario comparar cada campo para comprobar si hay igualdad.  Si espera que los usuarios comparen u ordenen instancias, o las usen como claves de tabla hash, el tipo de valor debe implementar Equals.  Si su lenguaje de programación admite la sobrecarga de operadores, también debería proporcionar una implementación de la igualdad y operadores de desigualdad.  
  
 Para obtener más información sobre cómo reemplazar equals y operadores de igualdad, vea [Instrucciones para implementar equals y el operador de Igualdad \(\=\=\)](http://go.microsoft.com/fwlink/?LinkId=177818).  
  
## Cómo investigar una advertencia  
 Para obtener un ejemplo sobre cómo implementar Equals y los operadores de igualdad, vea las reglas de análisis de código [CA1815: Reemplazar Equals y el operador Equals en los tipos de valor](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)