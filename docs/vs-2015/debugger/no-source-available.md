---
title: Ningún origen disponible | Documentos de Microsoft
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
ms.openlocfilehash: 9652073b6e5ea58b8206b195f3a99769a1b63a91
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995100"
---
# <a name="no-source-available"></a>No hay código fuente disponible
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El proyecto no contiene código fuente para el código que se está intentando ver. El motivo habitual es hacer doble clic en un módulo que no tiene código fuente en la **Ventana Pila de llamadas** o en la **Ventana Subprocesos**. Puede seguir depurando, pero no puede utilizar la ventana de código fuente para establecer puntos de interrupción y realizar otras acciones en dicha ubicación. Si necesita establecer un punto de interrupción, utilice la **Ventana Desensamblado** en su lugar.  
  
 En las Páginas de propiedades de la solución, puede cambiar los directorios en los que el depurador busca archivos de código fuente e indicar al depurador que omita los archivos de código fuente seleccionados. Consulte [cuadro de diálogo de páginas de propiedad de origen archivos, propiedades comunes, solución de depuración](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Buscar código fuente**  
 Haga clic en este vínculo para abrir un cuadro de diálogo en el que puede buscar código fuente.  
  
 **Mostrar desensamblado**  
 Inicia la **Ventana Desensamblado**.  
  
 **Mostrar siempre el desensamblado de los archivos de código fuente que falten**  
 Seleccione esta opción para que aparezca automáticamente la **Ventana Desensamblado** cuando no haya disponible ningún código fuente. Esta configuración también se puede cambiar en el cuadro de diálogo **Opciones**, categoría **Depuración**, página **General**. Para ello active o desactive **Mostrar desensamblado si el código fuente no está disponible**.  
  
## <a name="see-also"></a>Vea también  
 [Cuadro de diálogo Depurar archivos de código fuente, Propiedades comunes, Páginas de propiedades de solución](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Especificación de archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (Extensión de depuración de SOS)](http://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498)
