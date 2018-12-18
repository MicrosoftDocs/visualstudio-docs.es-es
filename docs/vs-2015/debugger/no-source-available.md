---
title: Ningún origen disponible | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.nosource
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc8331c710141a2cc2837d97101e9dff2b49785b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798383"
---
# <a name="no-source-available"></a>No hay código fuente disponible
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El proyecto no contiene código fuente para el código que se está intentando ver. La causa habitual es hacer doble clic en un módulo que no tiene código fuente en el **ventana Pila de llamadas** o **ventana subprocesos**. Puede seguir depurando, pero no puede utilizar la ventana de código fuente para establecer puntos de interrupción y realizar otras acciones en dicha ubicación. Si necesita establecer un punto de interrupción, utilice la **ventana Desensamblado** en su lugar.  
  
 En las Páginas de propiedades de la solución, puede cambiar los directorios en los que el depurador busca archivos de código fuente e indicar al depurador que omita los archivos de código fuente seleccionados. Consulte [cuadro de diálogo de páginas de propiedad de origen archivos, propiedades comunes, solución de depuración](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Buscar código fuente**  
 Haga clic en este vínculo para abrir un cuadro de diálogo en el que puede buscar código fuente.  
  
 **Mostrar desensamblado**  
 Inicia el **ventana Desensamblado**.  
  
 **Mostrar siempre el desensamblado de los archivos de origen que faltan**  
 Seleccione esta opción para mostrar el **ventana Desensamblado** automáticamente cuando no está disponible ningún origen. También se puede cambiar esta configuración en el **opciones** cuadro de diálogo, **depuración** categoría, **General** página activando o desactivando **Mostrar desensamblado si origen no está disponible**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar el código fuente, propiedades comunes, los archivos solución Property Pages Dialog Box](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Especificar símbolos (.pdb) y los archivos de origen](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (Extensión de depuración de SOS)](http://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498)



