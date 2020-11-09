---
title: Los tipos de propiedad no coinciden
description: No se puede crear una asociación; los tipos de propiedad no coinciden. Vea información sobre este mensaje de Object Relational Designer de Visual Studio (Object Relational Designer).
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 97ec5a04-6e23-45a2-9226-d77ead854392
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: bce5a285f3bccdc2be8004f0eba4546bb7964a42
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382057"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-types-do-not-match"></a>No se puede crear una asociación &lt;nombre de asociación&gt;; los tipos de propiedad no coinciden.

No se puede crear una asociación \<association name> ; los tipos de propiedad no coinciden. Las propiedades no tienen tipos coincidentes: \<property names> .

Las asociaciones las define el comando **Propiedades de la asociación** seleccionado en el cuadro de diálogo **Editor de asociaciones**. Las propiedades a ambos lados de la asociación deben ser del mismo tipo de datos.

Las propiedades especificadas en el mensaje no tienen los mismos tipos de datos.

## <a name="to-correct-this-error"></a>Para corregir este error

1. Examine el mensaje y fíjese en las propiedades especificadas en el mensaje.

2. Haga clic en **Aceptar** para descartar el cuadro de diálogo.

3. Examine las **Propiedades de la asociación** y seleccione propiedades que tengan el mismo tipo de datos.

4. Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también

- [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Cómo: crear una asociación entre clases LINQ to SQL (Object Relational Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)