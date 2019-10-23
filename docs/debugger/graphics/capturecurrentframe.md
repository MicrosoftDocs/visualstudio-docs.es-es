---
title: CaptureCurrentFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9967d776845088e707035c7b1c56855ac80af82
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736138"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Captura el resto del fotograma actual en el archivo de registro de gráficos.

## <a name="syntax"></a>Sintaxis

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Comentarios
 Si hay otra captura en curso actualmente, como una captura que inició la función `BeginCapture`, esa captura se completa y se registra en el registro de gráficos como un fotograma distinto. Inmediatamente después, el diagnóstico de gráficos empieza a capturar el resto del fotograma actual, que también se registra como un fotograma distinto. El final del fotograma actual se marca mediante una llamada de presentación.

 Para capturar un fotograma, debe preparar la aplicación para capturar y grabar información de gráficos, es decir, debe haber llamado a [init](init.md) a través de una instancia de la clase `VsgDbg` antes de llamar a `CaptureCurrentFrame`.

## <a name="see-also"></a>Vea también
- [Init](init.md)
- [BeginCapture](begincapture.md)