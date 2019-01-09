---
title: Procedimiento Visualizar una asociación de colecciones (Diseñador de clases)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: acf1fd75770888f492833235f09a381d0836be34
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53925399"
---
# <a name="how-to-visualize-a-collection-association-in-class-designer"></a>Procedimiento Visualizar una asociación de colecciones en el Diseñador de clases

Las propiedades y campos que son colecciones de otros tipos se pueden mostrar en el diagrama de clase como una asociación de colecciones. A diferencia de una asociación normal, que muestra un campo o propiedad como una línea que vincula la clase propietaria con el tipo de campo, una asociación de colecciones se muestra como una línea que vincula la clase propietaria con el tipo recopilado.

## <a name="to-create-a-collection-association"></a>Para crear una colección de asociación

1.  En el código, cree una propiedad o un campo cuyo tipo sea una colección fuertemente tipada.

2.  En el diagrama de clases, expanda la clase para que se muestren los campos y propiedades.

3.  En la clase, haga clic en el campo o la propiedad y elija **Mostrar como asociación de colecciones**.

La propiedad o el campo se muestra como una línea de asociación que se vincula al tipo recopilado.

## <a name="see-also"></a>Vea también

- [Cómo: Crear asociaciones entre tipos](how-to-create-associations-between-types.md)
- [Diseño de clases y tipos](designing-and-viewing-classes-and-types.md)
