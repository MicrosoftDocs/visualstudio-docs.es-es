---
title: 'CA1724: los nombres de tipo no deben coincidir con los espacios de nombres | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa0b73b6608f0dfd5daa4b770b7d780e64704c99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544435"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Los nombres de tipo no deben coincidir con los espacios de nombres
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|Identificador de comprobación|CA1724|
|Category|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un nombre de tipo coincide con [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] los nombres de un espacio de nombres en una comparación sin distinción entre mayúsculas y minúsculas.

## <a name="rule-description"></a>Descripción de la regla
 Los nombres de tipo no deben coincidir con los nombres de espacios de nombres definidos en la biblioteca de clases de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Infringir esta regla puede reducir la utilidad de la biblioteca.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Seleccione un nombre de tipo que no coincida con el nombre de un espacio de nombres de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] biblioteca de clases.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 En el desarrollo nuevo, no se produce ningún escenario conocido en el que debe suprimir una advertencia de esta regla. Antes de suprimir la advertencia, considere detenidamente cómo puede confundir los usuarios de la biblioteca con el nombre coincidente. En el caso de las bibliotecas de envío, es posible que tenga que suprimir una advertencia de esta regla.
