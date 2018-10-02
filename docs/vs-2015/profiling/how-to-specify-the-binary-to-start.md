---
title: 'Cómo: Especificar el binario de inicio | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec65dd3a5bcc812ff2f7c42ae4cbbba6080664db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577384"
---
# <a name="how-to-specify-the-binary-to-start"></a>Cómo: Especificar el binario de inicio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: especificar el binario de inicio](https://docs.microsoft.com/visualstudio/profiling/how-to-specify-the-binary-to-start).  
  
Para generar perfiles de binarios, como los archivos DLL, debe escribir información en el cuadro de diálogo **\<Destino > Páginas de propiedades**. Esta información indica dónde puede encontrar el proyecto DLL la aplicación que realiza la llamada.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-executable-to-start"></a>Para especificar el archivo ejecutable para iniciar  
  
1.  En el **Explorador de rendimiento**, haga clic con el botón derecho en el binario de destino y después haga clic en **Propiedades**.  
  
2.  En el cuadro de diálogo **Páginas de propiedades**, haga clic en las propiedades **Iniciar**.  
  
3.  Seleccione la casilla **Invalidar propiedades del proyecto**.  
  
4.  En el cuadro de texto **Ejecutable para iniciar**, especifique la ubicación del archivo.  
  
5.  En el cuadro de texto **Argumentos**, especifique los argumentos necesarios para iniciar la aplicación.  
  
6.  En el cuadro de texto **Directorio de trabajo**, especifique la ubicación del directorio.  
  
7.  Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)



