---
title: 'Cómo: establecer atributos de CLR en un elemento | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72ad9175729451c82fca3b61d06e449edaf8cf38
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662539"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Cómo: Establecer atributos de CLR en un elemento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los atributos personalizados son atributos especiales que se pueden agregar a elementos de dominio, formas, conectores y diagramas. Puede agregar cualquier atributo que herede de la clase `System.Attribute`.

### <a name="to-add-a-custom-attribute"></a>Para agregar un atributo personalizado

1. En el **Explorador de DSL**, seleccione el elemento al que desea agregar un atributo personalizado.

2. En la ventana **propiedades** , junto a la propiedad **atributos personalizados** , haga clic en el icono de examinar ( **...** ).

     Se abre el cuadro de diálogo **Editar atributos** .

3. En la columna **nombre** , haga clic en **\<add > de atributo** y escriba el nombre del atributo. Presione ENTRAR.

4. La línea bajo el nombre del atributo muestra paréntesis. En esta línea, escriba un tipo de parámetro para el atributo (por ejemplo, `string`) y, a continuación, presione Entrar.

5. En la columna de la **propiedad nombre** , escriba un nombre adecuado, por ejemplo, `MyString`.

6. Haga clic en **Aceptar**.

     La propiedad **atributos personalizados** ahora muestra el atributo con el siguiente formato:

     `[` *AttributeName* `(` *ParameterName* `=` *tipo* `)]`

## <a name="see-also"></a>Vea también
 [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
