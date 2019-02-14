---
title: EndCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8f72e3bcd3755fe59af5207586cf9cf03d432f4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54967630"
---
# <a name="endcapture"></a>EndCapture
Finaliza un intervalo de captura que se inició con `BeginCapture`.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
void EndCapture();  
```  
  
## <a name="remarks"></a>Comentarios  
 Un intervalo de captura suele abarcar un subconjunto de un fotograma, por ejemplo cuando desea capturar información de gráficos solo sobre algún tipo de llamada a Draw. Si el intervalo de captura abarca una llamada de presentación, se capturan dos fotogramas de información de gráficos. El primer fotograma abarca el intervalo entre la llamada a `BeginCapture` y la llamada de presentación; el segundo fotograma abarca el intervalo entre el primer evento de Direct3D después de la llamada de presentación y la llamada a `EndCapture`.  
  
 Para capturar un intervalo, debe preparar la aplicación para capturar y grabar información de gráficos, es decir, debe haber llamado a [Init](init.md) a través de una instancia de la `VsgDbg` antes de llamar a la clase `BeginCapture` o `EndCapture`.  
  
## <a name="see-also"></a>Vea también  
 [BeginCapture](begincapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)