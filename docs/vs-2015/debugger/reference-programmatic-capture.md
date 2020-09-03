---
title: Referencia (captura mediante programación) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cebeb7eb651c11b5f560b981df30213fc726c66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162262"
---
# <a name="reference-programmatic-capture"></a>Referencia (captura mediante programación)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagnóstico de gráficos admite el control mediante programación de sus características de captura a través de la API de captura mediante programación. Puede utilizar esta API para alternar y agregar mensajes al HUD (pantalla de visualización frontal) de diagnóstico de gráficos, inicializar y crear archivos de registro de gráficos, y capturar información de gráficos.  
  
## <a name="programmatic-capture-apis"></a>API de captura mediante programación  
  
### <a name="classes"></a>Clases  
  
|NOMBRE|Descripción|  
|----------|-----------------|  
|[Case VsgDbg](../debugger/vsgdbg-class.md)|Representa la interfaz a través de la que se controla mediante programación el componente de aplicación de diagnóstico de gráficos.|  
  
### <a name="preprocessor-symbols"></a>Símbolos de preprocesador  
  
|NOMBRE|Descripción|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)|Define por su presencia si el archivo de registro de gráficos se guarda en el directorio de archivos temporales del usuario.|  
|[VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)|Define el nombre de archivo predeterminado del archivo de registro de gráficos.|  
|[VSG_NODEFAULT_INSTANCE](../debugger/vsg-nodefault-instance.md)|Define por su presencia si se proporciona una instancia predeterminada de la clase `VsgDbg`.|  
  
## <a name="related-articles"></a>Artículos relacionados  
  
|Title|Descripción|  
|-----------|-----------------|  
|[Capturing Graphics Information](../debugger/capturing-graphics-information.md)|Muestra cómo capturar información de gráficos desde la aplicación basada en DirectX para que pueda utilizar las herramientas de Diagnóstico de gráficos de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] con el fin de diagnosticar problemas de representación.|  
|[Información general](../debugger/overview-of-visual-studio-graphics-diagnostics.md)|Muestra cómo Diagnóstico de gráficos puede ayudarle a depurar errores de representación en juegos y aplicaciones de DirectX.|
