---
title: Ningún origen disponible | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85d1d1307a119fa23bf7ba015130ab9c7b6f69d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905224"
---
# <a name="no-source-available"></a>No hay código fuente disponible
El proyecto no contiene código fuente para el código que se está intentando ver. El motivo habitual es hacer doble clic en un módulo que no tiene código fuente en la **Ventana Pila de llamadas** o en la **Ventana Subprocesos**. Puede seguir depurando, pero no puede utilizar la ventana de código fuente para establecer puntos de interrupción y realizar otras acciones en dicha ubicación. Si necesita establecer un punto de interrupción, utilice la **Ventana Desensamblado** en su lugar.

 En las Páginas de propiedades de la solución, puede cambiar los directorios en los que el depurador busca archivos de código fuente e indicar al depurador que omita los archivos de código fuente seleccionados. Consulte [cuadro de diálogo de páginas de propiedad de origen archivos, propiedades comunes, solución de depuración](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).

 **Busque el código fuente** haga clic en este vínculo para abrir un cuadro de diálogo donde puede examinar para buscar el código fuente.

 **Mostrar desensamblado** inicia el **ventana Desensamblado**.

 **Mostrar siempre el desensamblado de los archivos de origen que faltan** Seleccione esta opción para mostrar el **ventana Desensamblado** automáticamente cuando no está disponible ningún origen. Esta configuración también se puede cambiar en el cuadro de diálogo **Opciones**, categoría **Depuración**, página **General**. Para ello active o desactive **Mostrar desensamblado si el código fuente no está disponible**.

## <a name="see-also"></a>Vea también
- [Depurar archivos de código fuente, Propiedades comunes, Cuadro de diálogo Páginas de propiedades de Solución](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (Extensión de depuración de SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)