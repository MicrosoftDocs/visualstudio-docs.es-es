---
title: 'Cómo: Establecer atributos de CLR en un elemento'
description: Obtenga información sobre cómo puede agregar cualquier atributo que herede de la clase System.Attribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b11a6bd4a04bdb469cdf5c2fe2d7b78e0c0fe29a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387338"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Cómo: Establecer atributos de CLR en un elemento
Los atributos personalizados son atributos especiales que se pueden agregar a elementos de dominio, formas, conectores y diagramas. Puede agregar cualquier atributo que herede de la `System.Attribute` clase .

### <a name="to-add-a-custom-attribute"></a>Para agregar un atributo personalizado

1. En el **Explorador DSL,** seleccione el elemento al que desea agregar un atributo personalizado.

2. En la **ventana Propiedades,** junto a la **propiedad Atributos personalizados,** haga clic en el icono Examinar (**...**).

     Se **abre el cuadro de diálogo** Editar atributos.

3. En la **columna** Nombre, haga clic **\<add attribute>** y escriba el nombre del atributo. Presione ENTRAR.

4. La línea bajo el nombre del atributo muestra paréntesis. En esta línea, escriba un tipo de parámetro para el atributo (por ejemplo, `string` ) y presione ENTRAR.

5. En la **columna Propiedad de** nombre, escriba un nombre adecuado, por ejemplo, `MyString` .

6. Haga clic en **Aceptar**.

     La **propiedad Atributos personalizados** ahora muestra el atributo en el formato siguiente:

     `[`*AttributeName* `(` *ParameterName* `=` *Tipo*`)]`

## <a name="see-also"></a>Vea también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))