---
title: Procedimiento Activación y desactivación de la pluralización (Object Relational Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 3aeddaa1b3589857124e4658c758a52def896acd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983578"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Procedimiento Activación y desactivación de la pluralización (Object Relational Designer)
De forma predeterminada, al arrastrar objetos de base de datos con nombres que terminan en s o es desde **Explorador de servidores** o **Database Explorer** hasta la [de LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), el nombres de las clases de entidad generadas cambian de plural a singular. Este cambio se produce para representar con mayor precisión la asignación de la clase de entidad con instancias a un solo registro de datos. Por ejemplo, agregando un `Customers` la tabla a la **Object Relational Designer** da como resultado una clase de entidad denominada `Customer` porque la clase contendrá datos para un solo cliente.

> [!NOTE]
>  La pluralización está activada de forma predeterminada solamente en la versión en inglés de Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Para activar y desactivar la pluralización

1.  En el menú **Herramientas** , haga clic en **Opciones**.

2.  En el cuadro de diálogo **Opciones**, expanda **Herramientas para bases de datos**.

    > [!NOTE]
    >  Seleccione **Mostrar todas las configuraciones** si el nodo **Herramientas para bases de datos** no está visible.

3.  Haga clic en **Object Relational Designer**.

4.  Establecer **Pluralización de nombres** a **habilitado** = **False** para establecer el **Object Relational Designer** para que no cambia los nombres de clase .

5.  Establecer **Pluralización de nombres** a **habilitado** = **True** para aplicar las reglas de pluralización a los nombres de clase de los objetos agregados a la **Relational Diseñador**.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)