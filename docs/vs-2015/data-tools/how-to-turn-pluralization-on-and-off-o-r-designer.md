---
title: 'Cómo: activar y desactivar la pluralización (Object Relational Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: afe8c8a4429efb83c09d80a5dd00dfe08b0d63e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665932"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Procedimiento para activar y desactivar la pluralización (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

De forma predeterminada, al arrastrar objetos de base de datos que tienen nombres que terminan en o desde **Explorador de servidores** /**Explorador de bases de datos** en las [herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), los nombres de las clases de entidad generadas cambian de plural a particular. Este cambio se produce para representar con mayor precisión la asignación de la clase de entidad con instancias a un solo registro de datos. Por ejemplo, al agregar una tabla Customers al [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], se genera una clase de entidad denominada Customer debido a que la clase contendrá los datos de un solo cliente.

> [!NOTE]
> La pluralización está activada de forma predeterminada solamente en la versión en inglés de Visual Studio.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Para activar y desactivar la pluralización

1. En el menú **Herramientas** , haga clic en **Opciones**.

2. En el cuadro de diálogo **Opciones**, expanda **Herramientas para bases de datos**.

> [!NOTE]
> Seleccione **Mostrar todas las configuraciones** si el nodo **Herramientas para bases de datos** no está visible.

1. Haga clic en **Object Relational Designer**.

2. Establezca la **pluralización de nombres** en **habilitado**  = **false** para establecer el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] de modo que no cambie los nombres de clase.

3. Establezca la **pluralización de nombres** en **habilitado**  = **true** para aplicar las reglas de pluralización a los nombres de clase de los objetos agregados a la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

## <a name="see-also"></a>Vea también
 [LINQ to SQL herramientas en visual studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [acceder a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
