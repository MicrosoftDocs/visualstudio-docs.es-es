---
title: "Clase ficha, cuadro de diálogo de propiedades de ventana | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cb10cf8a571d37f27244398e6c957c46cee87f8b
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2018
---
# <a name="class-tab-window-properties-dialog-box"></a>Pestaña Clase (Cuadro de diálogo Propiedades de la ventana)
Use la **clase** ficha para mostrar información sobre la clase de la ventana seleccionada. Para mostrar la [cuadro de diálogo de propiedades de ventana](../debugger/window-properties-dialog-box.md), mover el foco a la [Windows Vista](../debugger/windows-view.md) ventana. Seleccione cualquier nodo de la ventana en el árbol y después elija **propiedades** desde el **vista** menú.  
  
 Las siguientes opciones están disponibles en la **clase** ficha:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Nombre de la clase**|El nombre (o número ordinal) de esta clase de ventana.|  
|**Estilos de clase**|Una combinación de códigos de estilo de clase.|  
|**Bytes de clase**|Datos específicos de aplicación asociados a esta clase de ventana.|  
|**Clase Atom**|El subcomponente de la clase devuelta por la **RegisterClass** llamar.|  
|**Identificador de instancia**|El identificador de instancia del módulo que registró la clase. Los identificadores de instancia no son únicos.|  
|**Bytes de ventana**|El número de bytes adicionales asociados a cada ventana de esta clase. El significado de estos bytes viene determinado por la aplicación. Expanda el cuadro de lista para ver los valores de byte en formato DWORD.|  
|**Proc.**|La dirección actual de la **/ / WndProc** función para las ventanas de esta clase. Esto difiere de **proc.** en el **General** ficha si la ventana es una subclase.|  
|**Nombre del menú**|El nombre del menú principal que está asociado a las ventanas de esta clase ("ninguno", si no hay ningún menú).|  
|**Identificador de icono**|El identificador para el icono que está asociado a las ventanas de esta clase ("ninguno", si no hay ningún icono).|  
|**Identificador del cursor**|El identificador del cursor que está asociado a las ventanas de esta clase ("ninguno", si no hay ningún cursor).|  
|**Pincel de fondo**|El identificador del pincel de fondo que está asociado a las ventanas de esta clase, o uno de los colores COLOR_ * predefinidos para pintar el fondo de la ventana ("ninguno", si no hay ningún pincel).|