---
title: Validación de fotogramas gráficos | Microsoft Docs
description: Obtenga información sobre la herramienta de validación de fotogramas para gráficos en Visual Studio. Esta herramienta muestra los errores y advertencias asociados a la lista de eventos.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9d52d04565b03d988d5d01a64e561fc0da8a16e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885253"
---
# <a name="graphics-frame-validation"></a>Validación de fotogramas gráficos
<!-- VERSIONLESS -->
Visual Studio 2017 y superior admiten la herramienta **Validación de fotogramas**.  La ventana Validación de fotogramas muestra errores y advertencias asociados a la lista de eventos.  Para ver esta ventana, seleccione el menú **Ver > Validación de fotogramas**.

![Validación de fotogramas](media/gfx_diag_frame_validation.png)

Haga clic en el botón **Ejecutar validación** situado en la esquina superior izquierda para iniciar el análisis.  Puede tardar varios minutos en completarse, en función de la complejidad del fotograma.  Los datos que aparecen aquí son una combinación de dos orígenes: los mensajes que D3D emite cuando las [capas del SDK](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) están habilitadas y los datos recopilados del seguimiento de estado interno de la herramienta. Una vez terminado, se ven varias columnas de datos:

| **Columna** | **Descripción** |
|------------| - |
| Id. de evento | Identificador que se asigna a una entrada de la ventana [Lista de eventos](graphics-event-list.md). |
| Gravedad | Daño, Error, Advertencia, Información o Mensaje. |
| Categoría | Definido por la aplicación, Varios, Inicialización, Limpieza, Compilación, Creación de estado, Configuración de estado, Obtención de estado, Ejecución, Manipulación de recursos, Sombreador, Redundante y Sin usar. |
| Mensaje | Mensaje asociado al evento. |
| evento | Evento asociado al error o advertencia. |

## <a name="see-also"></a>Vea también
[Diagnóstico de gráficos (Depurar gráficos de DirectX)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->