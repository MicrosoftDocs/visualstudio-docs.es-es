---
title: 'Cómo: habilitar y deshabilitar el análisis de código automático para código administrado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 7c22d194-5fea-4f23-b02d-19344fa64a64
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d87cc57b31e63ae7aafa53c335df2b56f86a0409
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658097"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Cómo: Habilitar y deshabilitar el análisis de código automático para código administrado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede configurar el análisis de código para que se ejecute antes de cada compilación de un proyecto de código administrado. Puede establecer distintas propiedades de análisis de código para cada configuración de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

### <a name="to-enable-or-disable-automatic-code-analysis"></a>Para habilitar o deshabilitar el análisis de código automático

1. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto y, a continuación, haga clic en **propiedades**.

2. En el cuadro de diálogo Propiedades del proyecto, haga clic en **análisis de código**.

3. Especifique el tipo de compilación en la **configuración** y la plataforma de destino en **plataforma**.

4. Para habilitar o deshabilitar el análisis de código automático, Active o desactive la casilla **Habilitar análisis de código al compilar (define la constante CODE_ANALYSIS)** .
