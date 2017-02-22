---
title: "Programaci&#243;n de Visual Studio Tools para Unity | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "crdun"
manager: "crdun"
---
# Programaci&#243;n de Visual Studio Tools para Unity
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En esta sección encontrará ejemplos de uso de la API de Visual Studio Tools para Unity.  
  
## Ejemplos  
 Estos son algunos ejemplos que muestran cómo se puede utilizar la API de Visual Studio Tools para Unity.  
  
### Personalizar archivos de proyecto creados por VSTU  
 Visual Studio Tools para Unity ofrece una devolución de llamada al estilo de Unity durante la generación del archivo de proyecto.  Para obtener información sobre cómo modificar el archivo de proyecto cada vez que se vuelva a generar, consulte [Ejemplo: Generación de archivo de proyecto](../cross-platform/customize-project-files-created-by-vstu.md).  
  
### Compartir la devolución de llamada de registro de Unity con VSTU  
 Visual Studio Tools para Unity registra una devolución de llamada de registro con Unity para poder transmitir su consola a Visual Studio.  Si los scripts del editor también registran una devolución de llamada de registro con Unity, la devolución de llamada de VSTU puede interferir con la devolución de llamada.  Para obtener información sobre cómo compartir la devolución de llamada de registro de Unity con VSTU, consulte [Ejemplo: Devolución de llamada de registro](../cross-platform/share-the-unity-log-callback-with-vstu.md).