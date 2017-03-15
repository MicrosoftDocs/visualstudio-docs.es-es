---
title: "CA1065: No producir excepciones en ubicaciones inesperadas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1065"
  - "DoNotRaiseExceptionsInUnexpectedLocations"
helpviewer_keywords: 
  - "DoNotRaiseExceptionsInUnexpectedLocations"
  - "CA1065"
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1065: No producir excepciones en ubicaciones inesperadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|  
|Identificador de comprobación|CA1065|  
|Categoría|Microsoft.Design|  
|Cambio problemático|No|  
  
## Motivo  
 Un método que no se espera que produzca excepciones inicia una excepción.  
  
## Descripción de la regla  
 Los métodos que no se espera que inicien excepciones se pueden clasificar como sigue:  
  
-   Métodos Get de propiedades  
  
-   Métodos de descriptor de acceso de eventos  
  
-   Métodos Equals  
  
-   Métodos GetHashCode  
  
-   Métodos ToString  
  
-   Constructores estáticos  
  
-   Finalizadores  
  
-   Métodos Dispose  
  
-   Operadores de igualdad  
  
-   Operadores de conversión implícitos  
  
 En las secciones siguientes se describe estos tipos de métodos.  
  
### Métodos Get de propiedades  
 En esencia, las propiedades son campos inteligentes.  Por consiguiente, deberían comportarse de la forma más parecida a un campo.  Los campos no inician excepciones y las propiedades tampoco deberían iniciarlas.  Si usa una propiedad que inicia una excepción, considere convertirla en un método.  
  
 Las excepciones siguientes se pueden iniciar desde un método Get de propiedad:  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName> y todos los derivados \(incluido <xref:System.ObjectDisposedException?displayProperty=fullName>\)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName> y todos los derivados  
  
-   <xref:System.ArgumentException?displayProperty=fullName> \(sólo de Get indizado\)  
  
-   <xref:System.Collections.Generic.KeyNotFoundException> \(sólo de Get indizado\)  
  
### Métodos de descriptor de acceso de eventos  
 Los descriptores de acceso de eventos deberían ser operaciones simples que no inicien excepciones.  Un evento no debería iniciar una excepción al intentar agregar o quitar un controlador de eventos.  
  
 Las excepciones siguientes pueden iniciarse desde un descriptor de acceso de eventos:  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName> y todos los derivados \(incluido <xref:System.ObjectDisposedException?displayProperty=fullName>\)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName> y todos los derivados  
  
-   <xref:System.ArgumentException> y derivados  
  
### Métodos Equals  
 Los métodos **Equals** siguientes no deberían iniciar excepciones:  
  
-   <xref:System.Object.Equals%2A?displayProperty=fullName>  
  
-   [M:IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)  
  
 Un método **Equals** debe devolver `true` o `false` en lugar de iniciar una excepción.  Por ejemplo, si Equals pasa dos tipos que no coinciden, simplemente debe devolver `false` en lugar de iniciar la excepción <xref:System.ArgumentException>.  
  
### Métodos GetHashCode  
 Los métodos **GetHashCode** siguientes normalmente no deberían iniciar excepciones:  
  
-   <xref:System.Object.GetHashCode%2A>  
  
-   [M:IEqualityComparer.GetHashCode\(t\)](http://go.microsoft.com/fwlink/?LinkId=113477)  
  
 **GetHashCode** siempre debe devolver un valor.  De lo contrario, pueden perderse elementos de la tabla hash.  
  
 Las versiones de **GetHashCode** que toman un argumento pueden iniciar <xref:System.ArgumentException>.  Sin embargo, **Object.GetHashCode** nunca debería iniciar una excepción.  
  
### Métodos ToString  
 El depurador utiliza <xref:System.Object.ToString%2A?displayProperty=fullName> para ayudar a mostrar información sobre los objetos en formato de cadena.  Por consiguiente, **ToString** no debería cambiar el estado de un objeto y no debería iniciar excepciones.  
  
### Constructores estáticos  
 Iniciar excepciones desde un constructor estático hace que el tipo sea inutilizable en el dominio de la aplicación actual.  Debe haber una muy buena razón \(como un problema de seguridad\) para iniciar una excepción desde un constructor estático.  
  
### Finalizadores  
 Iniciar una excepción desde un finalizador hace que CLR produzca errores rápidamente y que se destruya el proceso.  Por ello, siempre se debe evitar iniciar excepciones en un finalizador.  
  
### Métodos Dispose  
 Un método <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> no debería iniciar una excepción.  Dispose se llama a menudo como parte de la lógica de limpieza en una cláusula `finally`.  Por consiguiente, iniciar explícitamente una excepción desde Dispone obliga al usuario a agregar el control de excepciones dentro de la cláusula `finally`.  
  
 La ruta de acceso del código de **Dispose\(false\)** nunca debería iniciar excepciones, porque casi siempre se le llama desde un finalizador.  
  
### Operadores de igualdad \(\=\=, \!\=\)  
 Como los métodos Equals, los operadores de igualdad deberían devolver `true` o `false` y no iniciar excepciones.  
  
### Operadores de conversión implícitos  
 Dado que el usuario a menudo no advierte que se ha llamado a un operador de conversión implícito, una excepción iniciada por el operador de conversión implícito es completamente inesperada.  Por consiguiente, no se debería iniciar ninguna excepción desde los operadores de conversión implícitos.  
  
## Cómo corregir infracciones  
 En los métodos Get de propiedades, cambie la lógica para que no necesite iniciar una excepción o sustituya la propiedad por un método.  
  
 En todos los demás tipos de métodos mostrados anteriormente, cambie la lógica de manera que no sea necesario iniciar una excepción.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si la infracción la produjo una declaración de excepción en lugar de una excepción producida.  
  
## Reglas relacionadas  
 [CA2219: No producir excepciones en cláusulas de excepción](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)  
  
## Vea también  
 [Diseñar advertencias](../code-quality/design-warnings.md)