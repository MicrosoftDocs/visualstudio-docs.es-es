---
title: Este método relacionado es el método de copia de seguridad para los siguientes métodos de inserción, actualización o eliminación
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 60634bb2cdc0cf85bfaee441a3fb3d3eb55b3159
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281284"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Este método relacionado es el método de copia de seguridad para los siguientes métodos de inserción, actualización o eliminación

Este método relacionado es el método de respaldo para los siguientes `Insert` métodos, o predeterminados `Update` `Delete` . Si se elimina, estos métodos se eliminarán también. ¿Desea continuar?

El `DataContext` método seleccionado se usa actualmente como uno de los `Insert` `Update` métodos, o `Delete` para una de las clases de entidad en **Object**Relational Designer. Al eliminar el método seleccionado, la clase de entidad que estaba utilizando este método se revierte al comportamiento predeterminado en tiempo de ejecución para realizar la inserción, actualización o eliminación durante una actualización.

## <a name="selected-method-options"></a>Opciones del método seleccionado

- Para eliminar el método seleccionado, haciendo que la clase de entidad use las actualizaciones en tiempo de ejecución, haga clic en **sí**.

   El método seleccionado se elimina y las clases que usaban este método para invalidar el comportamiento de la actualización se revierten a usar el comportamiento predeterminado en tiempo de ejecución LINQ to SQL.

- Para cerrar el cuadro de mensaje y dejar el método seleccionado sin cambios, haga clic en **no**.

   El cuadro de mensaje se cierra y no se realiza ninguna modificación.

## <a name="see-also"></a>Vea también

- [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)