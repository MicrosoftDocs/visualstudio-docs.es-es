---
title: General (ficha), cuadro de diálogo de propiedades de ventana | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f762d935edab5720ccd9add155dac3d0e5f2f186
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480129"
---
# <a name="general-tab-window-properties-dialog-box"></a>Pestaña General (Cuadro de diálogo Propiedades de la ventana)
Use la **General** ficha para mostrar información sobre la ventana seleccionada. Para mostrar la [cuadro de diálogo de propiedades de ventana](../debugger/window-properties-dialog-box.md), mover el foco a la [Windows Vista](../debugger/windows-view.md) ventana. Seleccione cualquier nodo de la ventana en el árbol y después elija **propiedades** desde el **vista** menú.  
  
 Las siguientes opciones están disponibles en la **General** ficha:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Título de ventana**|El texto del título de ventana, o texto contenido en una ventana si se trata de un control.|  
|**Identificador de ventana**|El identificador único de esta ventana. Números de identificador de ventana se reutilizan; una ventana que identifican solo durante la duración de esa ventana.|  
|**Proc.**|La dirección virtual de la función de procedimiento de ventana para esta ventana. Este campo también indica si esta ventana es una ventana de Unicode y si tiene subclase.|  
|**rectángulo**|El rectángulo delimitador de la ventana. También se muestra el tamaño del rectángulo. Las unidades son píxeles en coordenadas de pantalla.|  
|**Rectángulo restaurado**|El rectángulo delimitador de la ventana restaurada. También se muestra el tamaño del rectángulo. Restaurada diferirá del rectángulo cuando la ventana está maximizada ni minimizada. Las unidades son píxeles en coordenadas de pantalla.|  
|**Rectángulo de cliente**|El rectángulo delimitador para el área de cliente de la ventana. También se muestra el tamaño del rectángulo. Las unidades son píxeles relativos a la esquina superior izquierda del área de cliente de la ventana.|  
|**Identificador de instancia**|El identificador de instancia de la aplicación. Los identificadores de instancia no son únicos.|  
|**Id. de control o identificador de menú**|Si la ventana que se muestra es una ventana secundaria, se muestra la etiqueta de Id. de Control. Id. de control es un entero que identifica el identificador del control de. esta ventana secundaria Si la ventana mostrada no es una ventana secundaria, se muestra la etiqueta de identificador de menú. Identificador de menú es un entero que identifica el identificador del menú asociado a esta ventana.|  
|**Datos de usuario**|Datos específicos de la aplicación que está asociados a esta estructura de ventana.|  
|**Bytes de ventana**|El número de bytes adicionales asociados a esta ventana. El significado de estos bytes viene determinado por la aplicación. Expanda el cuadro de lista para ver los valores de byte en formato DWORD.|