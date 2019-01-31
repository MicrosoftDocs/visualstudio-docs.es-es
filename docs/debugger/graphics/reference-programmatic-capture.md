---
title: Referencia (captura mediante programación) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 892831423ccc3607db1b3f162fb79f4508764afa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006756"
---
# <a name="reference-programmatic-capture"></a>Referencia (captura mediante programación)
Diagnóstico de gráficos admite el control mediante programación de sus características de captura a través de la API de captura mediante programación. Puede utilizar esta API para alternar y agregar mensajes al HUD (pantalla de visualización frontal) de diagnóstico de gráficos, inicializar y crear archivos de registro de gráficos, y capturar información de gráficos.  

## <a name="programmatic-capture-apis"></a>API de captura mediante programación  

### <a name="classes"></a>Clases  

|nombre|Descripción|  
|----------|-----------------|  
|[Case VsgDbg](vsgdbg-class.md)|Representa la interfaz a través de la que se controla mediante programación el componente de aplicación de diagnóstico de gráficos.|  

### <a name="preprocessor-symbols"></a>Símbolos de preprocesador  

|nombre|Descripción|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Define por su presencia si el archivo de registro de gráficos se guarda en el directorio de archivos temporales del usuario.|  
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Define el nombre de archivo predeterminado del archivo de registro de gráficos.|  
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Define por su presencia si se proporciona una instancia predeterminada de la clase `VsgDbg`.|  

## <a name="related-articles"></a>Artículos relacionados  

| Title | Descripción |
| - | - |
| [Capturing Graphics Information](capturing-graphics-information.md) | Muestra cómo capturar información de gráficos desde la aplicación basada en DirectX para que pueda utilizar las herramientas de Diagnóstico de gráficos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con el fin de diagnosticar problemas de representación. |
| [Información general](overview-of-visual-studio-graphics-diagnostics.md) | Muestra cómo Diagnóstico de gráficos puede ayudarle a depurar errores de representación en juegos y aplicaciones de DirectX. |
