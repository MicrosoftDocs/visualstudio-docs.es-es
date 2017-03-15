---
title: "Referencia (captura mediante programaci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Referencia (captura mediante programaci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diagnóstico de gráficos admite el control mediante programación de sus características de captura a través de la API de captura mediante programación.  Puede utilizar esta API para alternar y agregar mensajes al HUD \(pantalla de visualización frontal\) de diagnóstico de gráficos, inicializar y crear archivos de registro de gráficos, y capturar información de gráficos.  
  
## API de captura mediante programación  
  
### Clases  
  
|Name|Descripción|  
|----------|-----------------|  
|[VsgDbg \(Clase\)](../debugger/vsgdbg-class.md)|Representa la interfaz a través de la que se controla mediante programación el componente de aplicación de diagnóstico de gráficos.|  
  
### Símbolos de preprocesador  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[DONT\_SAVE\_VSGLOG\_TO\_TEMP](../debugger/dont-save-vsglog-to-temp.md)|Define por su presencia si el archivo de registro de gráficos se guarda en el directorio de archivos temporales del usuario.|  
|[VSG\_DEFAULT\_RUN\_FILENAME](../debugger/vsg-default-run-filename.md)|Define el nombre de archivo predeterminado del archivo de registro de gráficos.|  
|[VSG\_NODEFAULT\_INSTANCE](../debugger/vsg-nodefault-instance.md)|Define por su presencia si se proporciona una instancia predeterminada de la clase `VsgDbg`.|  
  
## Artículos relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Capturar información de gráficos](../debugger/capturing-graphics-information.md)|Muestra cómo capturar información de gráficos desde la aplicación basada en DirectX para que pueda utilizar las herramientas de Diagnóstico de gráficos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con el fin de diagnosticar problemas de representación.|  
|[Información general](../debugger/overview-of-visual-studio-graphics-diagnostics.md)|Muestra cómo Diagnóstico de gráficos puede ayudarle a depurar errores de representación en juegos y aplicaciones de DirectX.|