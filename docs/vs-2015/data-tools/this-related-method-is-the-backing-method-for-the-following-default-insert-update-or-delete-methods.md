---
title: Este método relacionado es el método de copia de seguridad para la siguiente inserción, actualización o métodos delete | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9f487bab485d11446d8e3f920d04c35a64591771
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575257"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Este método relacionado es el método de copia de seguridad para los siguientes métodos de inserción, actualización o eliminación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [este método relacionado es el método de copia de seguridad para la siguiente inserción, actualización o métodos de eliminación](https://docs.microsoft.com/visualstudio/data-tools/this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods).  
  
  
Este método relacionado es el método de copia de seguridad para los siguientes métodos de inserción, actualización o eliminación. Si se elimina, estos métodos se eliminarán también. ¿Desea continuar?  
  
 El método seleccionado de `DataContext` se usa actualmente como uno de los métodos de inserción, actualización o eliminación para una de las clases de entidad en Object Relational Designer. Al eliminar el método seleccionado, la clase de entidad que usaba este método se revertirá al comportamiento predeterminado en tiempo de ejecución para realizar la inserción, actualización o eliminación durante una actualización.  
  
### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Para eliminar el método seleccionado de modo que la clase de entidad utilizará las actualizaciones en tiempo de ejecución  
  
-   Haga clic en **Sí**.  
  
     El método seleccionado se elimina y las clases que usaban este método para invalidar el comportamiento de actualización se revierten al comportamiento predeterminado del motor en tiempo de ejecución LINQ to SQL.  
  
### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Para cerrar el cuadro de mensaje sin cambiar el método seleccionado  
  
-   Haga clic en **No**.  
  
     El cuadro de mensaje se cierra y no se realiza ninguna modificación.  
  
## <a name="see-also"></a>Vea también  
 [Métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

