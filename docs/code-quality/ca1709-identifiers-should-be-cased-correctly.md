---
title: "CA1709: Los identificadores deber&#237;an utilizar las may&#250;sculas y min&#250;sculas correctamente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldBeCasedCorrectly"
  - "CA1709"
helpviewer_keywords: 
  - "CA1709"
  - "IdentifiersShouldBeCasedCorrectly"
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 29
---
# CA1709: Los identificadores deber&#237;an utilizar las may&#250;sculas y min&#250;sculas correctamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|Identificador de comprobación|CA1709|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático: cuando se produce en los ensamblados, espacios de nombres, tipos, miembros y parámetros.<br /><br /> No problemático: cuando se produce en parámetros de tipo genérico.|  
  
## Motivo  
 No se han utilizado correctamente las mayúsculas y minúsculas para escribir el nombre.  
  
 – O bien –  
  
 El nombre de un identificador contiene un acrónimo de dos letras y la segunda letra es minúscula.  
  
 – O bien –  
  
 El nombre de un identificador contiene un acrónimo de tres o más letras mayúsculas.  
  
## Descripción de la regla  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime.  Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
 Por convención, los nombres de parámetro utilizan la convención Camel de uso de mayúsculas; el espacio de nombres, el tipo y los nombres de miembro utilizan la convención Pascal.  En un nombre basado en la convención Camel, la primera letra es minúscula y la primera letra de las demás palabras del nombre es mayúscula.  Los ejemplos de nombres escritos según la convención Camel son "packetSniffer", "ioFile" y "fatalErrorCode".  En un nombre escrito según la convención Pascal, la primera letra es mayúscula y la primera letra de las demás palabras del nombre es mayúscula.  Los ejemplos de nombres basados en la convención Pascal son "PacketSniffer", "IOFile" y "FatalErrorCode".  
  
 La regla divide el nombre en palabras según las mayúsculas o minúsculas y compara las palabras de dos letras, como "In" o "My", con la lista de palabras comunes de dos letras.  Si no se encuentra una coincidencia, se supone que la palabra es un acrónimo.  Asimismo, esta regla supone que ha encontrado un acrónimo cuando el nombre contiene cuatro letras mayúsculas seguidas o tres letras mayúsculas seguidas al final del nombre.  
  
 Por convención, los acrónimos de dos letras utilizan todas las letras mayúsculas y los acrónimos de tres o más caracteres utilizan la convención Pascal de mayúsculas.  Los ejemplos siguientes usan esta convención de nomenclatura: 'DB', 'CR', 'Cpa' y 'Ecma'.  Los ejemplos siguientes infringen la convención: 'Io', 'XML' y 'DoD' y para los nombres que no sean de parámetros, 'xp' y 'cpl'.  
  
 'ID' es un caso de uso de mayúsculas especial que provoca una infracción de esta regla. El “id.” no es un acrónimo sino una abreviatura para “identificador”.  
  
## Cómo corregir infracciones  
 Cambie el nombre utilizando las mayúsculas correctamente.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir esta advertencia si dispone de sus propias convenciones de nomenclatura o si el identificador representa un nombre correcto, por ejemplo, el nombre de una compañía o una tecnología.  
  
 También puede agregar términos específicos, abreviaturas y acrónimos a un diccionario personalizado de análisis de código.  Los términos especificados en el diccionario personalizado no producirán infracciones de esta regla.  Para obtener más información, vea [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
## Reglas relacionadas  
 [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)