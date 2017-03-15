---
title: "CA1308: Normalizar las cadenas en may&#250;sculas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1308"
  - "NormalizeStringsToUppercase"
helpviewer_keywords: 
  - "NormalizeStringsToUppercase"
  - "CA1308"
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1308: Normalizar las cadenas en may&#250;sculas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NormalizeStringsToUppercase|  
|Identificador de comprobación|CA1308|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Una operación normaliza una cadena para se escriba en letras minúsculas.  
  
## Descripción de la regla  
 Las cadenas se deberían normalizar para que se escriban en letras mayúsculas.  Hay un grupo reducido de caracteres que no pueden realizar un viaje de ida y vuelta cuando se convierten a minúsculas.  Realizar un viaje de ida y vuelta \(round trip\) significa convertir los caracteres de una configuración regional a otra configuración regional que representa los datos de caracteres de manera diferente y, a continuación, recuperar con precisión los caracteres originales de los caracteres convertidos.  
  
## Cómo corregir infracciones  
 Cambie las operaciones que convierten cadenas para que se escriban en letras minúsculas de forma que las cadenas se conviertan para que se escriban en su lugar en letras mayúsculas.  Por ejemplo, cambie `String.ToLower(CultureInfo.InvariantCulture)` a `String.ToUpper(CultureInfo.InvariantCulture)`.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir un mensaje de advertencia cuando no esté tomando una decisión relativa a la seguridad basada en el resultado \(por ejemplo, cuando la está mostrando en la interfaz de usuario\).  
  
## Vea también  
 [Advertencias de globalización](../code-quality/globalization-warnings.md)