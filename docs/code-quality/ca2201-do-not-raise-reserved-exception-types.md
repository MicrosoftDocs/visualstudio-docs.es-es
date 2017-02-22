---
title: "CA2201: No provocar tipos de excepci&#243;n reservados | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotRaiseReservedExceptionTypes"
  - "CA2201"
helpviewer_keywords: 
  - "CA2201"
  - "DoNotRaiseReservedExceptionTypes"
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2201: No provocar tipos de excepci&#243;n reservados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotRaiseReservedExceptionTypes|  
|Identificador de comprobación|CA2201|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método provoca un tipo de excepción que es demasiado general o que se reserva por el motor en tiempo de ejecución.  
  
## Descripción de la regla  
 Los tipos de excepción siguientes son demasiado generales para proporcionar la información suficiente al usuario:  
  
-   <xref:System.Exception?displayProperty=fullName>  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.SystemException?displayProperty=fullName>  
  
 Se reservan los tipos de excepción siguientes y sólo deberían ser producidos por Common Language Runtime:  
  
-   <xref:System.ExecutionEngineException?displayProperty=fullName>  
  
-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>  
  
-   <xref:System.NullReferenceException?displayProperty=fullName>  
  
-   <xref:System.OutOfMemoryException?displayProperty=fullName>  
  
 **No producir excepciones generales**  
  
 Si produce un tipo de excepción general, como <xref:System.Exception> o <xref:System.SystemException> en una biblioteca o marco, obliga a los consumidores a detectar todas las excepciones, incluso las excepciones desconocidas que no saben tratar.  
  
 En su lugar, produzca un tipo más derivado que ya exista en el marco o cree su propio tipo que se derive de <xref:System.Exception>.  
  
 **Producir las excepciones específicas**  
  
 La tabla siguiente muestra parámetros y las excepciones a producir al validar el parámetro, donde se incluye el parámetro de valor en el descriptor de acceso set de una propiedad:  
  
|Descripción del parámetro|Excepción|  
|-------------------------------|---------------|  
|Referencia `null`.|<xref:System.ArgumentNullException?displayProperty=fullName>|  
|Fuera del intervalo de valores permitido \(como un índice para una colección o lista\)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|  
|Valor no válido `enum`|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|  
|Contiene un formato que no cumple las especificaciones de parámetro de un método \(como la cadena del formato para `ToString(String)`\)|<xref:System.FormatException?displayProperty=fullName>|  
|De lo contrario no válido|<xref:System.ArgumentException?displayProperty=fullName>|  
  
 Cuando una operación no es válida para el estado actual de un objeto, produzca <xref:System.InvalidOperationException?displayProperty=fullName>  
  
 Cuando una operación se realiza en un objeto que se ha eliminado, produzca <xref:System.ObjectDisposedException?displayProperty=fullName>  
  
 Cuando una operación no se admite \(como en un **Stream.Write** invalidado en una Secuencia que se ha abierto para lectura\), produzca <xref:System.NotSupportedException?displayProperty=fullName>  
  
 Cuando una conversión provocaría un desbordamiento \(como en una sobrecarga del operador de conversión explícita\), produzca <xref:System.OverflowException?displayProperty=fullName>  
  
 Para el resto de situaciones, considere crear su propio tipo que se derive de <xref:System.Exception> y produzca eso.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el tipo de la excepción producida para un tipo específico que no es uno de los reservados.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Reglas relacionadas  
 [CA1031: No capturar los tipos de excepción general](../code-quality/ca1031-do-not-catch-general-exception-types.md)