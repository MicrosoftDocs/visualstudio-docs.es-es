---
title: Animar objetos en el Diseñador XAML
ms.date: 04/11/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: c8f8b1b62634c9da86a6aa152bd48cbd8c712198
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921409"
---
# <a name="animate-objects-in-xaml-designer"></a>Animar objetos en el Diseñador XAML

Cree animaciones cortas para el movimiento y el fundido de objetos.

Para empezar, cree un *guión gráfico*, que puede contener una o más *escalas de tiempo*. Establezca *fotogramas clave* en una escala de tiempo para marcar los cambios de propiedad. Luego, al ejecutar la animación, Blend interpola los cambios de propiedad durante el período de tiempo designado, lo que produce una transición fluida. Se puede animar cualquier propiedad que pertenezca a un objeto, incluso las propiedades no visuales.

La siguiente ilustración muestra un guión gráfico denominado **MoveUp**. La escala de tiempo contiene fotogramas clave que marcan la posición X e Y de un rectángulo. Cuando se ejecuta esta animación, el rectángulo se mueve de una posición a otra de manera fluida.

![Guion gráfico MoveUp en el Diseñador XAML](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png)

## <a name="see-also"></a>Vea también

- [Creación de una interfaz de usuario con Blend para Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)