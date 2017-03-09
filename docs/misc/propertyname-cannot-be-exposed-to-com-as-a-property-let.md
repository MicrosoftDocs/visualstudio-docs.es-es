---
title: "&#39;&lt;nombreDePropiedad&gt;&#39; no se puede exponer a COM como una propiedad &#39;Let&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc42102"
  - "vbc42102"
helpviewer_keywords: 
  - "BC42102"
ms.assetid: b77c5b7c-ac43-4b2d-b8bc-582e65e6f7e7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreDePropiedad&gt;&#39; no se puede exponer a COM como una propiedad &#39;Let&#39;
'\<nombreDePropiedad\>' no se puede exponer a COM como una propiedad 'Let'. No podrá asignar valores que no sean objetos \(como números o cadenas\) a esta propiedad desde Visual Basic 6.0 usando una instrucción 'Let'.  
  
 Una clase con un bloque de atributos `COMClassAttribute` declara una propiedad `Public` con el tipo de datos `Object`. Un programa de Visual Basic 6.0 puede acceder a esta propiedad como `Variant`, pero solo puede asignar una referencia de objeto con la instrucción `Set`. No puede asignar un tipo de valor con la instrucción `Let`.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42102  
  
### Para resolver esta advertencia  
  
-   Considere la posibilidad de informar a los posibles usuarios de de Visual Basic 6.0 de esta clase que no se puede usar esta propiedad con la instrucción `Let`.  
  
## Vea también  
 [Default Property Changes in Visual Basic](http://msdn.microsoft.com/es-es/9b8cfad7-40ac-4b83-affb-1ff781755a4c)   
 [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)   
 [Object \(Tipo de datos\)](/dotnet/visual-basic/language-reference/data-types/object-data-type)   
 [NO ESTÁ EN LA COMPILACIÓN: Atributos usados en Visual Basic](http://msdn.microsoft.com/es-es/22231318-8a40-49af-9245-e0aab723563b)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Clase ComClassAttribute](http://msdn.microsoft.com/es-es/5c2f0835-9210-47dc-bc59-5c1769953574)