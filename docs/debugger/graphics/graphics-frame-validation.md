---
title: Validación de fotogramas de gráficos | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0cdfdee83a9c78069b3f086ef84b280ba9328e4f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850885"
---
# <a name="graphics-frame-validation"></a>Validación de fotogramas de gráficos
<!-- VERSIONLESS --> Visual Studio 2017 y mayor compatibilidad con la **validación de fotogramas** herramienta.  La ventana de validación de fotogramas muestra errores y advertencias asociadas con la lista de eventos.  Para ver esta ventana, seleccione el **Ver > validación de fotogramas** menú.

![Validación de fotogramas](media/gfx_diag_frame_validation.png)

Haga clic en el **ejecutar validación** situado en la esquina superior izquierda para iniciar el análisis.  Pueden tardar varios minutos en completarse, según la complejidad del marco.  Los datos que aparece aquí es una combinación de dos orígenes: los mensajes que D3D propio cuando emite [capas del SDK](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) está habilitada y los datos que se recopilan desde el estado interno de la herramienta de seguimiento. Una vez que haya terminado, verá varias columnas de datos:


| **Columna** | **Descripción** |
|------------| - |
| Id. de evento | Id. que se asigna a una entrada en el [lista de eventos](graphics-event-list.md) ventana. |
| Gravedad | Daños, Error, advertencia, información o mensajes. |
| Categoría | Aplicación definida, vario, inicialización, limpieza, compilación, creación de estado, configuración de estado, obteniendo el estado, ejecución, manipulación de recursos, sombreador, redundante o sin usar. |
| Mensaje | El mensaje asociado al evento. |
| evento | El evento asociado al error o advertencia. |

## <a name="see-also"></a>Vea también  
[Diagnóstico de gráficos (depurar gráficos de DirectX)](visual-studio-graphics-diagnostics.md)   
<!-- /VERSIONLESS -->