---
title: Porcentaje de reducción de ruido | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.filter
helpviewer_keywords:
- Concurrency Visualizer, Noise Reduction Percentage
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9d3021aef3f9a2e11849991327a6ef8783b62439
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62794318"
---
# <a name="noise-reduction-percentage"></a>Porcentaje de reducción de ruido
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

De forma predeterminada, el valor del porcentaje de reducción de ruido es 2. Solo las entradas que tienen un porcentaje de tiempo inclusivo mayor o igual que esta configuración se muestran en el árbol de llamadas. Si cambia el valor, puede controlar el número de entradas que se muestran en el árbol de llamadas. Por ejemplo, cambiar el valor a 10 mostrará solo entradas del árbol de llamadas que tienen un tiempo inclusivo mayor o igual al 10 %. Al aumentar la configuración, puede centrarse en las entradas que tienen un impacto mayor en el rendimiento del proceso.
