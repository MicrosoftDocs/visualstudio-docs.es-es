---
title: Crear asociaciones entre tipos
description: Aprenda a crear asociaciones entre diferentes tipos en el Diseñador de clases.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e7cb4e344ca2ecde2f3644b57f0d26773b6294bb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880533"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>Cómo: Crear asociaciones entre tipos en el Diseñador de clases

En el **Diseñador de clases**, las líneas de asociación muestran la forma en que se relacionan las clases de un diagrama. Una línea de asociación representa una clase que es el tipo de una propiedad o un campo de otra clase del proyecto. Las líneas de asociación se utilizan generalmente para ilustrar las relaciones más importantes entre las clases del proyecto.

A pesar de que todos los campos y propiedades se pueden mostrar como asociaciones, tiene más sentido mostrar sólo los miembros importantes como asociaciones, dependiendo de lo que se desee resaltar en el diagrama. Puede mostrar los miembros menos importantes como miembros normales u ocultarlos totalmente.

> [!NOTE]
> El **Diseñador de clases** solo admite asociaciones unidireccionales.

## <a name="to-define-an-association-line-in-the-class-diagram"></a>Para definir una línea de asociación en el Diagrama de clases

1. En el cuadro de herramientas, en **Diseñador de clases**, seleccione **Asociación**.

2. Trace una línea entre las dos formas que desee vincular con una asociación.

     Se crea una nueva propiedad en la primera clase. Esta propiedad se muestra como línea de asociación (no como propiedad dentro de un compartimiento de la forma) con un nombre predeterminado. Su tipo es la forma a la que señala la línea de asociación.

## <a name="to-change-the-name-of-an-association"></a>Para cambiar el nombre de una asociación

En la superficie de diagrama, haga clic en la etiqueta de la línea de asociación y edítela.

Como alternativa, siga estos pasos:

1. Seleccione la forma que contiene la propiedad mostrada como asociación.

   La forma obtiene el foco y sus miembros aparecen en las ventanas **Detalles de clase** y **Propiedades**.

2. En la ventana **Detalles de clase** o **Propiedades**, edite el campo de nombre de la propiedad y presione **Entrar**.

   El nombre se actualiza en la ventana **Detalles de clase**, en la línea de asociación, en la ventana **Propiedades** y en el código.

## <a name="see-also"></a>Consulte también

- [Cómo: Cambiar entre notación de miembro y notación de asociación](how-to-change-between-member-notation-and-association-notation.md)
