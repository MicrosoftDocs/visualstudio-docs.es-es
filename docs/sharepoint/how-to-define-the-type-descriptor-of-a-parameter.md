---
title: "How to: Define the Type Descriptor of a Parameter"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor"
  - "BDC [SharePoint development in Visual Studio], parameter types"
  - "BDC [SharePoint development in Visual Studio], type descriptor"
  - "Business Data Connectivity service [SharePoint development in Visual Studio], parameter types"
ms.assetid: 7494559f-1567-4cbd-bde0-05a2ed288c3a
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# How to: Define the Type Descriptor of a Parameter
  Un descriptor de tipo contiene propiedades que describen el tipo de datos de un parámetro.  Un descriptor de tipo puede definir un campo, una entidad o una colección de entidades.  Para obtener más información, consulte [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### Para definir el descriptor de tipo de un parámetro  
  
1.  En la ventana **Detalles del método de BDC**, elija el descriptor de tipo del parámetro.  
  
2.  En la barra de menús, elija **Ver** y después elija **Ventana Propiedades**.  
  
3.  En la ventana **Propiedades**, establezca las propiedades del descriptor de tipo.  
  
     En los procedimientos siguientes se describe cómo se define un descriptor de tipo como un campo, entidad o colección de entidades.  
  
### Para definir un campo  
  
1.  En la ventana **Propiedades**, establezca la propiedad **Name** del descriptor de tipo en el nombre de un campo del tipo que representa la entidad \(por ejemplo, FirstName\).  
  
2.  En la lista situada junto a la propiedad **TypeName**, elija el tipo de datos adecuado \(por ejemplo, **Int32**\).  
  
     Para obtener información acerca de los parámetros opcionales, consulte [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### Para definir una entidad  
  
1.  En la ventana **Propiedades**, establezca la propiedad **Name** en un nombre que describa la entidad \(por ejemplo, Contact\).  
  
2.  Establezca la propiedad **TypeName** en el nombre completo del tipo que representa la entidad.  Este tipo puede ser una clase del proyecto, un tipo definido en un ensamblado al que se hace referencia en la solución o un tipo definido en el modelo de objetos de BDC.  
  
    -   Si se trata de una clase del proyecto, elija la flecha abajo situada junto a la propiedad **TypeName**, elija la pestaña **Proyecto actual** en el cuadro de diálogo que aparece y, a continuación, elija la clase del proyecto.  
  
         El nombre completo incluye el espacio de nombres y el nombre de la clase seguidos del nombre del sistema LOB.  En el ejemplo siguiente se establece el valor de la propiedad **TypeName** en una clase del proyecto.  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   Si se trata de un tipo ubicado en un ensamblado de la solución, el nombre completo contiene el nombre del tipo, el nombre del ensamblado, el número de versión, la referencia cultural y el token de clave pública.  
  
         En el ejemplo siguiente se establece el valor de la propiedad **TypeName** en un tipo definido en un ensamblado al que se hace referencia en la solución.  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   Si se trata de un tipo definido en el modelo de objetos de BDC, el nombre completo incluye el espacio de nombres y el nombre del tipo.  
  
         En el siguiente ejemplo se establece el valor de la propiedad **TypeName** en un tipo del modelo de objetos de BDC.  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  En la ventana **Detalles del método de BDC**, abra la lista que aparece en el descriptor de tipo y, a continuación, elija **Editar**.  
  
     Se abre la ventana **Explorador de BDC**.  
  
4.  En el **Explorador de BDC**, abra el menú contextual del descriptor de tipo y, a continuación, elija **Agregar descriptor de tipo**.  
  
     Un nuevo descriptor de tipo se agrega como elemento secundario al descriptor de tipo de entidad.  Configure este descriptor de tipo como un campo.  
  
5.  Repita el paso 4 para agregar un descriptor de tipo secundario en cada campo de la entidad.  
  
### Para definir una colección de entidades  
  
1.  En la ventana **Detalles del método de BDC**, elija el descriptor de tipo del parámetro que desea.  
  
2.  En la barra de menús, elija **Ver** y después elija **Ventana Propiedades**.  
  
3.  En la ventana **Propiedades**, establezca la propiedad **Name** en un nombre que describa la entidad \(por ejemplo, Contacts\).  
  
4.  Establezca la propiedad **IsCollection** en **True**.  Esto indica que este descriptor de tipo es una colección de entidades.  
  
5.  Establezca la propiedad **TypeName** en una cadena que contenga una referencia a la interfaz <xref:System.Collections.Generic.IEnumerable%601> y el nombre completo del tipo que representa la entidad.  Este tipo puede ser una clase del proyecto, un tipo definido en un ensamblado al que se hace referencia en la solución o un tipo definido en el modelo de objetos de BDC.  
  
    -   Si se trata de una clase del proyecto, elija la flecha abajo situada junto a la propiedad **TypeName**, elija la pestaña **Proyecto actual** en el cuadro de diálogo que aparece y, a continuación, elija la clase del proyecto.  
  
         El nombre completo incluye el espacio de nombres y el nombre de la clase seguidos del nombre del sistema LOB.  
  
         En el ejemplo siguiente se establece el valor de la propiedad **TypeName** en una colección de clases del proyecto.  
  
         `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.` `BdcModel1.Contact, BdcModel1]`  
  
    -   Si se trata de un tipo ubicado en un ensamblado de la solución, el nombre completo contiene el nombre del tipo, el nombre del ensamblado, el número de versión, la referencia cultural y el token de clave pública.  
  
         En el ejemplo siguiente se establece el valor de la propiedad **TypeName** en una colección de tipos de un ensamblado al que se hace referencia en la solución.  
  
         `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089]`  
  
    -   Si se trata de un tipo definido en el modelo de objetos de BDC, el nombre completo solamente incluye el espacio de nombres y el nombre del tipo.  
  
         En el siguiente ejemplo se establece el valor de la propiedad **TypeName** en una colección de tipos definida en el modelo de objetos de BDC.  
  
         `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]`  
  
6.  En la ventana **Detalles del método de BDC**, abra la lista que aparece en el descriptor de tipo y, a continuación, elija **Editar**.  
  
     Se abre la ventana **Explorador de BDC**.  
  
7.  En el **Explorador de BDC**, abra el menú contextual del descriptor de tipo y, a continuación, elija **Agregar descriptor de tipo**.  
  
     Un nuevo descriptor de tipo se agrega como elemento secundario al descriptor de tipo de la colección.  Configure este descriptor de tipo como una entidad.  
  
## Vea también  
 [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: Agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Cómo: Agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: Definir la instancia de un método](../sharepoint/how-to-define-a-method-instance.md)   
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  