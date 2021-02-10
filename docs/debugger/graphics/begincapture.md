---
title: BeginCapture | Microsoft Docs
description: Use el método BeginCapture de la clase VsgDbg para iniciar un intervalo de captura que finalizará con EndCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9e002a66ec3ec121a4cdc20ffb9ce59c1ed9dc0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874579"
---
# <a name="begincapture"></a>BeginCapture
Inicia un intervalo de captura que finalizará con `EndCapture`.

## <a name="syntax"></a>Sintaxis

```C++
void BeginCapture();
```

## <a name="remarks"></a>Comentarios
 Un intervalo de captura suele abarcar un subconjunto de un fotograma, por ejemplo cuando desea capturar información de gráficos solo sobre algún tipo de llamada a Draw. Si el intervalo de captura abarca una llamada de presentación, se capturan dos fotogramas de información de gráficos. El primer fotograma abarca el intervalo entre la llamada a `BeginCapture` y la llamada de presentación; el segundo fotograma abarca el intervalo entre el primer evento de Direct3D después de la llamada de presentación y la llamada a `EndCapture`.

 Para capturar un intervalo, debe preparar la aplicación para capturar y grabar información de gráficos; es decir, debe haber llamado a [Init](init.md) mediante una instancia de la clase `VsgDbg` antes de llamar a `BeginCapture` o `EndCapture`.

## <a name="see-also"></a>Vea también
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)