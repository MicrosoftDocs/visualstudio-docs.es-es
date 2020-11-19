---
title: 'Cómo: definir el descriptor de tipo de un parámetro | Microsoft Docs'
description: Obtenga información sobre cómo definir el descriptor de tipo de un parámetro para un método en el modelo de conectividad a datos profesionales (BDC).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8044f04902e74b2597d6cf331e54eb4a6138817a
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903603"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Cómo: definir el descriptor de tipo de un parámetro
  Un descriptor de tipo contiene propiedades que describen el tipo de datos de un parámetro. Un descriptor de tipo puede definir un campo, una entidad o una colección de entidades. Para obtener más información, vea [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-the-type-descriptor-of-a-parameter"></a>Para definir el descriptor de tipo de un parámetro

1. En la ventana **detalles del método de BDC** , elija el descriptor de tipo del parámetro.

2. En la barra de menús, elija **Ver**, **ventana Propiedades**.

3. En la ventana **propiedades** , establezca las propiedades del descriptor de tipos.

     En los procedimientos siguientes se describe cómo se define un descriptor de tipo como un campo, entidad o colección de entidades.

### <a name="to-define-a-field"></a>Para definir un campo

1. En la ventana **propiedades** , establezca la propiedad **nombre** del descriptor de tipo en el nombre de un campo del tipo que representa la entidad (por ejemplo: **FirstName**).

2. En la lista situada junto a la propiedad **TypeName** , elija el tipo de datos adecuado (por ejemplo, **Int32**).

     Para obtener información sobre otros parámetros opcionales, vea [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-an-entity"></a>Para definir una entidad

1. En la ventana **propiedades** , establezca la propiedad **nombre** en un nombre que describa la entidad (por ejemplo: **contacto**).

2. Establezca la propiedad **TypeName** en el nombre completo del tipo que representa la entidad. Este tipo puede ser una clase del proyecto, un tipo definido en un ensamblado al que se hace referencia en la solución o un tipo definido en el modelo de objetos de BDC.

    - Para una clase del proyecto, elija la flecha abajo situada junto a la propiedad **TypeName** , elija la pestaña **proyecto actual** en el cuadro de diálogo que aparece y, a continuación, elija la clase en el proyecto.

         El nombre completo incluye el espacio de nombres y el nombre de la clase seguidos del nombre del sistema LOB. En el ejemplo siguiente se establece el valor de la propiedad **TypeName** en una clase del proyecto.

         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`

    - Si se trata de un tipo ubicado en un ensamblado de la solución, el nombre completo contiene el nombre del tipo, el nombre del ensamblado, el número de versión, la referencia cultural y el token de clave pública.

         En el ejemplo siguiente se establece el valor de la propiedad **TypeName** en un tipo definido en un ensamblado al que se hace referencia en la solución.

         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

    - Si se trata de un tipo definido en el modelo de objetos de BDC, el nombre completo incluye el espacio de nombres y el nombre del tipo.

         En el ejemplo siguiente se establece el valor de la propiedad **TypeName** en un tipo del modelo de objetos de BDC.

         `Microsoft.BusinessData.Runtime.DynamicType`

3. En la ventana **detalles del método de BDC** , abra la lista que aparece para el descriptor de tipos y, a continuación, elija **Editar**.

     Se abre la ventana **Explorador de BDC** .

4. En el **Explorador de BDC**, abra el menú contextual del descriptor de tipo y, a continuación, elija **Agregar descriptor de tipos**.

     Un nuevo descriptor de tipo se agrega como elemento secundario al descriptor de tipo de entidad. Configure este descriptor de tipo como un campo.

5. Repita el paso 4 para agregar un descriptor de tipo secundario en cada campo de la entidad.

### <a name="to-define-a-collection-of-entities"></a>Para definir una colección de entidades

1. En la ventana **detalles del método de BDC** , elija el descriptor de tipo del parámetro que desee.

2. En la barra de menús, elija **Ver**, **ventana Propiedades**.

3. En la ventana **propiedades** , establezca la propiedad **nombre** en un nombre que describa la entidad (por ejemplo: **contactos**).

4. Establezca la propiedad **IsCollection** en **true**. Esto indica que este descriptor de tipo es una colección de entidades.

5. Establezca la propiedad **TypeName** en una cadena que contenga una referencia a la <xref:System.Collections.Generic.IEnumerable%601> interfaz y el nombre completo del tipo que representa la entidad. Este tipo puede ser una clase del proyecto, un tipo definido en un ensamblado al que se hace referencia en la solución o un tipo definido en el modelo de objetos de BDC.

   - Para una clase del proyecto, elija la flecha abajo situada junto a la propiedad **TypeName** , elija la pestaña **proyecto actual** en el cuadro de diálogo que aparece y, a continuación, elija la clase en el proyecto.

      El nombre completo incluye el espacio de nombres y el nombre de la clase seguidos del nombre del sistema LOB.

      En el ejemplo siguiente se establece el valor de la propiedad **TypeName** en una colección de clases del proyecto.

      `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace. BdcModel1. contact, BdcModel1] '

   - Si se trata de un tipo ubicado en un ensamblado de la solución, el nombre completo contiene el nombre del tipo, el nombre del ensamblado, el número de versión, la referencia cultural y el token de clave pública.

      En el ejemplo siguiente se establece el valor de la propiedad **TypeName** en una colección de tipos de un ensamblado al que se hace referencia en la solución.

      `System.Collections.Generic.IEnumerable`1 [myNameSpace. contact, myAssemblyName, version = 4.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089] '

   - Si se trata de un tipo definido en el modelo de objetos de BDC, el nombre completo solamente incluye el espacio de nombres y el nombre del tipo.

      En el ejemplo siguiente se establece el valor de la propiedad **TypeName** en una colección de tipos definidos en el modelo de objetos de BDC.

      `System.Collections.Generic.IEnumerable`1 [Microsoft. BusinessData. Runtime. DynamicType] '

6. En la ventana **detalles del método de BDC** , abra la lista que aparece para el descriptor de tipos y, a continuación, elija **Editar**.

    Se abre la ventana **Explorador de BDC** .

7. En el **Explorador de BDC**, abra el menú contextual del descriptor de tipo y, a continuación, elija **Agregar descriptor de tipos**.

    Un nuevo descriptor de tipo se agrega como elemento secundario al descriptor de tipo de la colección. Configure este descriptor de tipo como una entidad.

## <a name="see-also"></a>Consulte también
- [Introducción a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Cómo: definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)
- [Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)
