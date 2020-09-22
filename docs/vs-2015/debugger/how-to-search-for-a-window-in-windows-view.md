---
title: Procedimiento Búsqueda de una ventana en la vista Ventanas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d9d7a64191db82d5fb0b82518d3db1cf1eb1e0ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843423"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Procedimiento Buscar una ventana en la vista Ventanas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede buscar una ventana específica en la vista Ventanas mediante su identificador, título o clase, o una combinación de su título y clase, como criterios de búsqueda. También puede especificar la dirección inicial de la búsqueda. En los campos del cuadro de diálogo se mostrarán los atributos de la ventana seleccionada en el árbol de ventanas.  
  
 Comience por el árbol expandido al segundo nivel (todas las ventanas que son elementos secundarios del escritorio), para que pueda identificar las ventanas del escritorio por su nombre de clase y título. Una vez que haya elegido una ventana del escritorio, puede expandir ese nivel para buscar una ventana secundaria concreta.  
  
### <a name="to-search-for-a-window-in-windows-view"></a>Para buscar una ventana en la vista Ventanas  
  
1. Organice las ventanas para que se puedan ver las de Spy++, la de la [vista Ventanas](../debugger/windows-view.md) y la de destino.  
  
2. En el menú **Buscar**, seleccione **Buscar ventana**.  
  
     Se abrirá el cuadro de diálogo [Buscar ventana](../debugger/window-search-dialog-box.md).  
  
    > [!TIP]
    > Para reducir el desorden de la pantalla, seleccione la opción **Ocultar Spy**. Esta opción oculta la ventana principal de Spy++ y deja visible únicamente el cuadro de diálogo **Buscar ventana** encima de las otras aplicaciones. La ventana principal de Spy++ se restaura al hacer clic en **Aceptar** o **Cancelar**, o al desactivar la opción **Ocultar Spy++** .  
  
3. Arrastre la **Herramienta de búsqueda** sobre la ventana de destino. Al arrastrar la herramienta, el cuadro de diálogo **Buscar ventana** muestra detalles sobre la ventana seleccionada.  
  
     -O bien-  
  
     Si conoce el identificador de la ventana que le interesa (por ejemplo, del depurador), puede escribirlo en el cuadro **Identificador**.  
  
     -O bien-  
  
     Si conoce el título o la clase de la ventana que le interesa, puede escribirlos en los cuadros de texto **Título** y **Clase**, y desactivar el cuadro de texto **Identificador**.  
  
4. Seleccione **Arriba** o **Abajo** para determinar la dirección inicial de la búsqueda.  
  
5. Haga clic en **Aceptar**.  
  
     Si se encuentra una ventana coincidente, se resaltará en la ventana [vista Ventanas](../debugger/windows-view.md).
