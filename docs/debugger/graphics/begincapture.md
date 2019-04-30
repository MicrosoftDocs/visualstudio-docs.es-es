---
title: BeginCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e714245ff2585f9de0b998160ce08f04c88b097
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62896441"
---
# <a name="begincapture"></a>BeginCapture
Inicia un intervalo de captura que finalizará con `EndCapture`.

## <a name="syntax"></a>Sintaxis

```C++
void BeginCapture();
```

## <a name="remarks"></a>Comentarios
 Un intervalo de captura suele abarcar un subconjunto de un fotograma, por ejemplo cuando desea capturar información de gráficos solo sobre algún tipo de llamada a Draw. Si el intervalo de captura abarca una llamada de presentación, se capturan dos fotogramas de información de gráficos. El primer fotograma abarca el intervalo entre la llamada a `BeginCapture` y la llamada de presentación; el segundo fotograma abarca el intervalo entre el primer evento de Direct3D después de la llamada de presentación y la llamada a `EndCapture`.

 Para capturar un intervalo, debe preparar la aplicación para capturar y grabar información de gráficos, es decir, debe haber llamado a [Init](init.md) a través de una instancia de la `VsgDbg` antes de llamar a la clase `BeginCapture` o `EndCapture`.

## <a name="see-also"></a>Vea también
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)