---
title: 'Cómo: mostrar información de seguimiento WPF | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3584ae0d1dcd0e33bfa08954a2ad376485b6b71e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-display-wpf-trace-information"></a>Cómo: Mostrar información de seguimiento de WPF
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] puede recibir información de seguimiento de depuración de las aplicaciones de WPF y mostrar esa información en el **salida** ventana. Para mostrar información de seguimiento de depuración, debe estar habilitada la traza de WPF.  
  
 Puede habilitar la traza de WPF en su archivo App.Config o, mediante programación, utilizando la clase <xref:System.Diagnostics.PresentationTraceSources>. Es una manera más fácil de habilitar la traza de WPF mediante la **opciones** ventana. No se admite la traza WPF en las aplicaciones web.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>Para habilitar o personalizar la información de seguimiento de WPF  
  
1.  En el menú **Herramientas**, seleccione **Opciones**.  
  
2.  En el **opciones** cuadro de diálogo, en el cuadro de la izquierda, abra el **depuración** nodo.  
  
3.  En **depuración**, haga clic en **resultados (ventana)**.  
  
4.  En **configuración General de salida**, seleccione **todos salida de depuración**.  
  
5.  En el cuadro de la derecha, busque **configuración de seguimiento de WPF**.  
  
6.  Abra la **configuración de seguimiento de WPF** nodo.  
  
7.  En **configuración de seguimiento de WPF**, haga clic en la categoría de configuración que desea habilitar (por ejemplo, **enlace de datos**).  
  
     Un control de lista desplegable que aparece junto a en la columna configuración **enlace de datos** o cualquier categoría que hizo clic.  
  
8.  Haga clic en la lista desplegable y seleccione el tipo de información de seguimiento que desea ver: **todos los**, **crítico**, **Error**, **advertencia**,  **Información**, **detallado**, o **ActivityTracing**.  
  
     **Crítico** habilita la traza de sólo eventos críticos.  
  
     **Error** habilita la traza de eventos críticos y de Error.  
  
     **Advertencia** habilita la traza de críticos, de Error y eventos de advertencia.  
  
     **Información** habilita la traza de eventos crítico, Error, advertencia e informativos.  
  
     **Detallado** habilita la traza de eventos crítico, Error, advertencia, información y detallado.  
  
     **ActivityTracing** habilita la traza de eventos de detención, inicio, suspensión, transferencia y reanudar.  
  
     Para obtener más información sobre el significado de estos niveles de información de seguimiento, vea <xref:System.Diagnostics.SourceLevels>.  
  
9. Haga clic en **Aceptar**.  
  
### <a name="to-disable-wpf-trace-information"></a>Para deshabilitar la información de seguimiento de WPF  
  
1.  En el menú **Herramientas**, seleccione **Opciones**.  
  
2.  En el **opciones** cuadro de diálogo, en el cuadro de la izquierda, abra el **depuración** nodo.  
  
3.  En **depuración**, haga clic en **resultados (ventana)**.  
  
4.  En el cuadro de la derecha, busque **configuración de seguimiento de WPF**.  
  
5.  Abra la **configuración de seguimiento de WPF** nodo.  
  
6.  En **configuración de seguimiento de WPF**, haga clic en la categoría de configuración que desea habilitar (por ejemplo, **enlace de datos**).  
  
     Un control de lista desplegable que aparece junto a en la columna configuración **enlace de datos** o cualquier categoría que hizo clic.  
  
7.  Haga clic en la lista desplegable y seleccione **desactivar**.  
  
8.  Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar WPF](../debugger/debugging-wpf.md)