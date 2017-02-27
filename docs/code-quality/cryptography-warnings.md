---
title: "Advertencias de criptograf&#237;a | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 7
---
# Advertencias de criptograf&#237;a
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las advertencias de criptografía admiten bibliotecas y aplicaciones más seguras gracias al uso correcto de criptografía. Estas advertencias ayudan a evitar los errores de seguridad en su programa. Si deshabilita cualquier advertencia de este tipo, se debe indicar el motivo claramente en el código además de informar al responsable de seguridad designado a ese proyecto de desarrollo.  
  
|Regla|Descripción|  
|-----------|-----------------|  
|[CA5350: No use algoritmos criptográficos no seguros](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Las funciones hash y los algoritmos de cifrado débiles se usan hoy en día para numerosos propósitos, pero no se recomiendan para garantizar la confidencialidad o la integridad de los datos que se protegen. Esta regla se desencadena cuando se encuentran los algoritmos TripleDES, SHA1 o RIPEMD160 en el código.|  
|[CA5351 No use algoritmos criptográficos rotos](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Los algoritmos criptográficos rotos no se consideran seguros y debe desalentarse su uso. Esta regla se desencadena cuando encuentra el algoritmo hash MD5 o los algoritmos de cifrado DES o RC2 en el código.|