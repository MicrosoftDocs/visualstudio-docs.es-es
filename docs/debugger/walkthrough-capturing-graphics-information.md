---
title: "Tutorial: Capturar informaci&#243;n de gr&#225;ficos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Tutorial: Capturar informaci&#243;n de gr&#225;ficos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tutorial se muestra cómo utilizar el Diagnóstico de gráficos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para capturar manualmente información de gráficos desde una aplicación de Direct3D.  
  
 En el tutorial se muestran las tareas siguientes:  
  
-   Enlazar el Diagnóstico de gráficos con la aplicación  
  
-   Capturar información de gráficos  
  
## Capturar información de gráficos  
 Para utilizar las herramientas de Diagnóstico de gráficos, antes debe capturar la información gráfica en la que se basa. Para habilitar la captura, use el comando **Iniciar diagnóstico** para enlazar el Diagnóstico de gráficos con la aplicación cuando se inicia.  
  
#### Para habilitar la captura de información de gráficos después de que se cargue un proyecto o una solución  
  
1.  En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], cargue un archivo de proyecto o solución de la aplicación de la que quiere capturar información de gráficos.  
  
2.  En la barra de herramientas Diagnóstico de gráficos, elija **Iniciar diagnóstico**.  
  
#### Para habilitar la captura de información de gráficos sin cargar un proyecto ni una solución  
  
1.  En la barra de menús, elija **Archivo**, **Abrir**, **Proyecto o solución**. Aparecerá el cuadro de diálogo **Abrir proyecto**.  
  
2.  En lugar de un archivo de proyecto o solución, especifique el archivo ejecutable de la aplicación de la que quiere capturar información de gráficos y luego elija **Abrir**.  
  
3.  En la barra de menús, elija **Depurar**, **Gráficos**, **Iniciar diagnóstico**.  
  
 Cuando inicie la aplicación y esté procesando fotogramas, podrá capturar información de gráficos.  
  
#### Cómo capturar información de gráficos  
  
-   En la barra de herramientas Diagnóstico de gráficos, elija el botón **Capturar**.![Icono de botón de captura de gráficos](../debugger/media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")  
  
     O bien  
  
     Con el foco en la aplicación, presione **Imprimir pantalla**.  
  
 Cada vez que se captura información sobre un fotograma, el Diagnóstico de gráficos registra los eventos de Direct3D y el estado asociado y agrega dichos datos a un registro de gráficos. Se crea un nuevo registro de gráficos para cada sesión de Diagnóstico de gráficos. Para obtener información sobre los registros de gráficos, consulte [Información general](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## Pasos siguientes  
 En este tutorial se ha mostrado cómo capturar información de gráficos de forma manual. El paso siguiente puede ser:  
  
-   Aprenda cómo analizar la información de gráficos capturada mediante las herramientas de Diagnóstico de gráficos. Vea [Información general](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## Vea también  
 [Capturar información de gráficos](../debugger/capturing-graphics-information.md)