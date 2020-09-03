---
title: Este método relacionado es el método de respaldo para los siguientes métodos de inserción, actualización o eliminación predeterminados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 84d27dc6f5081a36a237748c091429cfdabbe841
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667183"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Este método relacionado es el método de copia de seguridad para los siguientes métodos de inserción, actualización o eliminación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este método relacionado es el método de copia de seguridad para los siguientes métodos de inserción, actualización o eliminación. Si se elimina, estos métodos se eliminarán también. ¿Desea continuar?

 El método seleccionado de `DataContext` se usa actualmente como uno de los métodos de inserción, actualización o eliminación para una de las clases de entidad en Object Relational Designer. Al eliminar el método seleccionado, la clase de entidad que usaba este método se revertirá al comportamiento predeterminado en tiempo de ejecución para realizar la inserción, actualización o eliminación durante una actualización.

### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Para eliminar el método seleccionado de modo que la clase de entidad utilizará las actualizaciones en tiempo de ejecución

- Haga clic en **Sí**.

     El método seleccionado se elimina y las clases que usaban este método para invalidar el comportamiento de actualización se revierten al comportamiento predeterminado del motor en tiempo de ejecución LINQ to SQL.

### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Para cerrar el cuadro de mensaje sin cambiar el método seleccionado

- Haga clic en **No**.

     El cuadro de mensaje se cierra y no se realiza ninguna modificación.

## <a name="see-also"></a>Consulte también
 [DataContext (métodos) (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md) [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [LINQ to SQL herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
