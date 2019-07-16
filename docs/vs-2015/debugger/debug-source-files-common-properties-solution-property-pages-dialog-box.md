---
title: Cuadro de diálogo de páginas de propiedad de origen archivos, propiedades comunes, solución de depuración | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 47fb2511e39153753a2c27483dd6ac96c26c9e83
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143030"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Depurar archivos de código fuente, Propiedades comunes, Páginas de propiedades de Solución (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta página de propiedades especifica si el depurador buscará archivos de código fuente al depurar la solución.  
  
 Para obtener acceso a la página de propiedades **Depurar archivos de código fuente**, en el **Explorador de soluciones**, haga clic con el botón derecho en la Solución y, a continuación, seleccione **Propiedades** en el menú contextual. Expanda la carpeta **Propiedades comunes** y haga clic en la página **Depurar archivos de código fuente**.  
  
 **Directorios que contienen código fuente**  
 Contiene una lista de directorios en los que el depurador busca archivos de código fuente al depurar la solución. Los subdirectorios de los directorios especificados también se incluyen en la búsqueda.  
  
 **No busque los siguientes archivos de código fuente**  
 Especifique los nombres de los archivos que no desea que lea el depurador. Si el depurador encuentra uno de estos archivos en uno de los directorios especificados anteriormente, lo omitirá. Si aparece el cuadro de diálogo **Buscar código fuente** mientras está depurando y hace clic en **Cancelar**, el archivo que buscaba se agregará a dicha lista y el depurador no seguirá buscándolo.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)
