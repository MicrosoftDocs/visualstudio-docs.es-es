---
title: Ficha general, cuadro de diálogo de propiedades de ventana | Documentos de Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998994"
---
# <a name="general-tab-window-properties-dialog-box"></a>Pestaña General (Cuadro de diálogo Propiedades de la ventana)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use la **General** ficha para mostrar información sobre la ventana seleccionada. Para mostrar el [ventana cuadro de diálogo de propiedades](../debugger/window-properties-dialog-box.md), mover el foco a la [Windows Vista](../debugger/windows-view.md) ventana. Seleccione el nodo de una ventana en el árbol y luego elija **propiedades** desde el **vista** menú.  
  
 Las siguientes opciones están disponibles en el **General** pestaña:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Título de ventana**|El texto del título de ventana o texto contenido en una ventana, si es un control.|  
|**Identificador de ventana**|El identificador único de esta ventana. Números de identificador de ventana se reutilizan; identifican una ventana únicamente para la duración de esa ventana.|  
|**Proc. de ventana**|La dirección virtual de la función de procedimiento de ventana para esta ventana. Este campo también indica si esta ventana es una ventana de Unicode y si tiene subclase.|  
|**Rectángulo**|El rectángulo delimitador de la ventana. También se muestra el tamaño del rectángulo. Las unidades son píxeles en coordenadas de pantalla.|  
|**Rectángulo restaurado**|El rectángulo delimitador de la ventana restaurada. También se muestra el tamaño del rectángulo. Rectángulo restaurado se diferencia del rectángulo sólo cuando la ventana está maximizada o minimizada. Las unidades son píxeles en coordenadas de pantalla.|  
|**Rect. de cliente**|El rectángulo delimitador del área de cliente de la ventana. También se muestra el tamaño del rectángulo. Las unidades son píxeles relativos a la esquina superior izquierda del área de cliente de la ventana.|  
|**Identificador de instancia**|El identificador de instancia de la aplicación. Los identificadores de instancia no son únicos.|  
|**Id. de control o identificador de menú**|Si la ventana que se muestra es una ventana secundaria, se muestra la etiqueta de Id. de Control. Id. de control es un entero que identifica el identificador de control de. esta ventana secundaria Si la ventana mostrada no es una ventana secundaria, se muestra la etiqueta de identificador de menú. Identificador de menú es un entero que identifica el identificador del menú asociado a esta ventana.|  
|**Datos del usuario**|Datos específicos de la aplicación que está asociados a esta estructura de la ventana.|  
|**Bytes de ventana**|El número de bytes adicionales asociados a esta ventana. El significado de estos bytes viene determinado por la aplicación. Expanda el cuadro de lista para ver los valores de bytes en formato DWORD.|
