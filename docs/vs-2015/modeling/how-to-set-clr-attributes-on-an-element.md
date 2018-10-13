---
title: 'Cómo: establecer atributos de CLR en un elemento | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b77e0f1f31c0f617e80a27de4e1d0ab1d0b3d2eb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49264036"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Cómo: Establecer atributos de CLR en un elemento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los atributos personalizados son atributos especiales que se pueden agregar a diagramas, formas, conectores y elementos de dominio. Puede agregar cualquier atributo que hereda de la `System.Attribute` clase.  
  
### <a name="to-add-a-custom-attribute"></a>Para agregar un atributo personalizado  
  
1.  En el **DSL Explorer**, seleccione el elemento al que desea agregar un atributo personalizado.  
  
2.  En el **propiedades** ventana, junto a la **atributos personalizados** propiedad, haga clic en el (**...** ) icono.  
  
     El **editar atributos** abre el cuadro de diálogo.  
  
3.  En el **nombre** columna, haga clic en  **\<Agregar atributo >** y escriba el nombre del atributo. Presione ENTRAR.  
  
4.  La línea bajo el nombre del atributo muestra entre paréntesis. En esta línea, escriba un tipo de parámetro para el atributo (por ejemplo, `string`), y, a continuación, presione ENTRAR.  
  
5.  En el **nombre de propiedad** columna, escriba un nombre adecuado, por ejemplo, `MyString`.  
  
6.  Haga clic en **Aceptar**.  
  
     El **atributos personalizados** propiedad ahora muestra el atributo en el formato siguiente:  
  
     `[` *AttributeName* `(` *ParameterName* `=` *tipo* `)]`  
  
## <a name="see-also"></a>Vea también  
 [Glosario de las herramientas de lenguajes específicos de dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



