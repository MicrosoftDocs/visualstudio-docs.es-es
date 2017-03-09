---
title: "El atributo &#39;&lt;nombreDeAtributo&gt;&#39; no se puede especificar m&#225;s de una vez en este proyecto, aunque sea con id&#233;nticos valores de par&#225;metros | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc41000"
  - "vbc41000"
helpviewer_keywords: 
  - "BC41000"
ms.assetid: 7e846177-7b89-44da-8f17-cdc8606ef148
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El atributo &#39;&lt;nombreDeAtributo&gt;&#39; no se puede especificar m&#225;s de una vez en este proyecto, aunque sea con id&#233;nticos valores de par&#225;metros
Un atributo personalizado está especificado más de una vez en el mismo elemento de programación, pero se aplicó un <xref:System.AttributeUsageAttribute> al atributo personalizado y su propiedad <xref:System.AttributeUsageAttribute.AllowMultiple%2A> está establecida en `False`.<xref:System.AttributeUsageAttribute.AllowMultiple%2A> controla si el atributo es multiuso.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC41000  
  
### Para corregir este error  
  
-   Quite la especificación adicional del atributo personalizado o establezca <xref:System.AttributeUsageAttribute.AllowMultiple%2A> en `True` en el <xref:System.AttributeUsageAttribute> que se le aplicó.  
  
## Vea también  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A>   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)