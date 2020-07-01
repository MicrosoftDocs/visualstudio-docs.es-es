---
title: 'Cómo: Crear tipos con el Diseñador de clases'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Clr.ClrAttributesDialog
helpviewer_keywords:
- custom attributes, applying
- class diagrams, creating types
- classes [Visual Studio], creating with Class Designer
- Class Designer [Visual Studio], creating classes
- types [Visual Studio], class diagrams
- attributes [Visual Studio], applying custom
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7bdbc255320a2d17eb3c51191b3a425500dd345c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533697"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Cómo: Crear tipos con el Diseñador de clases

Para diseñar nuevos tipos para proyectos de C# y Visual Basic, créelos en un diagrama de clases. Para ver los tipos existentes, vea [Cómo: Ver los tipos existentes](how-to-view-existing-types.md).

## <a name="create-a-new-type"></a><a name="CreateType"></a> Crear un tipo nuevo

1. En el **cuadro de herramientas**, en **Diseñador de clases**, arrastre uno de estos a un diagrama de clases:

    - **Clase** o **Clase abstracta**

    - **Enum**

    - **Interface**

    - **Estructura** (VB) o **Struct** (C#)

    - **Delegate**

    - **Módulo** (solo en VB)

2. Escriba un nombre para el tipo. Después seleccione su nivel de acceso.

3. Seleccione el archivo donde desea agregar el código inicial para el tipo:

    - Para crear un archivo nuevo y agregarlo al proyecto actual, seleccione **Crear nuevo archivo** y escriba un nombre de archivo.

    - Para agregar código a un archivo existente, seleccione **Agregar al archivo existente**.

         Si la solución tiene un proyecto que comparte código en varias aplicaciones, puede agregar un nuevo tipo a un diagrama de clases del proyecto de la aplicación, pero solo si el archivo de clases correspondiente está en el mismo proyecto de la aplicación o en el proyecto compartido.

4. Ahora agregue otros elementos para definir el tipo:

    |**For**|**Add**|
    |-|-|
    |Clases, clases abstractas, estructuras o structs|Métodos, propiedades, campos, eventos, constructores (método), destructores (método) y constantes que definen el tipo|
    |Enumeraciones|Valores de campo que constituyen la enumeración|
    |Interfaces|Métodos, propiedades y eventos que constituyen la interfaz|
    |delegado|Parámetros que definen el delegado|
    |Módulo|Métodos, propiedades, campos, eventos, constructores (método) y constantes que definen el módulo|

     Vea [Crear miembros](creating-and-configuring-type-members.md#create-members).

## <a name="apply-a-custom-attribute-to-a-type"></a><a name="CustAttributeType"></a> Aplicar un atributo personalizado a un tipo

1. Haga clic en la forma del tipo en un diagrama de clases.

2. En **Propiedades**, junto a la propiedad **Atributos personalizados** del tipo, haga clic en el botón de puntos suspensivos (...).

3. Agregue uno o varios atributos personalizados, uno por línea. No los encierre entre corchetes.

   Los atributos personalizados se aplican al tipo.

## <a name="apply-a-custom-attribute-to-a-type-member"></a><a name="CustAttributeMember"></a> Aplicar un atributo personalizado a un miembro de tipo

1. Haga clic en el nombre del miembro, en la forma del tipo en un diagrama de clases o en la fila en la ventana Detalles de clase.

2. En **Propiedades**, busque la propiedad **Atributos personalizados** del miembro.

3. Agregue uno o varios atributos personalizados, uno por línea. No los encierre entre corchetes.

   Los atributos personalizados se aplican al tipo.

## <a name="see-also"></a>Vea también

- [Cómo: Crear la herencia entre tipos](how-to-create-inheritance-between-types.md)
- [Cómo: Crear asociaciones entre tipos](how-to-create-associations-between-types.md)
- [Creación y configuración de miembros de tipo](creating-and-configuring-type-members.md)
- [Diseño de clases y tipos](designing-and-viewing-classes-and-types.md)
