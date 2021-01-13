---
title: EndCapture | Microsoft Docs
description: Use el método EndCapture de la clase VsgDbg para finalizar un intervalo de captura que se inició con BeginCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bbdc8f2dc4fa3ad25be8674b9a46bf02179aa1d
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727836"
---
# <a name="endcapture"></a>EndCapture
Finaliza un intervalo de captura que se inició con `BeginCapture`.

## <a name="syntax"></a>Sintaxis

```C++
void EndCapture();
```

## <a name="remarks"></a>Comentarios
 Un intervalo de captura suele abarcar un subconjunto de un fotograma, por ejemplo cuando desea capturar información de gráficos solo sobre algún tipo de llamada a Draw. Si el intervalo de captura abarca una llamada de presentación, se capturan dos fotogramas de información de gráficos. El primer fotograma abarca el intervalo entre la llamada a `BeginCapture` y la llamada de presentación; el segundo fotograma abarca el intervalo entre el primer evento de Direct3D después de la llamada de presentación y la llamada a `EndCapture`.

 Para capturar un intervalo, debe preparar la aplicación para capturar y grabar información de gráficos; es decir, debe haber llamado a [Init](init.md) mediante una instancia de la clase `VsgDbg` antes de llamar a `BeginCapture` o `EndCapture`.

## <a name="see-also"></a>Vea también
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)