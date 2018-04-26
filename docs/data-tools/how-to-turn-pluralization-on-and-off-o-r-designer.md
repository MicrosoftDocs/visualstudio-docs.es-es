---
title: 'Cómo: activar y desactivar (Object Relational Designer) la pluralización'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a8c477ac276ce0ff9c292dc42ba2f5f7d1e53dd9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Cómo: activar y desactivar (Object Relational Designer) la pluralización
De forma predeterminada, al arrastrar objetos de base de datos cuyos nombres terminan s o propiedades de **Explorador de servidores**/**el Explorador de base de datos** en el [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), se cambian los nombres de las clases de entidad generadas desde plural en singular. Este cambio se produce para representar con mayor precisión la asignación de la clase de entidad con instancias a un solo registro de datos. Por ejemplo, al agregar una tabla Customers al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], se genera una clase de entidad denominada Customer debido a que la clase contendrá los datos de un solo cliente.

> [!NOTE]
>  La pluralización está activada de forma predeterminada solamente en la versión en inglés de Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Para activar y desactivar la pluralización

1.  En el menú **Herramientas** , haga clic en **Opciones**.

2.  En el **opciones** cuadro de diálogo, expanda **herramientas de base de datos**.

    > [!NOTE]
    >  Seleccione **mostrar todas las configuraciones** si la **herramientas de base de datos** nodo no está visible.

3.  Haga clic en **Object Relational Designer**.

4.  Establecer **Pluralización de nombres** a **habilitado** = **False** para establecer el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] para que no cambie los nombres de clase.

5.  Establecer **Pluralización de nombres** a **habilitado** = **True** para aplicar las reglas de pluralización a los nombres de clase de los objetos agregados a la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

## <a name="see-also"></a>Vea también

- [Herramientas LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)