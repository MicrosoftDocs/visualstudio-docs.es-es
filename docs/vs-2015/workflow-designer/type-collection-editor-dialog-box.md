---
title: Cuadro de diálogo Editor de la colección de tipo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: c33049c264041495041798ab98c4223ebe0ed6f7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298576"
---
# <a name="type-collection-editor-dialog-box"></a>Editor de colección de tipos (cuadro de diálogo)
El **Editor de la colección de tipo** cuadro de diálogo se usa para agregar tipos conocidos para la **enviar** y **recepción** actividades. Este cuadro de diálogo también se usa para agregar argumentos de tipo genérico para el **InvokeMethod** actividad. Cuando se usa para la **enviar** y **recepción** actividades para agregar tipos conocidos, el **Editor de la colección de tipo** cuadro de diálogo requiere que se agreguen tipos únicos. Si se agrega un tipo duplicado y se confirma el cambio haciendo **Aceptar**, se devuelve un mensaje de error. Cuando se usa para la **InvokeMethod** actividad para agregar argumentos de tipo genérico, la **Editor de la colección de tipo** cuadro de diálogo permite la adición de tipos duplicados.  
  
> [!NOTE]
>  [!INCLUDE[crabout](../includes/crabout-md.md)] sobre los tipos conocidos, vea [Data Contract Known Types](http://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337).  
  
 La tabla siguiente describen los elementos de interfaz de usuario de la **tipo colección** cuadro de diálogo.  
  
|Elemento de la interfaz de usuario|Descripción|  
|----------------|-----------------|  
|**Lista de tipos**|Una lista de los tipos que se han agregado o se han quitado.|  
  
## <a name="to-bring-up-the-type-collection-editor"></a>Para mostrar el Editor de colección de tipos  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Para mostrar el Editor de colección de tipos para las actividades Send y Receive  
  
1.  Seleccione el **enviar** o **recepción** actividad en la vista Diseño.  
  
2.  Presione **F4** para que aparezca el **propiedades** ventana.  
  
3.  En el **propiedades** ventana, haga clic en el botón de puntos suspensivos situado junto a la **KnownTypes** propiedad.  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Para mostrar el Editor de colección de tipos para la actividad InvokeMethod  
  
1.  Seleccione el **InvokeMethod** actividad en la vista Diseño.  
  
2.  Presione **F4** para que aparezca el **propiedades** ventana.  
  
3.  En el **propiedades** ventana, haga clic en el botón de puntos suspensivos situado junto a la **GenericTypeArguments** propiedad.