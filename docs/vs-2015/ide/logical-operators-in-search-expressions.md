---
title: Operadores lógicos en expresiones de búsqueda | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8337c455ac283e7b9abbf70c39493b31c01a7d06
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212542"
---
# <a name="logical-operators-in-search-expressions"></a>Operadores lógicos en expresiones de búsqueda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con los operadores lógicos puede restringir la búsqueda de contenido mediante la creación de expresiones de búsqueda más complejas a partir de expresiones más sencillas. Como se muestra en la tabla siguiente, los operadores lógicos especifican cómo se deben combinar varios términos de búsqueda en una consulta de búsqueda.  
  
> [!IMPORTANT]
>  Debe escribir los operadores lógicos con todas las letras en mayúsculas para que el motor de búsqueda los reconozca.  
  
|Para buscar|Usar|Ejemplo|Resultado|  
|-------------------|---------|-------------|------------|  
|Ambos términos en el mismo tema|AND|dib AND paleta|Temas que contienen "dib" y "paleta".|  
|Cualquier término en un tema|O|trama OR vector|Temas que contienen "trama" o "vector".|  
|El primer término sin el segundo en el mismo tema|NOT|"sistema operativo" NOT DOS|Temas que contienen "sistema operativo", pero no "DOS".|  
|Ambos términos muy próximos en un tema|CERCA_DE|usuario NEAR kernel|Temas que contienen "usuario" cerca de "kernel".|  
  
## <a name="see-also"></a>Vea también  
 [Sugerencias para la búsqueda de texto completo](../ide/full-text-search-tips.md)   
 [Encontrar información](../ide/locate-information.md)



