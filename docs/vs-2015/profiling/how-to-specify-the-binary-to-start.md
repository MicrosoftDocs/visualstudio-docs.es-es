---
title: Procedimiento Especificar el binario de inicio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 919e84393cf4aef929a504aadbefe905afe24bfb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203432"
---
# <a name="how-to-specify-the-binary-to-start"></a>Procedimiento Especificación del binario de inicio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para generar perfiles de binarios, como los archivos DLL, debe escribir información en el cuadro de diálogo **\<Destino > Páginas de propiedades**. Esta información indica dónde puede encontrar el proyecto DLL la aplicación que realiza la llamada.  
  
 **Requisitos**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-executable-to-start"></a>Para especificar el archivo ejecutable para iniciar  
  
1. En el **Explorador de rendimiento**, haga clic con el botón derecho en el binario de destino y después haga clic en **Propiedades**.  
  
2. En el cuadro de diálogo **Páginas de propiedades**, haga clic en las propiedades **Iniciar**.  
  
3. Seleccione la casilla **Invalidar propiedades del proyecto**.  
  
4. En el cuadro de texto **Ejecutable para iniciar**, especifique la ubicación del archivo.  
  
5. En el cuadro de texto **Argumentos**, especifique los argumentos necesarios para iniciar la aplicación.  
  
6. En el cuadro de texto **Directorio de trabajo**, especifique la ubicación del directorio.  
  
7. Haga clic en **OK**.  
  
## <a name="see-also"></a>Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)
