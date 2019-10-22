---
title: Procedimiento para activar y desactivar la pluralización (O-R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 578a6333d1206553db50ce81f2f499da0481456d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648341"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Procedimiento para activar y desactivar la pluralización (Object Relational Designer)
De forma predeterminada, al arrastrar objetos de base de datos que tienen nombres que terminan en s o s desde **Explorador de servidores** o **Explorador de bases de datos** en las [herramientas de LINQ to SQL de Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), los nombres de las clases de entidad generadas cambian de plural a particular. Este cambio se produce para representar con mayor precisión la asignación de la clase de entidad con instancias a un solo registro de datos. Por ejemplo, al agregar una tabla `Customers` a **Object Relational Designer** , se obtiene una clase de entidad denominada `Customer` porque la clase almacenará los datos de un solo cliente.

> [!NOTE]
> La pluralización está activada de forma predeterminada solamente en la versión en inglés de Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Para activar y desactivar la pluralización

1. En el menú **Herramientas** , haga clic en **Opciones**.

2. En el cuadro de diálogo **Opciones**, expanda **Herramientas para bases de datos**.

    > [!NOTE]
    > Seleccione **Mostrar todas las configuraciones** si el nodo **Herramientas para bases de datos** no está visible.

3. Haga clic en **Object Relational Designer**.

4. Establezca la **pluralización de nombres** en **habilitado**  = **false** para establecer el Object Relational **Designer** de modo que no cambie los nombres de clase.

5. Establezca la **pluralización de nombres** en **habilitado**  = **true** para aplicar las reglas de pluralización a los nombres de clase de los objetos agregados a Object Relational **Designer**.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)