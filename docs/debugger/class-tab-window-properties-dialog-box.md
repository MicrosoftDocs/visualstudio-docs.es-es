---
title: Pestaña Clase (Cuadro de diálogo Propiedades de la ventana) | Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565018"
---
# <a name="class-tab-window-properties-dialog-box"></a>Pestaña Clase (Cuadro de diálogo Propiedades de la ventana)
Use la pestaña **Clase** para mostrar información sobre la clase de la ventana seleccionada. Para mostrar el [cuadro de diálogo Propiedades de la ventana](../debugger/window-properties-dialog-box.md), mueva el foco a la ventana [Vista Ventanas](../debugger/windows-view.md). Seleccione un nodo de ventana en el árbol y, después, elija **Propiedades** en el menú **Vista**.

 En la pestaña **Clase** están disponibles los valores siguientes:

|Entrada|Descripción|
|-----------|-----------------|
|**Nombre de la clase**|El nombre (o número ordinal) de esta clase de ventana.|
|**Estilos de clase**|Combinación de códigos de estilo de clase.|
|**Bytes de clase**|Datos específicos de la aplicación asociados a esta clase de ventana.|
|**Átomo de clase**|Atom de la clase devuelta por la llamada a **RegisterClass**.|
|**Identificador de instancia**|Identificador de instancia del módulo que registró la clase. Los identificadores de instancia no son únicos.|
|**Bytes de ventana**|Número de bytes adicionales asociados a cada ventana de esta clase. El significado de estos bytes viene determinado por la aplicación. Expanda el cuadro de lista para ver los valores de bytes en formato DWORD.|
|**Proc. de ventana**|Dirección actual de la función **WndProc** para ventanas de esta clase. Es diferente de **Proc. de ventana** en la pestaña **General** si la ventana está en una subclase.|
|**Nombre del menú**|Nombre del menú principal que está asociado con las ventanas de esta clase ("ninguno" si no hay ningún menú).|
|**Identificador de icono**|Identificador del icono que está asociado con las ventanas de esta clase ("ninguno" si no hay ningún icono).|
|**Identificador de cursor**|Identificador del cursor que está asociado con las ventanas de esta clase ("ninguno" si no hay ningún cursor).|
|**Pincel de fondo**|Identificador del pincel de fondo que está asociado a las ventanas de esta clase, o uno de los colores predefinidos COLOR_* predefinidos para pintar el fondo de la ventana ("ninguno" si no hay ningún pincel).|