---
title: Porcentaje de reducción de ruido | Microsoft Docs
description: Obtenga más información sobre el valor de porcentaje de la reducción de ruido y cómo puede controlar el número de entradas que se muestran en el árbol de llamadas.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.filter
helpviewer_keywords:
- Concurrency Visualizer, Noise Reduction Percentage
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 531ff082197ca1f7e63008aeda1c27e083b569de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922420"
---
# <a name="noise-reduction-percentage"></a>Porcentaje de reducción de ruido
De forma predeterminada, el valor del porcentaje de reducción de ruido es 2. Solo las entradas que tienen un porcentaje de tiempo inclusivo mayor o igual que esta configuración se muestran en el árbol de llamadas. Si cambia el valor, puede controlar el número de entradas que se muestran en el árbol de llamadas. Por ejemplo, cambiar el valor a 10 mostrará solo entradas del árbol de llamadas que tienen un tiempo inclusivo mayor o igual al 10 %. Al aumentar la configuración, puede centrarse en las entradas que tienen un impacto mayor en el rendimiento del proceso.