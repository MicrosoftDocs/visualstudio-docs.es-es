---
title: 'CA2201: No provocar tipos de excepción reservados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 696eed674dd2b85ec048290ba88084751230635d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924042"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: No provocar tipos de excepción reservados
|||
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|Identificador de comprobación|CA2201|
|Categoría|Microsoft.Usage|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método genera un tipo de excepción que es demasiado general o que está reservado por el tiempo de ejecución.

## <a name="rule-description"></a>Descripción de la regla
 Los siguientes tipos de excepción son demasiado generales para proporcionar información suficiente para el usuario:

-   <xref:System.Exception?displayProperty=fullName>

-   <xref:System.ApplicationException?displayProperty=fullName>

-   <xref:System.SystemException?displayProperty=fullName>

 Los tipos de excepción siguientes están reservados y deben producir solo por common language runtime:

-   <xref:System.ExecutionEngineException?displayProperty=fullName>

-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>

-   <xref:System.NullReferenceException?displayProperty=fullName>

-   <xref:System.OutOfMemoryException?displayProperty=fullName>

 **No genere excepciones generales**

 Si se produce un tipo de excepción general, como <xref:System.Exception> o <xref:System.SystemException> en una biblioteca o el marco de trabajo, obliga a los consumidores puedan todas las detectar excepciones, incluidas las excepciones desconocidas que no saben cómo controlar.

 En su lugar, se produce un tipo más derivado que ya existe en el marco de trabajo, o se crea su propio tipo que deriva de <xref:System.Exception>.

 **Producir excepciones específicas**

 La siguiente tabla muestra los parámetros y las excepciones que se producirá cuando se valida el parámetro, incluido el valor del parámetro en el descriptor de acceso set de una propiedad:

|Descripción del parámetro|Excepción|
|---------------------------|---------------|
|`null` Referencia|<xref:System.ArgumentNullException?displayProperty=fullName>|
|Fuera del intervalo permitido de valores (por ejemplo, un índice para una colección o lista)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|No válido `enum` valor|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|Contiene un formato que no cumple las especificaciones de parámetros de un método (por ejemplo, la cadena de formato `ToString(String)`)|<xref:System.FormatException?displayProperty=fullName>|
|No es válida|<xref:System.ArgumentException?displayProperty=fullName>|

 Cuando una operación no es válida para el estado actual de un objeto throw <xref:System.InvalidOperationException?displayProperty=fullName>

 Cuando se realiza una operación en un objeto que se ha eliminado throw <xref:System.ObjectDisposedException?displayProperty=fullName>

 Cuando una operación no se admite (como en un invalidado **Stream.Write** en una secuencia de abrir para lectura) throw <xref:System.NotSupportedException?displayProperty=fullName>

 Cuando una conversión daría como resultado un desbordamiento (como en una sobrecarga de operador de conversión explícita) throw <xref:System.OverflowException?displayProperty=fullName>

 Para el resto de situaciones, considere la posibilidad de crear su propio tipo que deriva de <xref:System.Exception> y que producen.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el tipo de la excepción a un tipo específico que no es uno de los tipos reservados.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1031: No capturar los tipos de excepción general](../code-quality/ca1031-do-not-catch-general-exception-types.md)