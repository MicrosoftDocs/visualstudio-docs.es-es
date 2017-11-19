---
title: "Ningún origen disponible | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e02c91f5e5a55e82633d89aa7209321126271e8e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="no-source-available"></a>No hay código fuente disponible
El proyecto no contiene código fuente para el código que se está intentando ver. La causa habitual es hacer doble clic en un módulo que no tiene código fuente en el **ventana Pila de llamadas** o **ventana subprocesos**. Puede seguir depurando, pero no puede utilizar la ventana de código fuente para establecer puntos de interrupción y realizar otras acciones en dicha ubicación. Si necesita establecer un punto de interrupción, utilice la **ventana Desensamblado** en su lugar.  
  
 En las Páginas de propiedades de la solución, puede cambiar los directorios en los que el depurador busca archivos de código fuente e indicar al depurador que omita los archivos de código fuente seleccionados. Vea [depurar el cuadro de diálogo de páginas de propiedades de origen archivos, propiedades comunes, solución](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Buscar código fuente**  
 Haga clic en este vínculo para abrir un cuadro de diálogo en el que puede buscar código fuente.  
  
 **Mostrar desensamblado**  
 Inicia la **ventana Desensamblado**.  
  
 **Mostrar siempre el desensamblado disponibles para los archivos de origen que faltan**  
 Seleccione esta opción para mostrar el **ventana Desensamblado** automáticamente cuando el origen no está disponible. Esta configuración también pueden cambiarse en el **opciones** cuadro de diálogo, **depuración** categoría, **General** página activando o desactivando **Mostrar desensamblado si origen no está disponible**.  
  
## <a name="see-also"></a>Vea también  
 [Cuadro de diálogo de páginas de propiedades de origen archivos, propiedades comunes, solución de depuración](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Especificar los símbolos (.pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (Extensión de depuración de SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)