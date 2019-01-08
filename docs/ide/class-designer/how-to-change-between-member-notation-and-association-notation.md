---
title: Procedimiento Cambiar entre notación de miembro y notación de asociación (Diseñador de clases)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db6bcf1d44be4a904b38877717aff589906995a7
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684160"
---
# <a name="how-to-change-between-member-notation-and-association-notation-in-class-designer"></a>Procedimiento Cambiar entre notación de miembro y notación de asociación en el Diseñador de clases

En el **Diseñador de clases**, puede cambiar el modo en que el diagrama de clases representa una relación de asociación entre dos tipos de notación de miembro a notación de asociación y viceversa. Los miembros que se muestran como líneas de asociación a menudo ofrecen una visualización útil de cómo se relacionan los tipos.

> [!NOTE]
> Las relaciones de asociación se pueden representar como una propiedad de miembro o campo. Para cambiar de notación de miembro a notación de asociación, un tipo debe tener un miembro de otro tipo. Para cambiar de notación de asociación a notación de miembro, los dos tipos deben estar conectados mediante una línea de asociación. Para obtener más información, vea [Cómo: Crear asociaciones entre tipos](how-to-create-associations-between-types.md). Si el proyecto contiene varios diagramas de clases, los cambios realizados a la forma en que un diagrama muestra las relaciones de asociación afectan solo a ese diagrama. Para cambiar la forma en que otro diagrama muestra las relaciones de asociación, abra o muestre el diagrama y siga estos pasos.

## <a name="to-change-member-notation-to-association-notation"></a>Para cambiar de notación de miembro a notación de asociación

1.  Desde el nodo del proyecto, en el Explorador de soluciones, abra el archivo de diagrama de clases (.cd).

2.  En la forma de tipo en el diagrama de clases, haga clic en la propiedad de miembro o campo que representa la asociación y elija **Mostrar como asociación**.

    > [!TIP]
    > Si no hay propiedades o campos visibles en la forma de tipo, puede que los compartimientos de la forma estén contraídos. Para expandir la forma de tipo, haga doble clic en el nombre del compartimiento o haga clic con el botón derecho en la forma de tipo y elija **Expandir**.

    El miembro desaparece del compartimiento en la forma de tipo y aparece una línea de asociación que conecta los dos tipos. La línea de asociación se etiqueta con el nombre de la propiedad o el campo.

## <a name="to-change-association-notation-to-member-notation"></a>Para cambiar de notación de asociación a notación de miembro

En el diagrama de clases, haga clic con el botón derecho en la línea de asociación y elija **Mostrar como propiedad** o **Mostrar como campo** según corresponda. La línea de asociación desaparece y la propiedad se muestra en el compartimiento correspondiente dentro de su forma de tipo en el diagrama.

## <a name="see-also"></a>Vea también

- [Cómo: Crear herencia entre tipos](how-to-create-inheritance-between-types.md)
- [Cómo: Ver la herencia entre tipos](how-to-view-inheritance-between-types.md)
- [Visualización de tipos y relaciones](designing-and-viewing-classes-and-types.md)
- [Cómo: Visualizar una asociación de colecciones](how-to-visualize-a-collection-association.md)