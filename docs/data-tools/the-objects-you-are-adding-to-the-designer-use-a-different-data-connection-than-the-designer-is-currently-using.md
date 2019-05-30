---
title: Objetos agregados al diseñador usan una conexión de datos diferentes
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c85e0c17eeb4cfbd786faac338c8b908c5a7f363
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260937"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Los objetos que se va a agregar al diseñador usan una conexión de datos diferente que el diseñador

Los objetos que va a agregar al diseñador usan una conexión de datos diferente a la que está usando el diseñador. ¿Desea reemplazar la conexión que usa el diseñador?

Cuando se agregan elementos a la **Object Relational Designer** (**Object Relational Designer**), todos los elementos usan una conexión de datos compartido. (La superficie de diseño representa la clase <xref:System.Data.Linq.DataContext>, que usa una sola conexión para todos los objetos en la superficie.) Si agrega al diseñador un objeto que usa una conexión de datos distinta de la conexión de datos que usa actualmente el diseñador, aparece este mensaje. Para resolver este error, puede optar por mantener la conexión existente. Si elige esta opción, no se agregará el objeto seleccionado. Asimismo, puede optar por agregar el objeto y restablecer la conexión de <xref:System.Data.Linq.DataContext> en la nueva conexión.

## <a name="connection-options"></a>Opciones de conexión

- Para reemplazar la conexión existente con la conexión usada por el objeto seleccionado, haga clic en **Sí**.

   El objeto seleccionado se agrega a la **Object Relational Designer**y el *DataContext.Connection* se establece en la nueva conexión.

   > [!NOTE]
   > Si hace clic en **Sí**, entidad de todas las clases en el **Object Relational Designer** se asignan a la nueva conexión.

- Para seguir usando la conexión existente y Cancelar adición del objeto seleccionado, haga clic en **No**.

   Se cancela la acción. *DataContext.Connection* se mantiene establecido en la conexión existente.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)
