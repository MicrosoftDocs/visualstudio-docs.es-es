---
title: 'Cómo: mostrar información de seguimiento WPF | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a91d9f1f58a6905d50e14351bbbaf6fe732c60f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771245"
---
# <a name="how-to-display-wpf-trace-information"></a>Cómo: Mostrar información de seguimiento de WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] puede recibir información de seguimiento de depuración de aplicaciones WPF y mostrar esa información en el **salida** ventana. Para mostrar información de seguimiento de depuración, debe estar habilitada la traza de WPF.  
  
 Puede habilitar la traza de WPF en su archivo App.Config o, mediante programación, utilizando la clase <xref:System.Diagnostics.PresentationTraceSources>. Es una manera más fácil de habilitar el seguimiento de WPF mediante la **opciones** ventana. No se admite la traza WPF en las aplicaciones web.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>Para habilitar o personalizar la información de seguimiento de WPF  
  
1.  En el menú **Herramientas**, seleccione **Opciones**.  
  
2.  En el **opciones** cuadro de diálogo, en el cuadro de la izquierda, abra el **depuración** nodo.  
  
3.  En **depuración**, haga clic en **ventana de salida**.  
  
4.  En **configuración General de salida**, seleccione **toda la salida de depuración**.  
  
5.  En el cuadro de la derecha, busque **configuración de seguimiento de WPF**.  
  
6.  Abra el **configuración de seguimiento de WPF** nodo.  
  
7.  En **configuración de seguimiento de WPF**, haga clic en la categoría de configuración que desee habilitar (por ejemplo, **enlace de datos**).  
  
     Un control de lista desplegable que aparece junto a en la columna configuración **enlace de datos** o cualquier categoría ha hecho clic.  
  
8.  Haga clic en la lista desplegable y seleccione el tipo de información de seguimiento que desea ver: **todas**, **crítico**, **Error**, **advertencia**,  **Información**, **detallado**, o **ActivityTracing**.  
  
     **Crítica** habilita la traza de sólo eventos críticos.  
  
     **Error** habilita la traza de eventos críticos y de Error.  
  
     **Advertencia** habilita la traza de crítico, Error y eventos de advertencia.  
  
     **Información** habilita la traza de eventos crítico, Error, advertencia e informativos.  
  
     **Detallado** habilita la traza de eventos de Error, crítico, advertencia, información y detallado.  
  
     **ActivityTracing** habilita la traza de eventos Stop, Start, Suspend, transferencia y reanudación.  
  
     Para obtener más información sobre el significado de estos niveles de información de seguimiento, vea <xref:System.Diagnostics.SourceLevels>.  
  
9. Haga clic en **Aceptar**.  
  
### <a name="to-disable-wpf-trace-information"></a>Para deshabilitar la información de seguimiento de WPF  
  
1.  En el menú **Herramientas**, seleccione **Opciones**.  
  
2.  En el **opciones** cuadro de diálogo, en el cuadro de la izquierda, abra el **depuración** nodo.  
  
3.  En **depuración**, haga clic en **ventana de salida**.  
  
4.  En el cuadro de la derecha, busque **configuración de seguimiento de WPF**.  
  
5.  Abra el **configuración de seguimiento de WPF** nodo.  
  
6.  En **configuración de seguimiento de WPF**, haga clic en la categoría de configuración que desee habilitar (por ejemplo, **enlace de datos**).  
  
     Un control de lista desplegable que aparece junto a en la columna configuración **enlace de datos** o cualquier categoría ha hecho clic.  
  
7.  Haga clic en la lista desplegable y seleccione **desactivar**.  
  
8.  Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar WPF](../debugger/debugging-wpf.md)



