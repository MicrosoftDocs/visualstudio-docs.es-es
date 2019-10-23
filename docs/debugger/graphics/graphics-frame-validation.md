---
title: Validación de fotogramas de gráficos | Microsoft Docs
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49248c6209f9e56e51551f6cd3d4af66ecac8b56
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735498"
---
# <a name="graphics-frame-validation"></a>Validación de fotogramas de gráficos
<!-- VERSIONLESS -->
Visual Studio 2017 y versiones posteriores admiten la herramienta de **validación de fotogramas** .  La ventana validación de fotogramas muestra errores y advertencias asociados a la lista de eventos.  Para ver esta ventana, seleccione el menú **ver > de validación de fotogramas** .

![Validación de fotogramas](media/gfx_diag_frame_validation.png)

Haga clic en el botón **Ejecutar validación** situado en la esquina superior izquierda para iniciar el análisis.  Puede tardar varios minutos en completarse, en función de la complejidad del marco.  Los datos que aparecen aquí son una combinación de dos orígenes: los mensajes que D3D se emiten cuando se habilitan las [capas de SDK](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) y los datos recopilados del seguimiento de estado interno de la herramienta. Una vez que haya finalizado, verá varias columnas de datos:

| **Columna** | **Descripción** |
|------------| - |
| Id. de evento | IDENTIFICADOR que se asigna a una entrada en la ventana [lista de eventos](graphics-event-list.md) . |
| Gravedad | Daños, errores, advertencias, información o mensaje. |
| Categoría | Aplicación definida, varios, inicialización, limpieza, compilación, creación de estado, configuración de estado, obtención de estado, ejecución, manipulación de recursos, sombreador, redundante y sin usar. |
| Mensaje | Mensaje asociado al evento. |
| evento | Evento asociado con el error o la advertencia. |

## <a name="see-also"></a>Vea también
[Diagnóstico de gráficos (Depurar gráficos de DirectX)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->