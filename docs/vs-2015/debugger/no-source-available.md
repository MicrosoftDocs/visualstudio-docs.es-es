---
title: No hay ningún origen disponible | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 69ea9c3a41f83b9c06dc18d6da1f859017f12ca5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697810"
---
# <a name="no-source-available"></a>No hay código fuente disponible
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El proyecto no contiene código fuente para el código que se está intentando ver. El motivo habitual es hacer doble clic en un módulo que no tiene código fuente en la **Ventana Pila de llamadas** o en la **Ventana Subprocesos**. Puede seguir depurando, pero no puede utilizar la ventana de código fuente para establecer puntos de interrupción y realizar otras acciones en dicha ubicación. Si necesita establecer un punto de interrupción, utilice la **Ventana Desensamblado** en su lugar.  
  
 En las Páginas de propiedades de la solución, puede cambiar los directorios en los que el depurador busca archivos de código fuente e indicar al depurador que omita los archivos de código fuente seleccionados. Vea [Depurar archivos de código fuente, Propiedades comunes, Páginas de propiedades de Solución](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Buscar código fuente**  
 Haga clic en este vínculo para abrir un cuadro de diálogo en el que puede buscar código fuente.  
  
 **Mostrar desensamblado**  
 Inicia la **Ventana Desensamblado**.  
  
 **Mostrar siempre el desensamblado de los archivos de código fuente que falten**  
 Seleccione esta opción para que aparezca automáticamente la **Ventana Desensamblado** cuando no haya disponible ningún código fuente. Esta configuración también se puede cambiar en el cuadro de diálogo **Opciones**, categoría **Depuración**, página **General**. Para ello active o desactive **Mostrar desensamblado si el código fuente no está disponible**.  
  
## <a name="see-also"></a>Consulte también  
 [Depurar archivos de código fuente, propiedades comunes, páginas de propiedades de solución (cuadro de diálogo)](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Especificar archivos de código fuente y símbolos (. pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (Extensión de depuración de SOS)](https://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498)
