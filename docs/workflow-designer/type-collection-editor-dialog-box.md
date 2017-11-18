---
title: "Cuadro de diálogo Editor de la colección de tipo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: bdc27b59640d92507956030fc34c767e321a81fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="type-collection-editor-dialog-box"></a>Editor de colección de tipos (cuadro de diálogo)
El **Editor de la colección de tipo** cuadro de diálogo se usa para agregar tipos conocidos a la **enviar** y **recepción** actividades. Este cuadro de diálogo también se utiliza para agregar argumentos de tipo genérico a la **InvokeMethod** actividad. Cuando se utiliza para la **enviar** y **recepción** actividades para agregar tipos conocidos, la **Editor de la colección de tipo** cuadro de diálogo requiere las adiciones de tipo sean únicos. Si se agrega un tipo duplicado y se confirma el cambio haciendo clic en **Aceptar**, se devuelve un mensaje de error. Cuando se utiliza para la **InvokeMethod** actividad para agregar argumentos de tipo genérico, la **Editor de la colección de tipo** cuadro de diálogo permite que se agreguen tipos duplicados.  
  
> [!NOTE]
>  [! INCLUIR[crabout](/dotnet/framework/wcf/feature-details/data-contract-known-types).  
  
 La tabla siguiente describen los elementos de interfaz de usuario de la **tipo de colección** cuadro de diálogo.  
  
|Elemento de la interfaz de usuario|Descripción|  
|----------------|-----------------|  
|**Lista de tipos**|Una lista de los tipos que se han agregado o se han quitado.|  
  
## <a name="to-bring-up-the-type-collection-editor"></a>Para mostrar el Editor de colección de tipos  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Para mostrar el Editor de colección de tipos para las actividades Send y Receive  
  
1.  Seleccione el **enviar** o **recepción** actividad en la vista Diseño.  
  
2.  Presione **F4** para que aparezca el **propiedades** ventana.  
  
3.  En el **propiedades** (ventana), haga clic en el botón de puntos suspensivos situado junto a la **KnownTypes** propiedad.  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Para mostrar el Editor de colección de tipos para la actividad InvokeMethod  
  
1.  Seleccione el **InvokeMethod** actividad en la vista Diseño.  
  
2.  Presione **F4** para que aparezca el **propiedades** ventana.  
  
3.  En el **propiedades** (ventana), haga clic en el botón de puntos suspensivos situado junto a la **GenericTypeArguments** propiedad.