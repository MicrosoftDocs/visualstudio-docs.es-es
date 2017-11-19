---
title: "Pestaña ventanas, cuadro de diálogo de propiedades de ventana | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Window Properties dialog box, Windows Tab
ms.assetid: 9001342a-09a8-4f5e-b6ed-881a3b9d7246
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a49ec9b52d2eaf6dc336ed28d5b4e531bb3b25cf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="windows-tab-window-properties-dialog-box"></a>Pestaña Ventanas (Cuadro de diálogo Propiedades de la ventana)
Use la **Windows** ficha para mostrar información sobre windows relacionada con la ventana seleccionada. Para mostrar la [cuadro de diálogo de propiedades de ventana](../debugger/window-properties-dialog-box.md), mover el foco a la [Windows Vista](../debugger/windows-view.md) ventana. Seleccione cualquier nodo de la ventana en el árbol y después elija **propiedades** desde el **vista** menú.  
  
 Las siguientes opciones están disponibles en la **Windows** ficha:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Ventana siguiente**|El identificador de la siguiente ventana de mismo nivel en la misma secuencia (orden Z) que se muestra en la vista de árbol de ventanas ("ninguno", si no hay ninguna ventana siguiente). Elija esta entrada para ver las propiedades de la siguiente ventana.|  
|**Ventana anterior**|El identificador de la ventana anterior del mismo nivel en la misma secuencia (orden Z) que se muestra en la vista de árbol de ventanas ("ninguno", si no hay ninguna ventana anterior). Elija esta entrada para ver las propiedades de la ventana anterior.|  
|**Ventana primaria**|El identificador de ventana primaria de esta ventana ("ninguno", si no hay ningún elemento primario). Elija esta entrada para ver las propiedades de la ventana primaria.|  
|**Primer elemento secundario**|El identificador de primera ventana secundaria esta ventana, en la secuencia (orden Z) se muestra en la vista de árbol de ventanas ("ninguno", si no hay ningún ventanas secundarias). Elija este valor para ver las propiedades de la primera ventana secundaria.|  
|**Ventana propietaria**|El identificador de ventana propietaria de esta ventana. Ventana principal de una aplicación suele ser propietaria de las ventanas de diálogo modal del sistema, por ejemplo ("ninguno", si no hay ningún propietario). Elija esta entrada para ver las propiedades de la ventana propietaria.|