---
title: EndCapture | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f587b10fea4b593234be2a536baa13cf7b3db66
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="endcapture"></a>EndCapture
Finaliza un intervalo de captura que se inició con `BeginCapture`.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
void EndCapture();  
```  
  
## <a name="remarks"></a>Comentarios  
 Un intervalo de captura suele abarcar un subconjunto de un fotograma, por ejemplo cuando desea capturar información de gráficos solo sobre algún tipo de llamada a Draw. Si el intervalo de captura abarca una llamada de presentación, se capturan dos fotogramas de información de gráficos. El primer fotograma abarca el intervalo entre la llamada a `BeginCapture` y la llamada de presentación; el segundo fotograma abarca el intervalo entre el primer evento de Direct3D después de la llamada de presentación y la llamada a `EndCapture`.  
  
 Para capturar un intervalo, debe preparar la aplicación para capturar y registrar información de gráficos, es decir, debe haber llamado [Init](init.md) a través de una instancia de la `VsgDbg` antes de llamar a la clase `BeginCapture` o `EndCapture`.  
  
## <a name="see-also"></a>Vea también  
 [BeginCapture](begincapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)