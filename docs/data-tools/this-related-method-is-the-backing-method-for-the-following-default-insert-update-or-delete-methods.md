---
title: Este método relacionado es el método de copia de seguridad para los siguientes métodos de inserción, actualización o eliminación
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a5ae70462079589ba2b63ee50cf0b7a0570e056a
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457841"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Este método relacionado es el método de copia de seguridad para los siguientes métodos de inserción, actualización o eliminación

Este método relacionado es el método de copia de seguridad predeterminado para el siguiente `Insert`, `Update`, o `Delete` métodos. Si se elimina, estos métodos se eliminarán también. ¿Desea continuar?

Seleccionado `DataContext` método se utiliza actualmente como uno de los `Insert`, `Update`, o `Delete` métodos para una de las clases de entidad en el **Object Relational Designer**. La clase de entidad que estaba utilizando este método para revertir al comportamiento de tiempo de ejecución predeterminado para realizar la inserción, eliminación de las causas del método seleccionado actualizar o eliminar durante una actualización.

## <a name="selected-method-options"></a>Opciones del método seleccionado

- Para eliminar el método seleccionado, provocando la clase de entidad usar las actualizaciones en tiempo de ejecución, haga clic en **Sí**.

   El método seleccionado se elimina y las clases que usaban este método para invalidar el comportamiento de actualización se revierten al comportamiento predeterminado del motor en tiempo de ejecución LINQ to SQL.

- Para cerrar el cuadro de mensaje, el método seleccionado sin cambios, haga clic en **No**.

   El cuadro de mensaje se cierra y no se realiza ninguna modificación.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)