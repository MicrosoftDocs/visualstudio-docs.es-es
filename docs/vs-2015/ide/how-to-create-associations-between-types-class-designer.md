---
title: Procedimiento Crear asociaciones entre tipos (Diseñador de clases) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2d152ce38c445955988ec76a2e328691eac152ca
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63416950"
---
# <a name="how-to-create-associations-between-types-class-designer"></a>Procedimiento Crear asociaciones entre tipos (Diseñador de clases)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En el Diseñador de clases, las líneas de asociación muestran la forma en que se relacionan las clases en un diagrama. Una línea de asociación representa una clase que es el tipo de una propiedad o un campo de otra clase del proyecto. Las líneas de asociación se utilizan generalmente para ilustrar las relaciones más importantes entre las clases del proyecto.  
  
 A pesar de que todos los campos y propiedades se pueden mostrar como asociaciones, tiene más sentido mostrar sólo los miembros importantes como asociaciones, dependiendo de lo que se desee resaltar en el diagrama. Puede mostrar los miembros menos importantes como miembros normales u ocultarlos totalmente.  
  
> [!NOTE]
> El Diseñador de clases sólo admite asociaciones unidireccionales.  
  
### <a name="to-define-an-association-line-in-the-class-diagram"></a>Para definir una línea de asociación en el Diagrama de clases  
  
1. En el cuadro de herramientas, en el Diseñador de clases, seleccione **Asociación**.  
  
2. Trace una línea entre las dos formas que desee vincular con una asociación.  
  
     Se crea una nueva propiedad en la primera clase. Esta propiedad se muestra como línea de asociación (no como propiedad dentro de un compartimiento de la forma) con un nombre predeterminado. Su tipo es la forma a la que señala la línea de asociación.  
  
### <a name="to-change-the-name-of-an-association"></a>Para cambiar el nombre de una asociación  
  
- En la superficie de diagrama, haga clic en la etiqueta de la línea de asociación y edítela.  
  
  \- o -  
  
1. Haga clic en la forma que contiene la propiedad mostrada como asociación.  
  
     La forma obtiene el foco y sus miembros aparecen en la ventana Detalles de clase y en la ventana Propiedades.  
  
2. En la ventana Detalles de clase o la ventana Propiedades, edite el campo de nombre de la propiedad y presione ENTRAR.  
  
     El nombre se actualiza en la ventana **Detalles de clase**, en la línea de asociación, en la ventana Propiedades y en el código.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Cambiar entre notación de miembro y notación de asociación (Diseñador de clases)](../ide/how-to-change-between-member-notation-and-association-notation-class-designer.md)
