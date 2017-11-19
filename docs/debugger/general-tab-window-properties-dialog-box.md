---
title: "General (ficha), cuadro de diálogo de propiedades de ventana | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b26896ce119e49ec2d001a0b09bc7b563bd7cac
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="general-tab-window-properties-dialog-box"></a>Pestaña General (Cuadro de diálogo Propiedades de la ventana)
Use la **General** ficha para mostrar información sobre la ventana seleccionada. Para mostrar la [cuadro de diálogo de propiedades de ventana](../debugger/window-properties-dialog-box.md), mover el foco a la [Windows Vista](../debugger/windows-view.md) ventana. Seleccione cualquier nodo de la ventana en el árbol y después elija **propiedades** desde el **vista** menú.  
  
 Las siguientes opciones están disponibles en la **General** ficha:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Título de ventana**|El texto del título de ventana, o texto contenido en una ventana si se trata de un control.|  
|**Identificador de ventana**|El identificador único de esta ventana. Números de identificador de ventana se reutilizan; una ventana que identifican solo durante la duración de esa ventana.|  
|**Proc.**|La dirección virtual de la función de procedimiento de ventana para esta ventana. Este campo también indica si esta ventana es una ventana de Unicode y si tiene subclase.|  
|**Rectángulo**|El rectángulo delimitador de la ventana. También se muestra el tamaño del rectángulo. Las unidades son píxeles en coordenadas de pantalla.|  
|**Rectángulo restaurado**|El rectángulo delimitador de la ventana restaurada. También se muestra el tamaño del rectángulo. Restaurada diferirá del rectángulo cuando la ventana está maximizada ni minimizada. Las unidades son píxeles en coordenadas de pantalla.|  
|**Rectángulo de cliente**|El rectángulo delimitador para el área de cliente de la ventana. También se muestra el tamaño del rectángulo. Las unidades son píxeles relativos a la esquina superior izquierda del área de cliente de la ventana.|  
|**Identificador de instancia**|El identificador de instancia de la aplicación. Los identificadores de instancia no son únicos.|  
|**Id. de control o identificador de menú**|Si la ventana que se muestra es una ventana secundaria, se muestra la etiqueta de Id. de Control. Id. de control es un entero que identifica el identificador del control de. esta ventana secundaria Si la ventana mostrada no es una ventana secundaria, se muestra la etiqueta de identificador de menú. Identificador de menú es un entero que identifica el identificador del menú asociado a esta ventana.|  
|**Datos de usuario**|Datos específicos de la aplicación que está asociados a esta estructura de ventana.|  
|**Bytes de ventana**|El número de bytes adicionales asociados a esta ventana. El significado de estos bytes viene determinado por la aplicación. Expanda el cuadro de lista para ver los valores de byte en formato DWORD.|