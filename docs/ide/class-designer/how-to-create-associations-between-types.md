---
title: Procedimiento Crear asociaciones entre tipos (Diseñador de clases)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bfab593674b10e483308df5407fa56f3568804d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54977816"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>Procedimiento Crear asociaciones entre tipos en Diseñador de clases

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

## <a name="see-also"></a>Vea también

- [Cómo: Cambiar entre notación de miembro y notación de asociación](how-to-change-between-member-notation-and-association-notation.md)
