---
title: "Validación de marco de gráficos | Documentos de Microsoft"
ms.custom: 
ms.date: 03/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9312ad8a96c5829aae21c87e78a0d5f2f0db1b35
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="graphics-frame-validation"></a>Validación de fotogramas de gráficos
<!-- VERSIONLESS -->
2017 de Visual Studio y mayor compatibilidad con la **marco de validación** herramienta.  La ventana de marco validación muestra errores y advertencias asociadas con la lista de eventos.  Para ver esta ventana, seleccione la **Vista > marco validación** menú.

![Validación de marco](media/gfx_diag_frame_validation.png)

Haga clic en el **ejecutar la validación** situado en la esquina superior izquierda para iniciar el análisis.  Puede tardar varios minutos en completarse según la complejidad del marco.  Los datos que aparece a continuación es una combinación de dos orígenes: los mensajes que D3D propio emite cuando [SDK capas](https://msdn.microsoft.com/library/windows/desktop/ff476881(v=vs.85).aspx) está habilitada y los datos que se recopilan en el estado interno de la herramienta de seguimiento. Una vez completado, verá varias columnas de datos:

**Columna**|**Descripción**
---|---
Id. de evento | Identificador que se asigna a una entrada en el [lista de eventos](graphics-event-list.md) ventana.
Gravedad | Daños, Error, advertencia, información o mensaje.
Categoría | Aplicación definida, varios, inicialización, limpieza, compilación, Estada la creación, configuración de estado, obtener estado, ejecución, manipulación de recursos, sombreador, redundante y no utilizado.
Mensaje | El mensaje asociado al evento.
Evento | El evento asociado con el error o advertencia.

## <a name="see-also"></a>Vea también  
[Diagnóstico de gráficos (depurar gráficos de DirectX)](visual-studio-graphics-diagnostics.md)   
<!-- /VERSIONLESS -->