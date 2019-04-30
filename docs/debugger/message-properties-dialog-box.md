---
title: Cuadro de diálogo Propiedades del mensaje | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options
- message options, General
ms.assetid: 58e9dc24-baf6-4ab8-916c-aea28b72e3b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f590f40e4e3361f4dbeb46a3a9b8758b8ab5075
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846120"
---
# <a name="message-properties-dialog-box"></a>Cuadro de diálogo Propiedades del mensaje
Utilice este cuadro de diálogo para obtener más información acerca de un mensaje concreto. Para mostrar este cuadro de diálogo, mueva el foco a un [vista mensajes](../debugger/messages-view.md) ventana. Seleccione el nodo de un mensaje en el árbol y luego elija **propiedades** desde el **vista** menú.

 El **General** pestaña es la única ficha mostrada. Las siguientes opciones están disponibles:

 **Identificador de ventana** el identificador único de esta ventana. Números de identificador de ventana se reutilizan; identifican una ventana únicamente para la duración de esa ventana. Haga clic en este valor para ver las propiedades de esta ventana.

 **Nivel de anidamiento** profundidad de anidamiento de este mensaje, donde 0 no es anidamiento.

 **Mensaje** número, el estado y el nombre del mensaje de windows seleccionada.

 **lResult** el valor de la *lResult* parámetro, si existe.

 **wParam** el valor de la *wParam* parámetro, si existe.

 **lParam** el valor de la *lParam* parámetro, si existe. Este valor se descodifica si es un puntero a una cadena o una estructura.

## <a name="related-sections"></a>Secciones relacionadas
 [Cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md) utiliza para seleccionar qué mensajes se muestran en la vista activa de mensajes.

 [Cuadro de diálogo de búsqueda del mensaje](../debugger/message-search-dialog-box.md) usa para encontrar el nodo de un mensaje concreto en la vista mensajes.

 [Referencia de Spy ++](../debugger/spy-increment-reference.md) incluye secciones que describen cada Spy ++ menú y cuadro de diálogo.

 [Abrir vista mensajes desde Buscar ventana](../debugger/how-to-open-messages-view-from-find-window.md) se explica cómo abrir la vista mensajes desde el cuadro de diálogo Buscar ventana.

 [Buscar un mensaje en la vista mensajes](../debugger/how-to-search-for-a-message-in-messages-view.md) se explica cómo encontrar un mensaje concreto en la vista mensajes.

 [La vista mensajes](../debugger/messages-view.md) muestra la secuencia de mensaje asociada a una ventana, proceso o subproceso.

 [Vistas de Spy ++](../debugger/spy-increment-views.md) explica las vistas de árbol de Spy ++ de windows, los mensajes, los procesos y subprocesos.

 [Usar Spy ++](../debugger/using-spy-increment.md) presenta la herramienta Spy ++ y explica cómo se puede usar.