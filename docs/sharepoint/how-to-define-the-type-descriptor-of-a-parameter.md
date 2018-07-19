---
title: 'Cómo: definir el Descriptor de tipo de un parámetro | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d1709ea21fa785a573dae03ad8c89814c9952b50
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119451"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Cómo: definir el descriptor de tipo de un parámetro
  Un descriptor de tipo contiene propiedades que describen el tipo de datos de un parámetro. Un descriptor de tipo puede definir un campo, una entidad o una colección de entidades. Para obtener más información, consulte [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### <a name="to-define-the-type-descriptor-of-a-parameter"></a>Para definir el descriptor de tipo de un parámetro  
  
1.  En el **detalles del método de BDC** ventana, elija el descriptor de tipo del parámetro.  
  
2.  En la barra de menús, elija **vista**, **ventana propiedades**.  
  
3.  En el **propiedades** ventana, establezca las propiedades de descriptor de tipos.  
  
     En los procedimientos siguientes se describe cómo se define un descriptor de tipo como un campo, entidad o colección de entidades.  
  
### <a name="to-define-a-field"></a>Para definir un campo  
  
1.  En el **propiedades** ventana, establezca el **nombre** propiedad de descriptor de tipos para el nombre de un campo en el tipo que representa la entidad (por ejemplo: **FirstName**).  
  
2.  En la lista junto a la **TypeName** propiedad, elija el tipo de datos adecuado (por ejemplo, **Int32**).  
  
     Para obtener información sobre otros parámetros opcionales, vea [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### <a name="to-define-an-entity"></a>Para definir una entidad  
  
1.  En el **propiedades** ventana, establezca el **nombre** propiedad a un nombre que describa la entidad (por ejemplo: **póngase en contacto con**).  
  
2.  Establecer el **TypeName** propiedad en el nombre completo del tipo que representa la entidad. Este tipo puede ser una clase del proyecto, un tipo definido en un ensamblado al que se hace referencia en la solución o un tipo definido en el modelo de objetos de BDC.  
  
    -   Para una clase en el proyecto, elija la flecha abajo junto a la **TypeName** propiedad, elija el **proyecto actual** ficha en el cuadro de diálogo que aparece y, a continuación, elija la clase en el proyecto.  
  
         El nombre completo incluye el espacio de nombres y el nombre de la clase seguidos del nombre del sistema LOB. En el ejemplo siguiente se establece el valor de la **TypeName** propiedad a una clase en el proyecto.  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   Si se trata de un tipo ubicado en un ensamblado de la solución, el nombre completo contiene el nombre del tipo, el nombre del ensamblado, el número de versión, la referencia cultural y el token de clave pública.  
  
         En el ejemplo siguiente se establece el valor de la **TypeName** propiedad a un tipo definido en un ensamblado que se hace referencia en la solución.  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   Si se trata de un tipo definido en el modelo de objetos de BDC, el nombre completo incluye el espacio de nombres y el nombre del tipo.  
  
         En el ejemplo siguiente se establece el valor de la **TypeName** propiedad a un tipo en el modelo de objetos BDC.  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  En el **detalles del método de BDC** , abra la lista que aparece en el descriptor de tipo y, a continuación, elija **editar**.  
  
     El **Explorador de BDC** abre la ventana.  
  
4.  En el **Explorador de BDC**, abra el menú contextual del descriptor de tipo y, a continuación, elija **agregar Descriptor de tipo**.  
  
     Un nuevo descriptor de tipo se agrega como elemento secundario al descriptor de tipo de entidad. Configure este descriptor de tipo como un campo.  
  
5.  Repita el paso 4 para agregar un descriptor de tipo secundario en cada campo de la entidad.  
  
### <a name="to-define-a-collection-of-entities"></a>Para definir una colección de entidades  
  
1.  En el **detalles del método de BDC** ventana, elija el descriptor de tipo del parámetro que desee.  
  
2.  En la barra de menús, elija **vista**, **ventana propiedades**.  
  
3.  En el **propiedades** ventana, establezca el **nombre** propiedad a un nombre que describa la entidad (por ejemplo: **contactos**).  
  
4.  Establecer el **IsCollection** propiedad **True**. Esto indica que este descriptor de tipo es una colección de entidades.  
  
5.  Establecer el **TypeName** propiedad en una cadena que contiene una referencia a la <xref:System.Collections.Generic.IEnumerable%601> interfaz y el nombre completo del tipo que representa la entidad. Este tipo puede ser una clase del proyecto, un tipo definido en un ensamblado al que se hace referencia en la solución o un tipo definido en el modelo de objetos de BDC.  
  
    -   Para una clase en el proyecto, elija la flecha abajo junto a la **TypeName** propiedad, elija el **proyecto actual** ficha en el cuadro de diálogo que aparece y, a continuación, elija la clase en el proyecto.  
  
         El nombre completo incluye el espacio de nombres y el nombre de la clase seguidos del nombre del sistema LOB.  
  
         En el ejemplo siguiente se establece el valor de la **TypeName** propiedad a una colección de las clases del proyecto.  
  
         `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.` ` BdcModel1.Contact, BdcModel1]'  
  
    -   Si se trata de un tipo ubicado en un ensamblado de la solución, el nombre completo contiene el nombre del tipo, el nombre del ensamblado, el número de versión, la referencia cultural y el token de clave pública.  
  
         En el ejemplo siguiente se establece el valor de la **TypeName** propiedad a una colección de tipos en un ensamblado que se hace referencia en la solución.  
  
         `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, versión = 4.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089]'  
  
    -   Si se trata de un tipo definido en el modelo de objetos de BDC, el nombre completo solamente incluye el espacio de nombres y el nombre del tipo.  
  
         En el ejemplo siguiente se establece el valor de la **TypeName** propiedad a una colección de tipos definidos en el modelo de objetos BDC.  
  
         `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]'  
  
6.  En el **detalles del método de BDC** , abra la lista que aparece en el descriptor de tipo y, a continuación, elija **editar**.  
  
     El **Explorador de BDC** abre la ventana.  
  
7.  En el **Explorador de BDC**, abra el menú contextual del descriptor de tipo y, a continuación, elija **agregar Descriptor de tipo**.  
  
     Un nuevo descriptor de tipo se agrega como elemento secundario al descriptor de tipo de la colección. Configure este descriptor de tipo como una entidad.  
  
## <a name="see-also"></a>Vea también
 [Introducción a las herramientas de diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)   
 [Diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
