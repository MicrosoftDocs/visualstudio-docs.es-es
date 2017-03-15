---
title: "C&#243;mo: Hacer referencia a informaci&#243;n de s&#237;mbolos de Windows | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "herramientas de rendimiento, servidores de símbolos"
  - "servidores, servidores de símbolos"
  - "herramientas de generación de perfiles, servidores de símbolos"
  - "servidores de símbolos"
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# C&#243;mo: Hacer referencia a informaci&#243;n de s&#237;mbolos de Windows
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las Herramientas de generación de perfiles de Visual Studio utilizan archivos de símbolos \(.pdb\) para resolver nombres simbólicos como los nombres de función en binarios del programa.  Puede seguir estos pasos para descargar y actualizar automáticamente en el equipo local los archivos .pdb correctos para la versión de Windows.  
  
> [!NOTE]
>  Esta configuración no afecta a los informes existentes.  Sólo los informes creados después de especificar el servidor de símbolos tendrán la información de símbolos.  
  
 Para obtener más información, vea [Especificar archivos de código fuente y símbolos \(.pdb\)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### Utilizar el servidor de símbolos de Microsoft  
  
1.  Cree una carpeta que contenga la información de los archivos de símbolos, como C:\\SymbolCache.  
  
2.  En el menú **Herramientas**, haga clic en **Opciones**.  
  
     Aparecerá el cuadro de diálogo **Opciones**.  
  
3.  Expanda el árbol **Depuración** y, a continuación, haga clic en **Símbolos**.  
  
4.  En las **Ubicaciones de archivos de símbolos \(.pdb\)**, seleccione **Servidores de símbolos de Microsoft**  
  
5.  En **Almacenar símbolos en caché desde los servidores de símbolos a este directorio**, escriba la ruta de acceso de la carpeta creada en el paso 1, por ejemplo:  
  
     C:\\SymbolCache  
  
     También se puede hacer clic en los puntos suspensivos \(**…**\) y seleccionar un directorio del cuadro de diálogo de **Buscar carpeta**.  
  
## Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Cómo: Serializar la información de símbolos](../profiling/how-to-serialize-symbol-information.md)