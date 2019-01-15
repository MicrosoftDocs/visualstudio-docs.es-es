---
title: Validación de fotogramas de gráficos | Microsoft Docs
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2add8032a1fa5da983c66ab5cfabede78f4c65c8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891779"
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
[Diagnóstico de gráficos (depuración de gráficos DirectX)](visual-studio-graphics-diagnostics.md)   
<!-- /VERSIONLESS -->