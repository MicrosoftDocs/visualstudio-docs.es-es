---
title: "Ya no se admite el evento &#39;Class_Initialize&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42001"
  - "bc42001"
helpviewer_keywords: 
  - "BC42001"
ms.assetid: 31e7c383-894e-416c-b834-3688cc340ccf
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ya no se admite el evento &#39;Class_Initialize&#39;
Ya no se admite el evento 'Class\_Initialize'. Use 'Sub New' para inicializar una clase.  
  
 El evento `Class_Initialize` de versiones anteriores de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] se sustituyó por constructores de clase.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42001  
  
### Para corregir este error  
  
-   Declare uno o varios procedimientos `Sub` denominados `New` para inicializar una clase. Se llama a `Sub New` cuando se crea una instancia de clase nueva.  
  
## Vea también  
 [Class\_Initialize Changes in Visual Basic](http://msdn.microsoft.com/es-es/2cd023cf-2869-4836-b08d-43822294beeb)   
 [Classes for Visual Basic 6.0 Users](http://msdn.microsoft.com/es-es/d625222c-cd32-4c8d-b25c-ea71729b88b7)   
 [NO ESTÁ EN LA COMPILACIÓN: Usar constructores y destructores](http://msdn.microsoft.com/es-es/548eebe1-86c4-4377-b2f5-447cb8be3d90)