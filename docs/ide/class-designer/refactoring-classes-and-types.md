---
title: Cambiar el nombre y mover clases y tipos en el Diseñador de clases
ms.date: 11/04/2016
ms.topic: how-to
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: baf0e9d9d0f4bb45ef965f64c256bd9360af112b
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768612"
---
# <a name="refactor-classes-and-types-in-class-designer"></a>Refactorizar clases y tipos en el Diseñador de clases

Al refactorizar el código, lo hace más fácil de entender y mantener, y más eficiente al cambiar su estructura interna y la manera en la que están diseñados los objetos, no su comportamiento externo. Utilice el Diseñador de clases y la ventana Detalles de clase para reducir el trabajo necesario y la posibilidad de que se introduzcan errores al refactorizar código de C#, Visual Basic o C++en el proyecto de Visual Studio.

> [!NOTE]
> Si los archivos de un proyecto son de solo lectura, el motivo puede ser que el proyecto esté bajo el control del código fuente y no esté desprotegido, que sea un proyecto al que se hace referencia o que sus archivos estén marcados como de solo lectura en el disco. Al trabajar en un proyecto que se encuentre en uno de estos estados, se le presentarán varias formas de guardar el trabajo según el estado del proyecto. Esto se aplica a la refactorización de código y también al código que cambie de otro modo como, por ejemplo, editándolo directamente.

## <a name="common-tasks"></a>Tareas comunes

|Tarea|Contenido adicional|
|----------| - |
|**Refactorización de clases:** puede utilizar operaciones de refactorización para dividir una clase en clases parciales o para implementar una clase base abstracta.|-   [Cómo: Dividir una clase en clases parciales](how-to-split-a-class-into-partial-classes.md)|
|**Trabajo con interfaces:** en el Diseñador de clases, puede implementar una interfaz en el diagrama de clases conectándola a una clase que proporcione el código para los métodos de interfaz.|-   [Cómo: Implementar una interfaz](how-to-implement-an-interface.md)|
|**Refactorización de tipos, miembros de tipos y parámetros:** con el Diseñador de clases puede cambiar el nombre de tipos, invalidar miembros de tipos o moverlos de un tipo a otro. También puede crear tipos que acepten valores NULL.|-   [Cambio de nombre de tipos y miembros de tipos](#rename-types-and-type-members)<br />-   [Traslado de miembros de tipo de un tipo a otro](#move-type-members-from-one-type-to-another)<br />-   [Cómo: Crear un tipo que acepta valores NULL](how-to-create-a-nullable-type.md)|

## <a name="rename-types-and-type-members"></a>Cambio de nombre de tipos y miembros de tipos

En el Diseñador de clases, puede cambiar el nombre de un tipo o un miembro de un tipo en el diagrama de clases o en la ventana **Propiedades**. En la ventana **Detalles de clase**, puede cambiar el nombre de un miembro, pero no de un tipo. Al cambiar el nombre de un tipo o un miembro de tipo, el cambio se propagará a todas las ventanas y las ubicaciones de código donde apareciera el nombre anterior.

### <a name="rename-in-the-class-designer"></a>Cambiar el nombre en el Diseñador de clases

1. En el diagrama de clases, seleccione el tipo o el miembro y, después, el nombre.

     El nombre del miembro pasará a ser editable.

2. Escribir el nuevo nombre del tipo o el miembro de tipo

### <a name="rename-in-the-class-details-window"></a>Cambiar el nombre en la ventana Detalles de clase

1. Para mostrar la ventana **Detalles de clase**, haga clic con el botón derecho en el tipo o el miembro de tipo y seleccione **Detalles de clase**.

     Aparecerá la ventana **Detalles de clase**.

2. En la columna **Nombre** , cambie el nombre del miembro de tipo.

3. Para mover el foco fuera de la celda, presione la tecla **Entrar** o haga clic fuera de la celda.

    > [!NOTE]
    > En la ventana **Detalles de clase**, puede cambiar el nombre de un miembro, pero no de un tipo.

### <a name="rename-in-the-properties-window"></a>Cambiar el nombre en la ventana Propiedades

1. En el diagrama de clases o en la ventana **Detalles de clase**, haga clic con el botón derecho en el tipo o el miembro y, luego, seleccione **Propiedades**.

     Aparecerá la ventana **Propiedades**, que muestra las propiedades del tipo o el miembro de tipo.

2. En la propiedad **Nombre** , cambie el nombre del tipo o el miembro de tipo.

     El nuevo nombre se propagará a todas las ventanas y las ubicaciones de código del proyecto actual donde apareciera el nombre anterior.

## <a name="move-type-members-from-one-type-to-another"></a>Traslado de miembros de tipo de un tipo a otro

Con el **Diseñador de clases**, puede mover un miembro de tipo de un tipo a otro. Ambos tipos deben estar visibles en el diagrama de clases actual.

1. En un tipo que esté visible en la superficie de diseño, haga clic con el botón derecho en el miembro que quiera mover a otro tipo y, después, seleccione **Cortar**.

2. Haga clic con el botón derecho en el tipo de destino y seleccione **Pegar**.

     La propiedad se quitará del tipo de origen y aparecerá en el tipo de destino.

## <a name="see-also"></a>Vea también

- [Diseño de clases y tipos](designing-and-viewing-classes-and-types.md)
