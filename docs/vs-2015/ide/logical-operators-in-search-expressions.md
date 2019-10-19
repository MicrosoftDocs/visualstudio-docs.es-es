---
title: Operadores lógicos en expresiones de búsqueda | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d56f2dfc2924008a6be293fe1498f0ffe32abaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651437"
---
# <a name="logical-operators-in-search-expressions"></a>Operadores lógicos en expresiones de búsqueda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con los operadores lógicos puede restringir la búsqueda de contenido mediante la creación de expresiones de búsqueda más complejas a partir de expresiones más sencillas. Como se muestra en la tabla siguiente, los operadores lógicos especifican cómo se deben combinar varios términos de búsqueda en una consulta de búsqueda.

> [!IMPORTANT]
> Debe escribir los operadores lógicos con todas las letras en mayúsculas para que el motor de búsqueda los reconozca.

|Para buscar|Usar|Ejemplo|Resultado|
|-------------------|---------|-------------|------------|
|Ambos términos en el mismo tema|AND|dib AND paleta|Temas que contienen "dib" y "paleta".|
|Cualquier término en un tema|O|trama OR vector|Temas que contienen "trama" o "vector".|
|El primer término sin el segundo en el mismo tema|NOT|"sistema operativo" NOT DOS|Temas que contienen "sistema operativo", pero no "DOS".|
|Ambos términos muy próximos en un tema|CERCA_DE|usuario NEAR kernel|Temas que contienen "usuario" cerca de "kernel".|

## <a name="see-also"></a>Otras referencias
 [Sugerencias para la búsqueda de texto completo](../ide/full-text-search-tips.md) [Buscar información](../ide/locate-information.md)
