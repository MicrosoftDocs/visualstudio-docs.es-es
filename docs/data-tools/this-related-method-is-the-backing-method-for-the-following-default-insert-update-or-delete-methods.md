---
title: Esto relacionado con el método es el método auxiliar siguiente inserción, actualización o eliminación métodos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 89421c61e34bf4ed98bcb8c2c8bd6ef93e1dae0b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Este método relacionado es el método de copia de seguridad para los siguientes métodos de inserción, actualización o eliminación
Este método relacionado es el método de copia de seguridad para los siguientes métodos de inserción, actualización o eliminación. Si se elimina, estos métodos se eliminarán también. ¿Desea continuar?  
  
 El método seleccionado de `DataContext` se usa actualmente como uno de los métodos de inserción, actualización o eliminación para una de las clases de entidad en Object Relational Designer. Al eliminar el método seleccionado, la clase de entidad que usaba este método se revertirá al comportamiento predeterminado en tiempo de ejecución para realizar la inserción, actualización o eliminación durante una actualización.  
  
### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Para eliminar el método seleccionado de modo que la clase de entidad utilizará las actualizaciones en tiempo de ejecución  
  
-   Haga clic en **Sí**.  
  
     El método seleccionado se elimina y las clases que usaban este método para invalidar el comportamiento de actualización se revierten al comportamiento predeterminado del motor en tiempo de ejecución LINQ to SQL.  
  
### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Para cerrar el cuadro de mensaje sin cambiar el método seleccionado  
  
-   Haga clic en **No**.  
  
     El cuadro de mensaje se cierra y no se realiza ninguna modificación.  
  
## <a name="see-also"></a>Vea también
[Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL de las herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)