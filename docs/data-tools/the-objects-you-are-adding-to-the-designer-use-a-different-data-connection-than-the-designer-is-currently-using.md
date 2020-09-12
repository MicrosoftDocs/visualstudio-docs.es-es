---
title: Los objetos usan una conexión diferente
description: Los objetos agregados al diseñador usan una conexión de datos diferente
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5b2ae4975f2848379403a0df1258640c32ccd58f
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036228"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Los objetos que va a agregar al diseñador usan una conexión de datos diferente que el diseñador

Los objetos que va a agregar al diseñador usan una conexión de datos diferente a la que está usando el diseñador. ¿Desea reemplazar la conexión que usa el diseñador?

Al agregar elementos al **Object Relational Designer** (Object Relational**Designer**), todos los elementos usan una conexión de datos compartida. (La superficie de diseño representa la <xref:System.Data.Linq.DataContext> , que usa una sola conexión para todos los objetos de la superficie). Si agrega un objeto al diseñador que usa una conexión de datos que difiere de la conexión de datos utilizada actualmente por el diseñador, aparece este mensaje. Para resolver este error, puede optar por mantener la conexión existente. Si elige esta opción, no se agregará el objeto seleccionado. Asimismo, puede optar por agregar el objeto y restablecer la conexión de <xref:System.Data.Linq.DataContext> en la nueva conexión.

## <a name="connection-options"></a>Opciones de conexión

- Para reemplazar la conexión existente con la conexión usada por el objeto seleccionado, haga clic en **sí**.

   El objeto seleccionado se agrega a Object **Relational Designer**y el *DataContext. Connection* se establece en la nueva conexión.

   > [!NOTE]
   > Si hace clic en **sí**, todas las clases de entidad de Object Relational **Designer** se asignan a la nueva conexión.

- Para seguir usando la conexión existente y cancelar la adición del objeto seleccionado, haga clic en **no**.

   Se cancela la acción. *DataContext. Connection* permanece establecido en la conexión existente.

## <a name="see-also"></a>Consulte también

- [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
