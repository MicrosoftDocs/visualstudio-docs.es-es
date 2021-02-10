---
title: CaptureCurrentFrame | Microsoft Docs
description: Use el método CaptureCurrentFrame de la clase VsgDbg para capturar el resto del fotograma actual en el archivo de registro de gráficos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94c55a34ee71f8002d31613d64ff978f0a546b72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874553"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Captura el resto del fotograma actual en el archivo de registro de gráficos.

## <a name="syntax"></a>Sintaxis

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Comentarios
 Si hay otra captura en curso actualmente, como una captura que inició la función `BeginCapture`, esa captura se completa y se registra en el registro de gráficos como un fotograma distinto. Inmediatamente después, el diagnóstico de gráficos empieza a capturar el resto del fotograma actual, que también se registra como un fotograma distinto. El final del fotograma actual se marca mediante una llamada de presentación.

 Para capturar un fotograma, debe preparar la aplicación para capturar y grabar información de gráficos, es decir, debe haber llamado a [Init](init.md) mediante una instancia de la clase `VsgDbg` antes de llamar a `CaptureCurrentFrame`.

## <a name="see-also"></a>Vea también
- [Init](init.md)
- [BeginCapture](begincapture.md)