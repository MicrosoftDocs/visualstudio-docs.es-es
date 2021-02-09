---
title: No se puede eliminar el método de respaldo
description: Este método relacionado es el método de copia de seguridad para los siguientes métodos de inserción, actualización o eliminación
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 94e9f1f91aa5c879e0e3ed0034e0d1f554901513
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866377"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Este método relacionado es el método de copia de seguridad para los siguientes métodos de inserción, actualización o eliminación

Este método relacionado es el método de respaldo para los siguientes `Insert` métodos, o predeterminados `Update` `Delete` . Si se elimina, estos métodos se eliminarán también. ¿Desea continuar?

El `DataContext` método seleccionado se usa actualmente como uno de los `Insert` `Update` métodos, o `Delete` para una de las clases de entidad en **Object** Relational Designer. Al eliminar el método seleccionado, la clase de entidad que estaba utilizando este método se revierte al comportamiento predeterminado en tiempo de ejecución para realizar la inserción, actualización o eliminación durante una actualización.

## <a name="selected-method-options"></a>Opciones del método seleccionado

- Para eliminar el método seleccionado, haciendo que la clase de entidad use las actualizaciones en tiempo de ejecución, haga clic en **sí**.

   El método seleccionado se elimina y las clases que usaban este método para invalidar el comportamiento de la actualización se revierten a usar el comportamiento predeterminado en tiempo de ejecución LINQ to SQL.

- Para cerrar el cuadro de mensaje y dejar el método seleccionado sin cambios, haga clic en **no**.

   El cuadro de mensaje se cierra y no se realiza ninguna modificación.

## <a name="see-also"></a>Vea también

- [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)