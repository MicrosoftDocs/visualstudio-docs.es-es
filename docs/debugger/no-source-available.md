---
title: No hay ningún origen disponible | Microsoft Docs
description: Obtenga información sobre lo que puede hacer cuando su proyecto no tiene código fuente para el código que quiere ver.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e9993c4482d20393a3ca46d9afcd0a8ec1b13f65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942040"
---
# <a name="no-source-available"></a>No hay código fuente disponible
El proyecto no contiene código fuente para el código que se está intentando ver. El motivo habitual es hacer doble clic en un módulo que no tiene código fuente en la **Ventana Pila de llamadas** o en la **Ventana Subprocesos**. Puede seguir depurando, pero no puede utilizar la ventana de código fuente para establecer puntos de interrupción y realizar otras acciones en dicha ubicación. Si necesita establecer un punto de interrupción, utilice la **Ventana Desensamblado** en su lugar.

 En las Páginas de propiedades de la solución, puede cambiar los directorios en los que el depurador busca archivos de código fuente e indicar al depurador que omita los archivos de código fuente seleccionados. Vea [Depurar archivos de código fuente, Propiedades comunes, Páginas de propiedades de Solución](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).

 **Buscar código fuente**: haga clic en este vínculo para abrir un cuadro de diálogo en el que puede buscar código fuente.

 **Mostrar desensamblado**: inicia la **ventana Desensamblado**.

 **Mostrar siempre el desensamblado de los archivos de código fuente que falten**: seleccione esta opción para que aparezca automáticamente la **ventana Desensamblado** cuando no haya disponible ningún código fuente. Esta configuración también se puede cambiar en el cuadro de diálogo **Opciones**, categoría **Depuración**, página **General**. Para ello active o desactive **Mostrar desensamblado si el código fuente no está disponible**.

## <a name="see-also"></a>Vea también
- [Depurar archivos de código fuente, Propiedades comunes, Cuadro de diálogo Páginas de propiedades de Solución](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (Extensión de depuración de SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)