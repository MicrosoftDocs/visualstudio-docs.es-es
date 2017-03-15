---
title: "Conjunto de reglas Reglas m&#237;nimas administradas para c&#243;digo administrado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 2
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 2
---
# Conjunto de reglas Reglas m&#237;nimas administradas para c&#243;digo administrado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las reglas se centran en los problemas más graves del código, incluidas posibles vulnerabilidades de seguridad, bloqueos de la aplicación y otros errores importantes de diseño y lógica.  Debe incluir este conjunto de reglas en todos los conjuntos de reglas personalizados que cree para sus proyectos.  
  
|Regla|Descripción|  
|-----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Los tipos que poseen campos descartables deben ser descartables|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Quitar los finalizadores vacíos|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Los campos desechables se deben desechar|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Sobrecargar el operador de igualdad al remplazar el tipo de valor de igualdad|