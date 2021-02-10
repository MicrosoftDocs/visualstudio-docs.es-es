---
title: Pestaña Ventanas (Cuadro de diálogo Propiedades de la ventana) | Microsoft Docs
description: Use la pestaña Ventanas de Propiedades de Windows para ver información sobre las ventanas que están relacionadas con la ventana seleccionada. Consulte este artículo para conocer la configuración.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Windows Tab
ms.assetid: 9001342a-09a8-4f5e-b6ed-881a3b9d7246
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffc7f8a80e86779f2cc419f841a3b80280f39c9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896408"
---
# <a name="windows-tab-window-properties-dialog-box"></a>Pestaña Ventanas (Cuadro de diálogo Propiedades de la ventana)
Use la pestaña **Ventanas** para ver información sobre las ventanas relacionadas con la ventana seleccionada. Para ver el [Cuadro de diálogo Propiedades de la ventana](../debugger/window-properties-dialog-box.md), mueva el foco a la ventana [Vista Ventanas](../debugger/windows-view.md). Seleccione un nodo de ventana en el árbol y, después, elija **Propiedades** en el menú **Vista**.

 En la pestaña **Ventanas** encontrarás las opciones de configuración siguientes:

|Entrada|Descripción|
|-----------|-----------------|
|**Ventana siguiente**|El manipulador de la siguiente ventana del mismo nivel en la misma secuencia (orden Z) que se muestra en la vista de árbol de la ventana ("none" si no hay ninguna ventana siguiente). Elija esta entrada para ver las propiedades de la ventana siguiente.|
|**Ventana anterior**|El manipulador de la ventana anterior del mismo nivel en la misma secuencia (orden Z) que se muestra en la vista de árbol de la ventana ("none" si no hay ninguna ventana anterior). Elija esta entrada para ver las propiedades de la ventana anterior.|
|**Ventana primaria**|El manipulador de la ventana primaria de esta ventana ("none" si no hay ninguna ventana primaria). Elija esta entrada para ver las propiedades de la ventana primaria.|
|**Primer elemento secundario**|El manipulador de la ventana secundaria de eta ventana en la secuencia (orden Z) que se muestra en la vista de árbol de la ventana ("none" si no hay ninguna ventana secundaria). Elija este valor para ver las propiedades de la primera ventana secundaria.|
|**Ventana propietaria**|El manipulador de la ventana propietaria de esta ventana. Normalmente, la ventana principal de una aplicación es propietaria de las ventanas System Modal, por ejemplo ("none" si no hay ninguna ventana propietaria). Elija esta entrada para ver las propiedades de la ventana propietaria.|