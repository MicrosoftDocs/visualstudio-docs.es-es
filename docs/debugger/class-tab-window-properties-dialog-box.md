---
title: Clase de ficha, cuadro de diálogo de propiedades de ventana | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0917c9a038b42e6302ec1f1782f095ca397a92ef
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628356"
---
# <a name="class-tab-window-properties-dialog-box"></a>Pestaña Clase (Cuadro de diálogo Propiedades de la ventana)
Use la **clase** ficha para mostrar información sobre la clase de la ventana seleccionada. Para mostrar el [ventana cuadro de diálogo de propiedades](../debugger/window-properties-dialog-box.md), mover el foco a la [Windows Vista](../debugger/windows-view.md) ventana. Seleccione el nodo de una ventana en el árbol y luego elija **propiedades** desde el **vista** menú.

 Las siguientes opciones están disponibles en el **clase** pestaña:

|Entrada|Descripción|
|-----------|-----------------|
|**Nombre de la clase**|El nombre (o número ordinal) de esta clase de ventana.|
|**Estilos de clase**|Una combinación de códigos de estilo de clase.|
|**Bytes de clase**|Datos de específicos de la aplicación asociados con esta clase de ventana.|
|**Átomo de clase**|El subcomponente de la clase devuelta por la **RegisterClass** llamar.|
|**Identificador de instancia**|El identificador de instancia del módulo que registró la clase. Los identificadores de instancia no son únicos.|
|**Bytes de ventana**|El número de bytes adicionales asociados a cada ventana de esta clase. El significado de estos bytes viene determinado por la aplicación. Expanda el cuadro de lista para ver los valores de bytes en formato DWORD.|
|**Proc. de ventana**|La dirección actual de la **WndProc** función para las ventanas de esta clase. Esto difiere de **proc. de ventana** en el **General** pestaña si la ventana es una subclase.|
|**Nombre del menú**|El nombre del menú principal que está asociado a las ventanas de esta clase ("none" Si no hay ningún menú).|
|**Identificador de icono**|El identificador del icono que está asociado a las ventanas de esta clase ("none" Si no hay ningún icono).|
|**Identificador de cursor**|El identificador del cursor que está asociado a las ventanas de esta clase ("none" Si no hay ningún cursor).|
|**Pincel de fondo**|El identificador del pincel de fondo que está asociado a las ventanas de esta clase, o uno de los colores COLOR_ * predefinidos para pintar el fondo de ventana ("none" Si no hay ningún pincel).|