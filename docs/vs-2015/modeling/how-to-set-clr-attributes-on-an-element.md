---
title: Procedimiento Establecer atributos de CLR en un elemento | Documentos de Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f9af25934a40c01c6b4cfd48dcd7419bddf322d3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698026"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Procedimiento Establecer atributos de CLR en un elemento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los atributos personalizados son atributos especiales que se pueden agregar a diagramas, formas, conectores y elementos de dominio. Puede agregar cualquier atributo que hereda de la `System.Attribute` clase.  
  
### <a name="to-add-a-custom-attribute"></a>Para agregar un atributo personalizado  
  
1. En el **DSL Explorer**, seleccione el elemento al que desea agregar un atributo personalizado.  
  
2. En el **propiedades** ventana, junto a la **atributos personalizados** propiedad, haga clic en el ( **...** ) icono.  
  
     El **editar atributos** abre el cuadro de diálogo.  
  
3. En el **nombre** columna, haga clic en  **\<Agregar atributo >** y escriba el nombre del atributo. Presione ENTRAR.  
  
4. La línea bajo el nombre del atributo muestra entre paréntesis. En esta línea, escriba un tipo de parámetro para el atributo (por ejemplo, `string`), y, a continuación, presione ENTRAR.  
  
5. En el **nombre de propiedad** columna, escriba un nombre adecuado, por ejemplo, `MyString`.  
  
6. Haga clic en **Aceptar**.  
  
     El **atributos personalizados** propiedad ahora muestra el atributo en el formato siguiente:  
  
     `[` *AttributeName* `(` *ParameterName* `=` *tipo* `)]`  
  
## <a name="see-also"></a>Vea también  
 [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
