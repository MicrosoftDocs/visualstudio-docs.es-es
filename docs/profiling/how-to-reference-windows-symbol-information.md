---
title: "Cómo: Hacer referencia a información de símbolos de Windows | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 09e17cc1e28ad520f76d60c3411de4803a2b4b96
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-reference-windows-symbol-information"></a>Cómo: Hacer referencia a información de símbolos de Windows
Las herramientas de generación de perfiles de Visual Studio utilizan archivos de símbolos (.pdb) para resolver nombres simbólicos como los nombres de función en binarios del programa. Puede seguir estos pasos para descargar y actualizar automáticamente los archivos .pdb correctos para la versión de Windows en el equipo local.  
  
> [!NOTE]
>  Esta configuración no afecta a los informes existentes. Solo los informes creados después de especificar el servidor de símbolos tendrán la información de símbolos.  
  
 Para obtener más información, consulte [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### <a name="to-use-the-microsoft-symbol-server"></a>Para utilizar el servidor de símbolos de Microsoft  
  
1.  Cree una carpeta para que contenga la información del archivo de símbolos, como C:\SymbolCache.  
  
2.  En el menú **Herramientas** , haga clic en **Opciones**.  
  
     Aparecerá el cuadro de diálogo **Opciones** .  
  
3.  Expanda el árbol **Depuración** y después haga clic en **Símbolos**.  
  
4.  En **Ubicaciones de archivos de símbolos (.pdb)**, seleccione **Servidores de símbolos de Microsoft**  
  
5.  En **Almacenar símbolos en caché desde los servidores de símbolos a este directorio**, escriba la ruta de acceso de la carpeta que creó en el paso 1, por ejemplo:  
  
     **C:\SymbolCache**  
  
     También puede hacer clic en el botón de puntos suspensivos (**...**) y después seleccionar un directorio en el cuadro de diálogo **Buscar carpeta**.  
  
## <a name="see-also"></a>Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Cómo: Serializar la información de símbolos](../profiling/how-to-serialize-symbol-information.md)