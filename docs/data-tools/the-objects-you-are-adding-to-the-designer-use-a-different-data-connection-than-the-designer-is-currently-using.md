---
title: Los objetos que va a agregar al diseñador usan una conexión de datos diferente a la que está usando el diseñador
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a2fb26fa8960c652feefa157fb04c31b9ed7abb9
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174200"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Los objetos que se va a agregar al diseñador usan una conexión de datos diferente que el diseñador

Los objetos que va a agregar al diseñador usan una conexión de datos diferente a la que está usando el diseñador. ¿Desea reemplazar la conexión que usa el diseñador?

Cuando se agregan elementos a la **Object Relational Designer** (**Object Relational Designer**), todos los elementos usan una conexión de datos compartido. (La superficie de diseño representa la clase <xref:System.Data.Linq.DataContext>, que usa una sola conexión para todos los objetos en la superficie.) Si agrega al diseñador un objeto que usa una conexión de datos distinta de la conexión de datos que usa actualmente el diseñador, aparece este mensaje. Para resolver este error, puede optar por mantener la conexión existente. Si elige esta opción, no se agregará el objeto seleccionado. Como alternativa, puede agregar el objeto y restablecer el <xref:System.Data.Linq.DataContext> conexión a la nueva conexión.

> [!NOTE]
> Si hace clic en **Sí**, entidad de todas las clases en el **Object Relational Designer** se asignan a la nueva conexión.

## <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Para reemplazar la conexión existente con la conexión que usa el objeto seleccionado

- Haga clic en **Sí**.

    El objeto seleccionado se agrega a la **Object Relational Designer**y el *DataContext.Connection* se establece en la nueva conexión.

## <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Para continuar usando la conexión existente y cancelar la adición del objeto seleccionado

- Haga clic en **No**.

    Se cancela la acción. El *DataContext.Connection* mantiene establecido en la conexión existente.

## <a name="see-also"></a>Vea también

- [Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
