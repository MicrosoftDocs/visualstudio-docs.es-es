---
title: 'Cómo: buscar un proceso en la vista procesos | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8129516476977e526cde9c3eb3dbe546bdbe3876
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822922"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Cómo: Buscar un proceso en la vista Procesos
Puede buscar un proceso específico en la vista procesos mediante el uso de su cadena de identificador o el módulo de proceso como criterios de búsqueda. También puede especificar la dirección inicial de la búsqueda. Los campos en el cuadro de diálogo mostrará los atributos del proceso seleccionado en el árbol de procesos.  
  
### <a name="to-search-for-a-process-in-processes-view"></a>Para buscar un proceso en la vista procesos  
  
1. Organizar las ventanas por lo que ese Spy ++ y un activo [vista procesos](../debugger/processes-view.md) ventana están visibles.  
  
2. Desde el **búsqueda** menú, elija **Buscar proceso**  
  
    El [cuadro de diálogo Buscar proceso](../debugger/process-search-dialog-box.md) se abre.  
  
3. Escriba el identificador de proceso o una cadena de módulo como criterios de búsqueda.  
  
4. Borrar todos los campos que no desea especificar los valores.  
  
   > [!TIP]
   >  Para buscar todos los procesos que pertenecen a un módulo, desactive la **proceso** cuadro y escriba el nombre del módulo en el **módulo** cuadro. A continuación, usar **Buscar siguiente** para continuar la búsqueda de procesos.  
  
5. Elija **seguridad** o **abajo** para la dirección inicial de la búsqueda.  
  
6. Haga clic en **Aceptar**.  
  
   Si se encuentra un proceso coincidente, se resalta en el **vista proceso** ventana.