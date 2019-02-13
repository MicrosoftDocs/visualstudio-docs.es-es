---
title: Refactorización de clases y tipos (Diseñador de clases) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ClassDesigner.OverrideMembersDialog
helpviewer_keywords:
- members, overriding
- overriding members
- classes [Visual Studio], refactoring
- type members, overriding
- refactoring, types
- types [Visual Studio], refactoring
- Class Designer [Visual Studio], refactoring classes
- refactoring, classes
ms.assetid: dcf07bb4-fa3b-4224-9dec-566fd924a8ce
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e6a150d32fa4eb5bc162f9ce8522ddfed634253b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782131"
---
# <a name="refactoring-classes-and-types-class-designer"></a>Refactorización de clases y tipos (Diseñador de clases)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al refactorizar el código, lo hace más fácil de entender y mantener, y más eficiente al cambiar su estructura interna y la manera en la que están diseñados los objetos, no su comportamiento externo. Utilice el Diseñador de clases y la ventana Detalles de clase para reducir el trabajo necesario y la posibilidad de que se introduzcan errores al refactorizar código de .NET de Visual C#, .NET de Visual Basic o C++ en el proyecto de Visual Studio.  
  
> [!NOTE]
>  Si los archivos de un proyecto son de solo lectura, el motivo puede ser que el proyecto esté bajo el control del código fuente y no esté desprotegido, que sea un proyecto al que se hace referencia o que sus archivos estén marcados como de solo lectura en el disco. Al trabajar en un proyecto que se encuentre en uno de estos estados, se le presentarán varias formas de guardar el trabajo según el estado del proyecto. Esto se aplica a la refactorización de código y también al código que cambie de otro modo como, por ejemplo, editándolo directamente. Para obtener más información, consulte [Presentación de la información de solo lectura (Diseñador de clases)](http://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tarea|Contenido adicional|  
|----------|------------------------|  
|**Refactorización de clases:** puede utilizar operaciones de refactorización para dividir una clase en clases parciales o para implementar una clase base abstracta.|-   [Cómo: Dividir una clase en clases parciales (Diseñador de clases)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md)|  
|**Trabajo con interfaces:** en el Diseñador de clases, puede implementar una interfaz en el diagrama de clases conectándola a una clase que proporcione el código para los métodos de interfaz.|-   [Cómo: Implementar una interfaz (Diseñador de clases)](../ide/how-to-implement-an-interface-class-designer.md)|  
|**Refactorización de tipos, miembros de tipos y parámetros:** con el Diseñador de clases puede cambiar el nombre de tipos, invalidar miembros de tipos o moverlos de un tipo a otro. También puede crear tipos que acepten valores NULL.|-   [Cambio de nombre de tipos y miembros de tipos](../ide/refactoring-classes-and-types-class-designer.md#RenamingTypesAndMembers)<br />-   [Traslado de miembros de tipo de un tipo a otro](../ide/refactoring-classes-and-types-class-designer.md#MovingTypeMembers)<br />-   [Cómo: Crear un tipo que acepta valores NULL (Diseñador de clases)](../ide/how-to-create-a-nullable-type-class-designer.md)|  
  
###  <a name="RenamingTypesAndMembers"></a> Cambio de nombre de tipos y miembros de tipos  
 En el Diseñador de clases, puede cambiar el nombre de un tipo o un miembro de un tipo en el diagrama de clases o en la ventana Propiedades. En la ventana Detalles de clase, puede cambiar el nombre de un miembro, pero no un tipo. Al cambiar el nombre de un tipo o un miembro de tipo, el cambio se propagará a todas las ventanas y las ubicaciones de código donde apareciera el nombre anterior.  
  
##### <a name="to-rename-a-name-in-the-class-designer"></a>Para cambiar un nombre en el Diseñador de clases  
  
1.  En el diagrama de clases, seleccione el tipo o el miembro y haga clic en el nombre.  
  
     El nombre del miembro pasará a ser editable.  
  
2.  Escribir el nuevo nombre del tipo o el miembro de tipo  
  
##### <a name="to-rename-a-name-in-the-class-details-window"></a>Para cambiar un nombre en la ventana Detalles de clase  
  
1.  Para mostrar la ventana Detalles de clase, haga clic con el botón secundario en el tipo o el miembro de tipo y, luego, haga clic en **Detalles de clase**.  
  
     Aparecerá la ventana Detalles de clase.  
  
2.  En la columna **Nombre** , cambie el nombre del miembro de tipo.  
  
3.  Para mover el foco fuera de la celda, presione la tecla **ENTRAR** o haga clic fuera de la celda.  
  
    > [!NOTE]
    >  En la ventana Detalles de clase, puede cambiar el nombre de un miembro, pero no un tipo.  
  
##### <a name="to-rename-a-name-in-the-properties-window"></a>Para cambiar un nombre en la ventana Propiedades  
  
1.  En el diagrama de clases o en la ventana Detalles de clase, haga clic con el botón secundario en el tipo o el miembro y, luego, haga clic en **Propiedades**.  
  
     Aparecerá la ventana Propiedades, que muestra las propiedades del tipo o el miembro de tipo.  
  
2.  En la propiedad **Nombre** , cambie el nombre del tipo o el miembro de tipo.  
  
     El nuevo nombre se propagará a todas las ventanas y las ubicaciones de código del proyecto actual donde apareciera el nombre anterior.  
  
###  <a name="MovingTypeMembers"></a> Traslado de miembros de tipo de un tipo a otro  
 Con el **Diseñador de clases**, puede mover un miembro de tipo de un tipo a otro, si los dos se encuentran visibles en el diagrama de clases actual.  
  
##### <a name="to-move-a-type-member-from-one-type-to-another"></a>Para mover un miembro de tipo de un tipo a otro  
  
1.  En un tipo que esté visible en la superficie de diseño, haga clic con el botón secundario en el miembro que quiera mover a otro tipo y, después, haga clic en **Cortar**.  
  
2.  Haga clic con el botón secundario en el tipo de destino y, luego, haga clic en **Pegar**.  
  
     La propiedad se quitará del tipo de origen y aparecerá en el tipo de destino.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Title|Descripción|  
|-----------|-----------------|  
|[Ver tipos y relaciones (Diseñador de clases)](../ide/viewing-types-and-relationships-class-designer.md)||  
|[Diseñar clases y tipos (Diseñador de clases)](../ide/designing-classes-and-types-class-designer.md)||
