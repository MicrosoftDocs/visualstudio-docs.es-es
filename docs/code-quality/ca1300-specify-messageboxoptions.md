---
title: "CA1300: Especifique MessageBoxOptions | Microsoft Docs"
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
  - "SpecifyMessageBoxOptions"
  - "CA1300"
helpviewer_keywords: 
  - "SpecifyMessageBoxOptions"
  - "CA1300"
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1300: Especifique MessageBoxOptions
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyMessageBoxOptions|  
|Identificador de comprobación|CA1300|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un método llama a una sobrecarga del método <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> que no toma un argumento <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName>.  
  
## Descripción de la regla  
 Para mostrar correctamente un cuadro de texto para las referencias culturales con escritura de derecha a izquierda, los miembros <xref:System.Windows.Forms.MessageBoxOptions> y <xref:System.Windows.Forms.MessageBoxOptions> de la enumeración <xref:System.Windows.Forms.MessageBoxOptions> se deben pasar al método <xref:System.Windows.Forms.MessageBox.Show%2A>.  Examine la propiedad <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> del control que contiene para determinar si debe utilizar el orden de lectura de derecha a izquierda.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, llame a una sobrecarga del método <xref:System.Windows.Forms.MessageBox.Show%2A> que toma un argumento <xref:System.Windows.Forms.MessageBoxOptions>.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si la biblioteca de códigos no se puede adaptar para una referencia cultural con orden de lectura de derecha a izquierda.  
  
## Ejemplo  
 El ejemplo siguiente muestra un método que muestra un cuadro de mensaje con opciones adecuadas para el orden de lectura de la referencia cultural.  Es necesario un archivo de recursos, que no se muestra, para compilar el ejemplo.  Siga los comentarios del ejemplo para compilarlo sin un archivo de recursos y probar la característica de lectura de derecha a izquierda.  
  
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-cs[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]  
  
## Vea también  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Recursos de aplicaciones de escritorio](../Topic/Resources%20in%20Desktop%20Apps.md)