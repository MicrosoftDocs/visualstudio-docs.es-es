---
title: Procedimiento Buscar un proceso en la vista procesos | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a6b57226b14963759bb4d78afff3beb5559a63e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2019
ms.locfileid: "64798981"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Procedimiento Búsqueda de un proceso en la vista Procesos
Puede buscar un proceso específico en la vista procesos mediante el uso de su cadena de identificador o el módulo de proceso como criterios de búsqueda. También puede especificar la dirección inicial de la búsqueda. Los campos en el cuadro de diálogo mostrará los atributos del proceso seleccionado en el árbol de procesos.

### <a name="to-search-for-a-process-in-processes-view"></a>Para buscar un proceso en la vista procesos

1. Organizar las ventanas por lo que ese Spy ++ y un activo [vista procesos](../debugger/processes-view.md) ventana están visibles.

2. Desde el **búsqueda** menú, elija **Buscar proceso**

    El [cuadro de diálogo Buscar proceso](../debugger/process-search-dialog-box.md) se abre.

3. Escriba el identificador de proceso o una cadena de módulo como criterios de búsqueda.

4. Borrar todos los campos que no desea especificar los valores.

   > [!TIP]
   > Para buscar todos los procesos que pertenecen a un módulo, desactive la **proceso** cuadro y escriba el nombre del módulo en el **módulo** cuadro. A continuación, usar **Buscar siguiente** para continuar la búsqueda de procesos.

5. Elija **seguridad** o **abajo** para la dirección inicial de la búsqueda.

6. Haga clic en **OK**.

   Si se encuentra un proceso coincidente, se resalta en el **vista proceso** ventana.