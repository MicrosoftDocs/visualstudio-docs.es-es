---
title: CaptureCurrentFrame | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fcdeee28077f2c7affd1c4cd1f82d8c8cb29494b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Captura el resto del fotograma actual en el archivo de registro de gráficos.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Comentarios  
 Si hay otra captura en curso actualmente, como una captura que inició la función `BeginCapture`, esa captura se completa y se registra en el registro de gráficos como un fotograma distinto. Inmediatamente después, el diagnóstico de gráficos empieza a capturar el resto del fotograma actual, que también se registra como un fotograma distinto. El final del fotograma actual se marca mediante una llamada de presentación.  
  
 Para capturar un fotograma, debe preparar la aplicación para capturar y registrar información de gráficos, es decir, debe haber llamado [Init](init.md) a través de una instancia de la `VsgDbg` antes de llamar a la clase `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>Vea también  
 [Init](init.md)   
 [BeginCapture](begincapture.md)