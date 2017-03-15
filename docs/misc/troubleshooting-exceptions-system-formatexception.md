---
title: "Soluci&#243;n de problemas de excepciones: System.FormatException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "FormatException (clase)"
ms.assetid: b2a4f55e-da87-4915-a053-59eb1595993d
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.FormatException
Un método lanza una excepción <xref:System.FormatException> que analiza un tipo o le da formato cuando el formato de un argumento no cumple las especificaciones de los parámetros del método.  
  
## En este artículo  
  
## Provocación de excepciones de formato  
  
### Aplicación de formato  
 *Aplicar formato* es el proceso de convertir una instancia de una clase, una estructura o un valor de enumeración en su representación de cadena, a menudo para que la cadena resultante se pueda mostrar a los usuarios o se pueda usar para guardar el estado del objeto.  
  
 Por ejemplo, <xref:System.Int32.ToString%28System.String%29?displayProperty=fullName> toma un parámetro de cadena que identifica una *cadena de formato* estándar o personalizada y devuelve la representación de cadena del número. El método lanza una <xref:System.FormatException>. Si la cadena de formato no es válida o no se admite, se lanza una.  
  
### Formatos compuestos  
 El *formato compuesto* toma una lista de objetos y una cadena de formato compuesto como entrada. Una cadena de formato compuesto está formada por texto fijo combinado con marcadores de posición indizados, que reciben el nombre de elementos de formato, y que se corresponden con los objetos de la lista. La operación de formato genera una cadena de resultado compuesta por el texto fijo original combinado con la representación de cadena de los objetos de la lista.  
  
 <xref:System.String.Format%2A?displayProperty=fullName> y <xref:System.Console.WriteLine%2A?displayProperty=fullName> son ejemplos de métodos que realizan el formato compuesto. Los métodos que utilizan el formato compuesto lanzan una <xref:System.FormatException> si la cadena de formato no es válida o el índice de un elemento de formato es menor que cero o mayor o igual que el número de argumentos.  
  
### Análisis  
 El *análisis* es el proceso de convertir una cadena que representa un tipo base de.NET Framework en ese tipo base. Por ejemplo, se usa una operación de análisis para convertir una cadena en un número de punto flotante o un valor de fecha y hora.  
  
 Por ejemplo, <xref:System.Int32.Parse%28System.String%29?displayProperty=fullName> <xref:System.DateTime.Parse%2A> convierte la representación de cadena de una fecha y hora en su equivalente de <xref:System.DateTime> con la información de formato específica de la referencia cultural especificada en el parámetro <xref:System.IformatProvider>. Si la cadena no está en el formato correcto, se lanza <xref:System.FormatException>.  
  
## Evitar FormatExceptions  
 El artículo de referencia de clase <xref:System.FormatException> incluye las causas y soluciones comunes de los errores <xref:System.FormatException>.  
  
 Las secciones de MSDN Library [Aplicar formato a tipos](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md) y [Analizar cadenas](../Topic/Parsing%20Strings%20in%20the%20.NET%20Framework.md) contienen información sobre cómo aplicar formato a los tipos y analizarlos correctamente.  
  
 **Formatos compuestos**  
  
 [Formatos compuestos](../Topic/Composite%20Formatting.md)  
  
 **Tipos numéricos**  
  
|||  
|-|-|  
|[Cadenas con formato numérico estándar](../Topic/Standard%20Numeric%20Format%20Strings.md)|[Cadenas con formato numérico personalizado](../Topic/Custom%20Numeric%20Format%20Strings.md)|  
|[Analizar cadenas numéricas](../Topic/Parsing%20Numeric%20Strings%20in%20the%20.NET%20Framework.md)||  
  
 **Tipos de fecha y hora y Timespan**  
  
|||  
|-|-|  
|[Cadenas con formato de fecha y hora estándar](../Topic/Standard%20Date%20and%20Time%20Format%20Strings.md)|[Cadenas con formato de fecha y hora personalizado](../Topic/Custom%20Date%20and%20Time%20Format%20Strings.md)|  
|[Cadenas de formato TimeSpan estándar](../Topic/Standard%20TimeSpan%20Format%20Strings.md)|[Cadenas de formato TimeSpan personalizado](../Topic/Custom%20TimeSpan%20Format%20Strings.md)|  
|[Analizar cadenas de fecha y hora](../Topic/Parsing%20Date%20and%20Time%20Strings%20in%20the%20.NET%20Framework.md)||  
  
 **Otros tipos**  
  
|||  
|-|-|  
|[Cadenas de formato de enumeración](../Topic/Enumeration%20Format%20Strings.md)|[Analizar otras cadenas](../Topic/Parsing%20Other%20Strings%20in%20the%20.NET%20Framework.md)|