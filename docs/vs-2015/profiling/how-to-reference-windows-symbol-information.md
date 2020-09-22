---
title: 'Cómo: Hacer referencia a información de símbolos de Windows | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7a123a42c1a46faf67fb5b63b1ab4ef300735f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843090"
---
# <a name="how-to-reference-windows-symbol-information"></a>Cómo: Hacer referencia a información de símbolos de Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las herramientas de generación de perfiles de Visual Studio utilizan archivos de símbolos (.pdb) para resolver nombres simbólicos como los nombres de función en binarios del programa. Puede seguir estos pasos para descargar y actualizar automáticamente los archivos .pdb correctos para la versión de Windows en el equipo local.  
  
> [!NOTE]
> Esta configuración no afecta a los informes existentes. Solo los informes creados después de especificar el servidor de símbolos tendrán la información de símbolos.  
  
 Para obtener más información, consulte [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### <a name="to-use-the-microsoft-symbol-server"></a>Para utilizar el servidor de símbolos de Microsoft  
  
1. Cree una carpeta para que contenga la información del archivo de símbolos, como C:\SymbolCache.  
  
2. En el menú **Herramientas** , haga clic en **Opciones**.  
  
     Aparecerá el cuadro de diálogo **Opciones** .  
  
3. Expanda el árbol **Depuración** y después haga clic en **Símbolos**.  
  
4. En **Ubicaciones de archivos de símbolos (.pdb)** , seleccione **Servidores de símbolos de Microsoft**  
  
5. En **Almacenar símbolos en caché desde los servidores de símbolos a este directorio**, escriba la ruta de acceso de la carpeta que creó en el paso 1, por ejemplo:  
  
     **C:\SymbolCache**  
  
     También puede hacer clic en el botón de puntos suspensivos ( **...** ) y después seleccionar un directorio en el cuadro de diálogo **Buscar carpeta**.  
  
## <a name="see-also"></a>Consulte también  
 [Configuración de sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Cómo: serializar la información de símbolos](../profiling/how-to-serialize-symbol-information.md)
