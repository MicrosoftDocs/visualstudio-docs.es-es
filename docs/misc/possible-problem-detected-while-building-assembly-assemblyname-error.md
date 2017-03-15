---
title: "Posible problema al compilar el ensamblado &#39;&lt;assemblyname&gt;&#39;: &lt;error&gt; | Microsoft Docs"
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
  - "vbc40010"
  - "bc40010"
helpviewer_keywords: 
  - "BC40010"
ms.assetid: 3a4f4a4a-a5ad-4501-bf4c-0fbf25c50734
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Posible problema al compilar el ensamblado &#39;&lt;assemblyname&gt;&#39;: &lt;error&gt;
La herramienta ALink, que ejecuta el compilador [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], notifica un error al generar el ensamblado. Las causas posibles son las siguientes:  
  
-   Un ensamblado firmado hace referencia a un ensamblado no firmado. En este caso, considere si el ensamblado al que se hace referencia cumple con los criterios de seguridad.  
  
-   Se ha creado una aplicación de 64 bits en una plataforma de 32 bits. En este caso, debe asegurarse de que las versiones de 64 bits de todos los ensamblados a los que se hace referencia están instaladas en la plataforma de destino. Para un ensamblado de Common Language Runtime \(CLR\), esto se controla automáticamente, aunque se genera este mensaje de error.  
  
 Este mensaje es una advertencia. El compilador sigue generando el ensamblado. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC40010  
  
### Para corregir este error  
  
1.  Examine el mensaje de error indicado y tome las medidas adecuadas.  
  
2.  Vuelva a compilar el programa para ver si el error se repite.  
  
3.  Si el error se repite, reinstale el compilador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
4.  Si el error persiste después de la reinstalación, reúna información sobre las circunstancias y notifíquelo a los Servicios de soporte técnico de Microsoft.  
  
## Vea también  
 [PAVEOVER Compatibilidad de productos y accesibilidad](http://msdn.microsoft.com/es-es/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)   
 [Common Language Runtime Overview](http://msdn.microsoft.com/es-es/0fd9aeae-af10-435f-86d4-e76619741e4a)