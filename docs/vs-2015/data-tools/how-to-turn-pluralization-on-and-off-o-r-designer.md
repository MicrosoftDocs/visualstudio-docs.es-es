---
title: Filtrar Activar y desactivar (Object Relational Designer) la pluralización | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9ff3f206f57a544053498def16318e0ed65b64ab
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987274"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Filtrar Activación y desactivación de la pluralización (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
De forma predeterminada, al arrastrar objetos de base de datos con nombres que terminan en s o es desde **Explorador de servidores**/**Database Explorer** hasta la [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), los nombres de las clases de entidad generadas cambian de plural a singular. Este cambio se produce para representar con mayor precisión la asignación de la clase de entidad con instancias a un solo registro de datos. Por ejemplo, al agregar una tabla Customers al [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], se genera una clase de entidad denominada Customer debido a que la clase contendrá los datos de un solo cliente.  
  
> [!NOTE]
>  La pluralización está activada de forma predeterminada solamente en la versión en inglés de Visual Studio.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>Para activar y desactivar la pluralización  
  
1.  En el menú **Herramientas** , haga clic en **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones**, expanda **Herramientas para bases de datos**.  
  
> [!NOTE]
>  Seleccione **Mostrar todas las configuraciones** si el nodo **Herramientas para bases de datos** no está visible.  
  
1.  Haga clic en **Object Relational Designer**.  
  
2.  Establecer **Pluralización de nombres** a **habilitado** = **False** para establecer el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] para que no cambia los nombres de clase.  
  
3.  Establecer **Pluralización de nombres** a **habilitado** = **True** para aplicar las reglas de pluralización a los nombres de clase de los objetos agregados a la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
