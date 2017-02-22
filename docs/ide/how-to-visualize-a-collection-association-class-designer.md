---
title: "How to: Visualize a Collection Association (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.collectionassociationline"
  - "vs.classdesigner.ShowAssociationException"
helpviewer_keywords: 
  - "collection associations"
  - "collections, collection associations"
  - "Class Designer [Visual Studio], collection associations"
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Visualize a Collection Association (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las propiedades y los campos que son colección de otros tipos pueden mostrarse en el diagrama de clases como una asociación de colecciones.  A diferencia de una asociación normal, que muestra un campo o una propiedad como una línea que vincula la clase propietaria al tipo del campo, una asociación de colecciones se muestra como una línea que vincula la clase propietaria al tipo perteneciente a la colección.  
  
### Para crear una asociación de colecciones  
  
1.  En el código, cree una propiedad o un campo cuyo tipo sea él mismo una colección fuertemente tipada.  
  
2.  En el diagrama de clases, expanda la clase para que se muestren las propiedades y los campos.  
  
3.  En la clase, haga clic con el botón secundario del mouse en el campo o la propiedad y elija **Mostrar como asociación de colecciones**.  
  
     La propiedad o el campo se muestran como una línea de asociación que se vincula al tipo recopilado.  
  
## Vea también  
 [How to: Create Associations Between Types \(Class Designer\)](../ide/how-to-create-associations-between-types-class-designer.md)   
 [Designing Classes and Types \(Class Designer\)](../ide/designing-classes-and-types-class-designer.md)   
 [Viewing Types and Relationships \(Class Designer\)](../ide/viewing-types-and-relationships-class-designer.md)