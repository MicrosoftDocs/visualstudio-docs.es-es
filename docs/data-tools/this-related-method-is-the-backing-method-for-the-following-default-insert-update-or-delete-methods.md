---
title: Este método relacionado es el método de copia de seguridad para los siguientes métodos de inserción, actualización o eliminación
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 1b5579c8916e81e3c49e9d6e24bf37ed85039c03
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851828"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Este método relacionado es el método de copia de seguridad para los siguientes métodos de inserción, actualización o eliminación

Este método relacionado es el método de copia de seguridad predeterminado para el siguiente `Insert`, `Update`, o `Delete` métodos. Si se elimina, estos métodos se eliminarán también. ¿Desea continuar?

Seleccionado `DataContext` método se utiliza actualmente como uno de los `Insert`, `Update`, o `Delete` métodos para una de las clases de entidad en el **Object Relational Designer**. La clase de entidad que estaba utilizando este método para revertir al comportamiento de tiempo de ejecución predeterminado para realizar la inserción, eliminación de las causas del método seleccionado actualizar o eliminar durante una actualización.

## <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Para eliminar el método seleccionado de modo que la clase de entidad utilizará las actualizaciones en tiempo de ejecución

- Haga clic en **Sí**.

    El método seleccionado se elimina y las clases que usaban este método para invalidar el comportamiento de actualización se revierten al comportamiento predeterminado del motor en tiempo de ejecución LINQ to SQL.

## <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Para cerrar el cuadro de mensaje sin cambiar el método seleccionado

- Haga clic en **No**.

    El cuadro de mensaje se cierra y no se realiza ninguna modificación.

## <a name="see-also"></a>Vea también

- [Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)