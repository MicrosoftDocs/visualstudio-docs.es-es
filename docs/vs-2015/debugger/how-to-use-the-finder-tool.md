---
title: 'Cómo: usar la herramienta de búsqueda | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 935aab109ef15fc1478ca92bb901cbb353b89cb5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49198762"
---
# <a name="how-to-use-the-finder-tool"></a>Cómo: Usar la herramienta de búsqueda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar la herramienta de búsqueda en el **Buscar ventana** cuadro de diálogo para mostrar la ventana Propiedades o mensajes. La herramienta de búsqueda también puede encontrar ventanas secundarias deshabilitadas y discernir qué ventana resaltar si deshabilita ventanas secundarias se superponen.  
  
 ![Spy&#43; &#43; ventana cuadro de diálogo Buscar](../debugger/media/icon-spy-find.png "Icon_Spy ++ _Find")  
Herramienta de búsqueda en el cuadro de diálogo Buscar ventana  
  
 La ilustración anterior muestra el cuadro de diálogo Buscar ventana después del paso 3 siguiente.  
  
### <a name="to-display-window-properties-or-messages"></a>Para mostrar la ventana Propiedades o mensajes  
  
1.  Organizar las ventanas para que estén visibles Spy ++ y la ventana de destino.  
  
2.  Desde el **Spy** menú, elija **Buscar ventana**.  
  
     El [cuadro de diálogo Buscar ventana](../debugger/find-window-dialog-box.md) se abre.  
  
3.  Arrastre el **herramienta de búsqueda** a través de la ventana de destino.  
  
     A medida que arrastra la herramienta, el **Buscar ventana** cuadro de diálogo muestra los detalles de la ventana seleccionada.  
  
     -O bien-  
  
     Si tiene el identificador de la ventana que desea examinar (por ejemplo, si se copian desde el depurador), escríbalo en el **controlar** cuadro de texto.  
  
    > [!TIP]
    >  Para reducir la confusión en la pantalla, seleccione el **Ocultar Spy** opción. Esta opción oculta la ventana principal de Spy ++, dejando sólo los **Buscar ventana** cuadro de diálogo visible encima de las otras aplicaciones. La ventana principal de Spy ++ se restaura al hacer clic en **Aceptar** o **cancelar**, o cuando se borra el **Ocultar Spy ++** opción.  
  
4.  En **mostrar**, seleccione **propiedades** o **mensajes**.  
  
5.  Presione **Aceptar**.  
  
     Si seleccionó **propiedades**, el [cuadro de diálogo de propiedades de ventana](../debugger/window-properties-dialog-box.md) se abre. Si seleccionó **mensajes**, un [vista mensajes](../debugger/messages-view.md) abre la ventana.  
  
## <a name="see-also"></a>Vea también  
 [Vistas de Spy ++](../debugger/spy-increment-views.md)   
 [Usar Spy ++](../debugger/using-spy-increment.md)   
 [Referencia de Spy++](../debugger/spy-increment-reference.md)



