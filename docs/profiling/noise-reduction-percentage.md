---
title: Porcentaje de reducción de ruido | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.filter
helpviewer_keywords:
- Concurrency Visualizer, Noise Reduction Percentage
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e18484154e3fd1664eae1ccbdd5fd787d3d1c3b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960833"
---
# <a name="noise-reduction-percentage"></a>Porcentaje de reducción de ruido
De forma predeterminada, el valor del porcentaje de reducción de ruido es 2. Solo las entradas que tienen un porcentaje de tiempo inclusivo mayor o igual que esta configuración se muestran en el árbol de llamadas. Si cambia el valor, puede controlar el número de entradas que se muestran en el árbol de llamadas. Por ejemplo, cambiar el valor a 10 mostrará solo entradas del árbol de llamadas que tienen un tiempo inclusivo mayor o igual al 10 %. Al aumentar la configuración, puede centrarse en las entradas que tienen un impacto mayor en el rendimiento del proceso.