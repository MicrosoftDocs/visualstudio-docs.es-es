---
title: Advertencias de criptografía | Documentos de Microsoft
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c573d461b477bbcdc7e988ea66f03d5a7cc0fdb6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201447"
---
# <a name="cryptography-warnings"></a>Advertencias de criptografía
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las advertencias de criptografía admiten bibliotecas y aplicaciones más seguras gracias al uso correcto de criptografía. Estas advertencias ayudan a evitar los errores de seguridad en su programa. Si deshabilita cualquier advertencia de este tipo, se debe indicar el motivo claramente en el código además de informar al responsable de seguridad designado a ese proyecto de desarrollo.  
  
|Regla|DESCRIPCIÓN|  
|----------|-----------------|  
|[CA5350: No Use algoritmos criptográficos no seguros](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Las funciones hash y los algoritmos de cifrado débiles se usan hoy en día para numerosos propósitos, pero no se recomiendan para garantizar la confidencialidad o la integridad de los datos que se protegen.        Esta regla se desencadena cuando se encuentran los algoritmos TripleDES, SHA1 o RIPEMD160 en el código.|  
|[CA5351: Do Not Use Broken Cryptographic Algorithms (No use algoritmos criptográficos rotos)](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Los algoritmos criptográficos rotos no se consideran seguros y debe desalentarse su uso. Esta regla se desencadena cuando encuentra el algoritmo hash MD5 o los algoritmos de cifrado DES o RC2 en el código.|
