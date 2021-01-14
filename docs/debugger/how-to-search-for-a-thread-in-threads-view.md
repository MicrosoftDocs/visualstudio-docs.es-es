---
title: Búsqueda de un subproceso en la vista Subprocesos | Microsoft Docs
description: Para buscar un subproceso específico en la vista Subprocesos de la herramienta Spy++, utilice su id. de subproceso o cadena de módulo como criterios de búsqueda durante la depuración en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92864c9d3c66a7547ef52a2694f6307d57a43304
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148538"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Procedimiento Búsqueda de un subproceso en la vista Subprocesos
Para buscar un subproceso específico en la vista Subprocesos, utilice su id. de subproceso o cadena de módulo como criterios de búsqueda. También puede especificar la dirección inicial de la búsqueda. En los campos del cuadro de diálogo se mostrarán los atributos del subproceso seleccionado en el árbol de subprocesos.

### <a name="to-search-for-a-thread-in-threads-view"></a>Para buscar un subproceso en la vista Subprocesos

1. Organice las ventanas para que se vean la ventana de Spy++ y una ventana activa de la [vista Subprocesos](../debugger/threads-view.md).

2. En el menú **Buscar**, seleccione **Buscar subproceso**.

    Se abrirá el [cuadro de diálogo Buscar subproceso](../debugger/thread-search-dialog-box.md).

3. Escriba el id. de subproceso o una cadena de módulo como criterios de búsqueda.

4. Borre los campos en los que no quiera especificar ningún valor.

   > [!TIP]
   > Para buscar todos los subprocesos que pertenecen a un módulo, desactive el cuadro de texto **Subproceso** y escriba el nombre del módulo en el cuadro **Módulo**. A continuación, use **Buscar siguiente** para seguir buscando subprocesos.

5. Seleccione **Arriba** o **Abajo** para determinar la dirección inicial de la búsqueda.

6. Haga clic en **Aceptar**.

   Si se encuentra un subproceso coincidente, se resaltará en la ventana de la vista Ventanas.