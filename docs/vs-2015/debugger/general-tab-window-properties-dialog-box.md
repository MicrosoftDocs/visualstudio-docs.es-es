---
title: Pestaña General (Cuadro de diálogo Propiedades de la ventana) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b8733ef63a60baa1b268c42c8780cdf80f2674b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159960"
---
# <a name="general-tab-window-properties-dialog-box"></a>Pestaña General (Cuadro de diálogo Propiedades de la ventana)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use la pestaña **General** para mostrar información sobre la ventana seleccionada. Para mostrar el [cuadro de diálogo Propiedades de la ventana](../debugger/window-properties-dialog-box.md), mueva el foco a la ventana [Vista Ventanas](../debugger/windows-view.md). Seleccione un nodo de ventana en el árbol y, después, elija **Propiedades** en el menú **Vista**.  
  
 En la pestaña **General** están disponibles los valores siguientes:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Título de ventana**|Texto del título de la ventana o texto incluido en una ventana si es un control.|  
|**Identificador de ventana**|Identificador único de esta ventana. Los números de identificador de ventana se reutilizan; identifican una ventana solo mientras dure esa ventana.|  
|**Proc. de ventana**|Dirección virtual de la función de procedimiento de ventana para esta ventana. Este campo también indica si esta ventana es una ventana Unicode y si está en una subclase.|  
|**Rectángulo**|Rectángulo de delimitación de la ventana. También se muestra el tamaño del rectángulo. Las unidades son píxeles en coordenadas de pantalla.|  
|**Rectángulo restaurado**|Rectángulo de delimitación de la ventana restaurada. También se muestra el tamaño del rectángulo. El rectángulo restaurado se diferenciará del rectángulo solo cuando la ventana esté maximizada o minimizada. Las unidades son píxeles en coordenadas de pantalla.|  
|**Rect. de cliente**|Rectángulo de delimitación del área de cliente de la ventana. También se muestra el tamaño del rectángulo. Las unidades son píxeles en relación con la parte superior izquierda del área de cliente de la ventana.|  
|**Identificador de instancia**|Identificador de instancia de la aplicación. Los identificadores de instancia no son únicos.|  
|**Identificador de control o de menú**|Si la ventana que se muestra es una ventana secundaria, se muestra la etiqueta del identificador de control. El identificador de control es un entero que identifica el identificador de control de la ventana secundaria. Si la ventana que se muestra no es una ventana secundaria, se muestra la etiqueta Identificador de menú. El identificador de menú es un entero que identifica el identificador del menú asociado a esta ventana.|  
|**Datos del usuario**|Datos específicos de la aplicación que están asociados a esta estructura de ventana.|  
|**Bytes de ventana**|Número de bytes adicionales asociados a esta ventana. El significado de estos bytes viene determinado por la aplicación. Expanda el cuadro de lista para ver los valores de bytes en formato DWORD.|
