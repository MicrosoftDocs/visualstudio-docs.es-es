---
title: 'Tutorial: Captura de información de gráficos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68ad8e09558aad1b6a4172acd0aa8b4749661854
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930113"
---
# <a name="walkthrough-capturing-graphics-information"></a>Tutorial: Capturar información de gráficos
En este tutorial se muestra cómo utilizar el Diagnóstico de gráficos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para capturar manualmente información de gráficos desde una aplicación de Direct3D.  
  
 En el tutorial se muestran las tareas siguientes:  
  
-   Enlazar el Diagnóstico de gráficos con la aplicación  
  
-   Capturar información de gráficos  
  
## <a name="capturing-graphics-information"></a>Capturar información de gráficos  
 Para utilizar las herramientas de Diagnóstico de gráficos, antes debe capturar la información gráfica en la que se basa. Para habilitar la captura, use el comando **Iniciar diagnóstico** para enlazar el Diagnóstico de gráficos con la aplicación cuando se inicia.  
  
#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Para habilitar la captura de información de gráficos después de que se cargue un proyecto o una solución  
  
1. En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], cargue un archivo de proyecto o solución de la aplicación de la que quiere capturar información de gráficos.  
  
2. En la barra de herramientas Diagnóstico de gráficos, elija **Iniciar diagnóstico**.  
  
#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Para habilitar la captura de información de gráficos sin cargar un proyecto ni una solución  
  
1. En la barra de menús, elija **Archivo**, **Abrir**, **Proyecto o solución**. Aparecerá el cuadro de diálogo **Abrir proyecto** .  
  
2. En lugar de un archivo de proyecto o solución, especifique el archivo ejecutable de la aplicación de la que quiere capturar información de gráficos y luego elija **Abrir**.  
  
3. En la barra de menús, elija **Depurar**, **Gráficos**, **Iniciar diagnóstico**.  
  
   Cuando inicie la aplicación y esté procesando fotogramas, podrá capturar información de gráficos.  
  
#### <a name="to-capture-graphics-information"></a>Cómo capturar información de gráficos  
  
- En la barra de herramientas Diagnóstico de gráficos, elija el botón **Capturar** . ![Icono de botón de captura de gráficos](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")  
  
   o bien  
  
   Con el foco en la aplicación, presione **Imprimir pantalla**.  
  
  Cada vez que se captura información sobre un fotograma, el Diagnóstico de gráficos registra los eventos de Direct3D y el estado asociado y agrega dichos datos a un registro de gráficos. Se crea un nuevo registro de gráficos para cada sesión de Diagnóstico de gráficos. Para obtener información acerca de los registros de gráficos, vea [Introducción](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="next-steps"></a>Pasos siguientes  
 En este tutorial se ha mostrado cómo capturar información de gráficos de forma manual. El paso siguiente puede ser:  
  
-   Aprenda cómo analizar la información de gráficos capturada mediante las herramientas de Diagnóstico de gráficos. Consulte [Introducción](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Vea también  
 [Capturing Graphics Information](capturing-graphics-information.md)