---
title: "CA1500: Los nombres de las variables no deben coincidir con los nombres de los campos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VariableNamesShouldNotMatchFieldNames"
  - "CA1500"
helpviewer_keywords: 
  - "VariableNamesShouldNotMatchFieldNames"
  - "CA1500"
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1500: Los nombres de las variables no deben coincidir con los nombres de los campos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|VariableNamesShouldNotMatchFieldNames|  
|Identificador de comprobación|CA1500|  
|Categoría|Microsoft.Maintainability|  
|Cambio problemático|Cuando se desencadena en un parámetro que tiene el mismo nombre que un campo:<br /><br /> -   No problemático: si tanto el campo como el método que declara al parámetro no se pueden ver fuera del ensamblado, independientemente del cambio que realice.<br />-   Problemático: si cambia el nombre del campo y se puede ver fuera del ensamblado.<br />-   Problemático: si cambia el nombre del parámetro y el método que lo declara se puede ver fuera del ensamblado.<br /><br /> Cuando se desencadena en una variable local que tiene el mismo nombre que un campo:<br /><br /> -   No problemático: si el campo no se puede ver fuera del ensamblado, independientemente del cambio realizado.<br />-   No problemático: si cambia el nombre de la variable local y no cambia el nombre del campo.<br />-   Problemático: si cambia el nombre del campo y se puede ver fuera del ensamblado.|  
  
## Motivo  
 Un método de instancia declara un parámetro o una variable local cuyo nombre coincide con un campo de instancia del tipo declarativo.  Para detectar las variables locales que infringen esta regla, el ensamblado probado se debe compilar  a partir de la información de depuración, y el archivo de base de datos de programa asociado \(.pdb\) debe estar disponible.  
  
## Descripción de la regla  
 Cuando el nombre de un campo de instancia coincide con el de un parámetro o el de una variable local, se tiene acceso al campo de instancia utilizando la palabra `this` \(`Me` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) desde el interior del cuerpo del método.  Al mantener el código, resulta fácil olvidarse de esta diferencia y suponer que el parámetro o la variable local hace referencia al campo de instancia, lo que puede provocar errores.  Esto sucede especialmente con cuerpos de método largos.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el nombre del parámetro o la variable, o el del campo.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra dos infracciones de esta regla.  
  
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
 [!code-cs[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]