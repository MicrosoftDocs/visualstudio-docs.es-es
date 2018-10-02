---
title: Configuración de reglas reglas mínimas administradas para código administrado | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cca9670f65ef517a4697fc0752c65cbafbaa3b16
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574833"
---
# <a name="managed-minimun-rules-rule-set-for-managed-code"></a>Conjunto de reglas Reglas mínimas administradas para código administrado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [de conjunto de reglas de reglas de mínimas administradas para código administrado](https://docs.microsoft.com/visualstudio/code-quality/managed-minimun-rules-rule-set-for-managed-code).  
  
Las reglas mínimas administradas se centran en los problemas más graves del código, incluidas posibles vulnerabilidades de seguridad, bloqueos de la aplicación y otros errores de diseño y lógica importantes. Debe incluir este conjunto de reglas en todos los conjuntos de reglas personalizados que cree para sus proyectos.  
  
|Regla|Descripción|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Los tipos que poseen campos descartables deben ser descartables|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Quitar los finalizadores vacíos|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Los campos desechables se deben desechar|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Sobrecargar el operador equals al invalidar ValueType.Equals|



